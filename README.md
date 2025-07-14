# Manara_Project
# Serverless Image Processing with S3 and Lambda
# Smart Serverless Image Uploader with AWS

## Project Description

This project implements a fully serverless image upload and metadata management application using AWS. Users can upload images via an HTTP API, which triggers a Lambda function that stores the image in an S3 bucket and records metadata (like file name, type, and upload time) in DynamoDB. This showcases a real-world event-driven architecture using AWS services.

---

##  AWS Services Used

| Service              | Purpose                                                                 |
|----------------------|-------------------------------------------------------------------------|
| **Amazon S3**         | Stores original uploaded images                                          |
| **AWS Lambda**        | Handles image processing and metadata storage                           |
| **Amazon DynamoDB**   | Stores metadata of uploaded images (e.g., name, type, timestamp, S3 key)|
| **Amazon API Gateway**| Provides REST API endpoint for image upload                             |
| **Amazon CloudWatch** | Logs Lambda execution and tracks performance                            |
| **IAM Roles**         | Manages secure access to AWS resources                                  |

---

##  Architecture Overview

1. The user uploads an image through an HTTP request (via frontend or Postman).
2. The request is sent to Amazon API Gateway.
3. API Gateway triggers a Lambda function.
4. Lambda:
   - Stores the image in an S3 bucket.
   - Saves metadata in DynamoDB.
   - Logs execution via CloudWatch.
![System Architecture](diagram.png)


---

## API Endpoint

| Method | Endpoint    | Description               |
|--------|-------------|---------------------------|
| POST   | `/upload`   | Upload image via base64   |

---

## Sample JSON Payload (for POST request)

```json
{
  "filename": "photo.jpg",
  "content_type": "image/jpeg",
  "image_base64": "BASE64_ENCODED_IMAGE_HERE"
}
