# _10404_CC_miniproj

### 👩‍💻 Mini Project: Resume Scanner  
By **Ashal Dabre**, TE Comps-B (Roll No. 10404)  
Subject: **Cloud Computing**

---

## 🧠 Project Overview

This is a cloud-based **Resume Scanner** application that provides **tailored job recommendations** based on resume content. The system utilizes multiple **AWS services** to analyze uploaded resumes and stores the results for further processing.

---

## 🚀 Features

- Upload your resume through a frontend interface
- Get job recommendations based on your resume content
- Secure upload using **presigned URLs**
- End-to-end processing and logging using AWS serverless architecture

---

## ☁️ AWS Services Involved

- **Amazon API Gateway** – Handles HTTP requests from frontend
- **Amazon S3** – Stores uploaded resumes securely
- **AWS Lambda** – Handles logic for presigned URL generation and resume analysis
- **Amazon Textract** – Extracts text from resumes
- **Amazon SQS** – Passes analysis completion status
- **Amazon DynamoDB** – Stores metadata and processing status
- **AWS IAM** – Manages permissions and access control

---

## 🧩 Architecture & Workflow

### 🔹 Step 1: API Gateway
- Frontend requests a **presigned URL** from **API Gateway**.
- API Gateway invokes the **GeneratePresignedUrlLambda** function.

### 🔹 Step 2: Lambda Function – Presigned URL
- The Lambda returns a **secure presigned S3 URL** to the frontend.

### 🔹 Step 3: Upload to S3
- User uploads resume using the presigned URL.
- Uploading triggers the **FinishTextractJob Lambda** via an S3 event.

### 🔹 Step 4: Resume Analysis
- FinishTextractJob Lambda invokes **Textract** to analyze the resume.
- After processing, it:
  - Sends a message to **SQS** ("SUCCESS" or failure).
  - Logs file name, upload time, scan status into **DynamoDB**.

---

## 🌐 Frontend Feature

> Simple UI where user can **upload a resume** and get **personalized recommendations** powered by AWS services.

---



