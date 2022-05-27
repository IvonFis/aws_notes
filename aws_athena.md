# Athena

___

## What is it? 

Athena is a serverless query service that queries data from S3 data such as JSON, CSV, parquet using ANSI SQL. 
It works directly from data from S3. 

## Technology

Athena uses Presto (fill standard SQL support)

## Limitations

### Query related quotas

The account has query-related quotas. 

- Active DDL queries: (CREATE TABLE, ALTER TABLE, etc) **20**
- DDL query time out: (max a DDL query can run before it gets cancelled) **600**
- Active DML queries: (SELECT, INSERT INTO, etc) **100-200**
- DML query timeout: (max time DML query can run before it gets cancelled) **30**

Athena process quieries based on the 

- service load
- asynchronous processes pick up as the resources become available

> EX. if your DML query quota is 25 and your total of running and queued queries is 26, query 26 will result in a **TooManyRequestsException**

### String length

The maximum allowed query string length is 262144 bytes, where the strings are encoded in UTF-8

## Amazon Redshift vs Amazon Athena

A data warehouse like Amazon Redshift is your best choice when you need to pull together data from many different sourcess.



### References

[1] https://docs.aws.amazon.com/athena/latest/ug/service-limits.html
