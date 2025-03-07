# Sentiment-Analysis-with-AWS-Lambda-and-Comprehend-Public
Features
Automated Workflow – Triggered by S3 events when a file is uploaded.
Sentiment Analysis – Uses AWS Comprehend to classify sentiment as POSITIVE, NEGATIVE, NEUTRAL, or MIXED.
Scalable Sampling – Processes up to 25,000 reviews per file for efficient analysis.
S3 Output – Stores the processed CSV file in the output/ directory of the same bucket.
Error Handling – Provides logging and error handling for missing data or unexpected issues.
Setup & Usage
Prerequisites
AWS Lambda with permissions to:
S3 (read/write access)
AWS Comprehend (for sentiment analysis)
Python 3.9+
Required Python libraries:
boto3
pandas
Input & Output File Format
Input CSV: Must contain a column named review_description.

csv
Copy
Edit
review_id,review_description
1,"Great app, love it!"
2,"Terrible experience."
Output CSV: Includes an additional Sentiment column.

csv
Copy
Edit
review_id,review_description,Sentiment
1,"Great app, love it!",POSITIVE
2,"Terrible experience.",NEGATIVE
Deployment Steps
Set Up S3 Bucket:
Create an S3 bucket.
Add an event notification to trigger the Lambda function upon file upload.
Deploy the Lambda Function:
Copy the Python script into an AWS Lambda function.
Attach an IAM role with S3 and AWS Comprehend permissions.
Test the Workflow:
Upload a CSV file to the bucket.
Check the output/ directory for processed results.
Configuration & Notes
Adjust the sample size (n=25000) in the script if needed.
Ensure the LanguageCode in AWS Comprehend API calls matches the review language ('en' for English).
Reviews are processed sequentially; consider batching or multiprocessing for high-volume workloads.
Only CSV files with valid UTF-8 encoding are supported
