# 🎶 AWS Lambda Music Charts Aggregator

## Overview
This project automates the aggregation of music chart data stored in `.csv` files using AWS Lambda, S3, and EventBridge. It processes daily chart data to generate a final top 20 monthly artists summary in CSV format, stored in a public S3 bucket.

- **Lambda ARN**: `aws:lambda:us-east-1:057760358300:function:processtopartists`
- **EventBridge ARN**: `aws:events:us-east-1:057760358300:event-bus/default`
- **Final CSV Output**: [monthly_top_20_artists_summary.csv](https://my-music-toplists.s3.us-east-1.amazonaws.com/final/monthly_top_20_artists_summary.csv)

## 🛠️ Steps I Followed
1. Verified that all `.csv` files were present in the `raw/` folder inside the S3 bucket.
2. Configured an **S3 Event Notification** to trigger the Lambda function whenever a `.csv` file is added or deleted in `raw/`.
3. Created an **EventBridge rule** with `cron(0 0 1 * ? *)` to run the function automatically on the 1st day of each month.
4. Tested the system by uploading and deleting files, as well as waiting for the scheduled trigger.
5. Verified successful execution in **CloudWatch Logs** and confirmed output in the final S3 path.

## ✅ Final Conclusion
This project demonstrates the transition from manual processing to **fully automated cloud-based data pipelines**. By integrating AWS Lambda, S3, and EventBridge, I created a serverless solution that triggers on both schedule and event-based rules. The workflow is **scalable, reliable**, and suitable for professional **data engineering environments**.
