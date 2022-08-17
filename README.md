# senior-data-engineer-coding-interview

In Git, please create a `feature/` branch, off of the `development` branch, using your name and surname as the branch name.

Submit a pull request into the `development` branch once you're done coding.

# Problem Statement

You are consulting on a Banking group's Data Engineering project and need to write an extract from their Aurora cluster into a CSV file on S3.

There are three different banks in the group.

An Amazon Aurora cluster (postgres flavour) houses their Operational Data Store.

Connection details are:
mycluster.cluster-123456789012.us-east-1.rds.amazonaws.com
(us the default postgres port to connect)
username: postgres
password: 5Y67bg#r#

Given the following data model:

![](DataModel_ERD.png)

# Perform the following tasks

1. Write code to deploy the following resources via Terraform:

(Put this code in the file `Terraform/main.tf`)

* A Glue Crawler to crawl this datasource
* A Glue Catalog Database to persist the metadata
* A Glue Job which will read data from this datasource and write it to S3
* An S3 bucket to house the transformed dataset
* Any other terraform resources you might require

2. Write a Glue ETL script (use the file `main.tf`), which calculates the moving average of loan amounts taken out over the last three months, per branch. Create a separate file for each bank in the group. Files need to be partitioned by Bank Name, Year and Month and the filename needs to be of the format BankName_YYYYMMDD.csv
   
3. Bonus points if you can:
   1. Build in a form of scheduling/ an orchestration layer
   2. Ensure idempotency of the ETL system
   3. Keep passwords and connection details secure
   4. Add comments and logging to your code
   5. Documentation is always nice ;)
   6. Anything else we did not specify in the task outline, but which you think will add value to your solution (keep in mind templatisability for reuse of your code by other team members)