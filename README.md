#Netflix Data Analysis using AWS Glue and Amazon Athena#

Project Overview

This project demonstrates how to perform serverless data analysis on a dataset stored in Amazon S3 using AWS Glue and Amazon Athena.

The dataset NetflixOriginals.csv is uploaded to an Amazon S3 bucket. AWS Glue Crawler scans the dataset and automatically detects the schema, creating a table in the AWS Glue Data Catalog. Using Amazon Athena, SQL queries are executed on the dataset to retrieve useful insights.

This architecture enables efficient data analysis without managing any servers or databases.


AWS Services Used

Amazon S3 – Stores the dataset.

AWS IAM – Provides necessary permissions for AWS Glue.

AWS Glue Crawler – Scans the dataset and detects the schema.

AWS Glue Data Catalog – Stores metadata about the dataset.

Amazon Athena – Used to query data using SQL.

Project Architecture:-
Amazon S3
   ↓
AWS Glue Crawler
   ↓
AWS Glue Data Catalog
   ↓
Amazon Athena
   ↓
SQL Query Results


Explanation:

Dataset is uploaded to Amazon S3.

AWS Glue Crawler scans the dataset.

Schema is stored in AWS Glue Data Catalog.

Amazon Athena queries the dataset using SQL.




Dataset Information

Dataset Name: NetflixOriginals.csv

The dataset contains information about Netflix original movies and shows, including details such as title, genre, runtime, release date, and other attributes.



Steps Performed in the Project
Step 1 – Create S3 Bucket

Created an Amazon S3 bucket named:
my-netflix-demo

Uploaded dataset:
NetflixOriginals.csv


Step 2 – Create IAM Role
Created IAM role:
netflixglue-demo

Attached policies:

AmazonS3FullAccess

AWSGlueServiceRole

This role allows AWS Glue to access S3 and create tables in the Data Catalog.


Step 3 – Create AWS Glue Crawler
Crawler name:
crawler-demo


Configuration:

Data source → S3 bucket

IAM role → netflixglue-demo

Target database → netflix-db

The crawler scans the dataset and automatically detects the schema.



Step 4 – Run the Crawler

After running the crawler, a table is created in AWS Glue Data Catalog:

my_netflix_demo

Database name:

netflix-db


Step 5 – Query Data using Amazon Athena

Example Query:
SHOW TABLES;

Example Query:
SELECT COUNT(*) AS total_records
FROM my_netflix_demo;

Output:
Total Records = 358


#################################Project Structure#############################
netflix-data-analysis-aws
│
├── dataset
│   └── NetflixOriginals.csv
│
├── queries
│   ├── show_tables.sql
│   └── count_records.sql
│
├── screenshots
│   ├── s3_upload.png
│   ├── iam_role.png
│   ├── glue_crawler.png
│   ├── athena_query.png
│   └── query_result.png
│
└── README.md






