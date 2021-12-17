+++
title = "Running the ksqlDB application created"
weight = 11
chapter = true
pre = "<b>11. </b>"
+++

## Running the ksqlDB application created 

Once the Mysql connector is provisioned and running, navigate back to the ksqlDB and click on the application we created in the previous step.

![Subscribe](/images/runKsql/1.png)

Copy and paste below SQL command to the editor and “Run Query”

*The ksqlDB that we have below will set up streams and tables using the topics we sourced from the MySQL database and the topic the new credit applications will feed into.   To understand the difference between a stream, imagine for a moment a chess match currently in play.  A stream would be all of the moves on the chess table leading up to the current state of the match.  A table would show you just the current state.*

```
SET 'auto.offset.reset'='earliest';

CREATE STREAM credit_payment_history (customer_id VARCHAR,
                     credit_type VARCHAR,
                     paid_on_time INT)
                         WITH (KAFKA_TOPIC='mysql_credit_payment_history',
              VALUE_FORMAT='JSON',
              KEY_FORMAT='JSON');

CREATE TABLE credit_payment_history_tbl AS
    SELECT customer_id,
          ROUND(CAST(SUM(paid_on_time) AS DOUBLE) / CAST(COUNT(*) AS DOUBLE) * 100, 2) as PCT_PAID_ON_TIME
    FROM credit_payment_history
    GROUP BY customer_id;

CREATE STREAM credit_utilization (customer_id STRING,
                     total_balance BIGINT,
                     total_limit BIGINT)
    WITH (kafka_topic='mysql_credit_utilization',
          value_format='JSON');

CREATE STREAM CREDIT_UTILIZATION_REKEYED
  WITH (KAFKA_TOPIC='credit_utilization_rekeyed') AS
  SELECT *
  FROM CREDIT_UTILIZATION
  PARTITION BY CUSTOMER_ID;

CREATE TABLE credit_utilization_tbl (
    customer_id STRING PRIMARY KEY,
    total_balance BIGINT,
    total_limit BIGINT
  ) WITH (
    KAFKA_TOPIC = 'credit_utilization_rekeyed',
    VALUE_FORMAT = 'JSON',
    KEY_FORMAT = 'JSON'
  );

CREATE STREAM credit_applications (
    customer_id VARCHAR KEY,
    credit_type VARCHAR,
    amount BIGINT
  ) WITH (
    KAFKA_TOPIC = 'credit_applications',
    VALUE_FORMAT = 'JSON',
    KEY_FORMAT = 'JSON'
  );
```
![Subscribe](/images/runKsql/2.png)

Once the query is executed and completed, lets remove the query from the editor and paste below query and Run it again.

*The ksqlDB code below will set up two new streams that will either approve or reject applications using the WHERE clause.  For approval the applicant will need to have PCT_PAID_ON_TIME over 90% and their credit utilization needs to be under 30%.  The code will reject the application if either PCT_PAID_ON_TIME is less than or equal to 90% or their utilization is equal to or greater than 30%.  Also note the "emit changes" which will send the approvals and rejects to their own Kafka topics.*

```
SET 'auto.offset.reset'='earliest';

CREATE STREAM approved_applications
WITH (VALUE_FORMAT='AVRO') AS
SELECT  a.customer_id,
        a.credit_type,
        a.amount,
        cp.PCT_PAID_ON_TIME,
        ROUND(CAST(cu.total_balance AS DOUBLE) / CAST(cu.total_limit AS DOUBLE) * 100, 2) as PCT_CREDIT_UTILIZATION
FROM credit_applications a
INNER JOIN credit_payment_history_tbl cp ON (a.customer_id = cp.customer_id)
INNER JOIN credit_utilization_tbl cu ON (a.customer_id = cu.customer_id)
WHERE PCT_PAID_ON_TIME > 90 AND ROUND(CAST(cu.total_balance AS DOUBLE) / CAST(cu.total_limit AS DOUBLE) * 100, 2) < 30
emit changes;

CREATE STREAM rejected_applications
WITH (VALUE_FORMAT='AVRO') AS
SELECT  a.customer_id,
        a.credit_type,
        a.amount,
        cp.PCT_PAID_ON_TIME,
        ROUND(CAST(cu.total_balance AS DOUBLE) / CAST(cu.total_limit AS DOUBLE) * 100, 2) as PCT_CREDIT_UTILIZATION
FROM credit_applications a
INNER JOIN credit_payment_history_tbl cp ON (a.customer_id = cp.customer_id)
INNER JOIN credit_utilization_tbl cu ON (a.customer_id = cu.customer_id)
WHERE PCT_PAID_ON_TIME <= 90 AND ROUND(CAST(cu.total_balance AS DOUBLE) / CAST(cu.total_limit AS DOUBLE) * 100, 2) >= 30
emit changes;
```
![Subscribe](/images/runKsql/3.png)

Navigate back to the Topics section, you will notice that a few new topics were created when those SQL statements were executed. 

Notice there are two Topics which ends with **APPROVED_APPLICATIONS** and **REJECTED_APPLICATIONS**, which are the topics containing applications that were approved and rejected respectively.

Now, lets move to next section.