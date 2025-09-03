# Automated Story Generation System

This project is a **serverless application** that generates **personalized children's stories** using **Amazon Bedrock** and **AWS Lambda**.  
It demonstrates how **Amazon Q Developer** can help even novice programmers create, understand, and improve code inside the AWS Lambda editor.

---

## 📖 Overview

The application allows users to:
- Provide inputs like a **character name**, **theme**, and **setting**.
- Generate a safe, age-appropriate story using **Amazon Bedrock foundation models**.
- Store the generated story in **Amazon S3** and its metadata in **Amazon DynamoDB**.

Amazon Q Developer is used for:
- Explaining the Lambda code
- Writing comments
- Assisting with function creation and testing

---

## 🗂 Architecture

The system is designed with a **fully serverless architecture**.

**Key components:**
- **AWS Lambda (`story-teller`)** – Core logic for generating stories
- **Amazon Bedrock** – Foundation models for story generation
- **Amazon S3** – Storage for generated stories
- **Amazon DynamoDB** – Storage for metadata
- **Amazon Q Developer** – Code assistance in AWS Lambda editor

**Architecture Diagram:**

![Architecture](architecture.png)

---

## 🧪 Example Lambda Execution

Below is a sample output of the Lambda function when executed successfully:

![Lambda Output](lambda_output.png)

---

## 🧩 AWS Services Used
- **Amazon Q Developer** – For code explanations and recommendations  
- **Amazon Bedrock** – To generate story text  
- **AWS Lambda** – Serverless compute for the story logic  
- **Amazon S3** – Story storage  
- **Amazon DynamoDB** – Metadata storage  

---

## 🗃 How It Works
1. The **novice programmer** creates and tests the Lambda function in the AWS Console.  
2. The Lambda function sends user inputs (character name, theme, setting) to **Amazon Bedrock**.  
3. Bedrock generates a **personalized story**.  
4. The Lambda function:
   - Stores the story JSON in **Amazon S3**.
   - Saves metadata (like timestamp and inputs) in **Amazon DynamoDB**.  
5. The story can then be retrieved or displayed later.

---

## ⚙️ Deployment Steps

### 1. Upload Lambda Code
- The code is available in `story_teller_function.txt`.
- Copy the code into the AWS Lambda console **or** upload as a `.zip` file.

### 2. Set Permissions
Ensure your Lambda function’s role has:
- `bedrock:InvokeModel`
- `s3:PutObject`
- `dynamodb:PutItem`
- `codewhisperer:GenerateRecommendations` *(for Amazon Q Developer assistance in the Lambda editor)*

### 3. Configure S3 and DynamoDB
- Create an S3 bucket named `story-teller`.
- Create a DynamoDB table named `story-table` with a primary key `storyId`.

---

## 🔒 Security Considerations
- Encrypt S3 objects using SSE-S3 or SSE-KMS.
- Enable DynamoDB encryption (enabled by default).
- Avoid storing PII like children's full names.
- Use Amazon Bedrock Guardrails to filter inappropriate content.

---

## 🌱 Future Improvements
- Add illustrations using **Amazon Bedrock Image Models**.
- Implement text-to-speech using **Amazon Polly**.
- Build a simple web front-end using **API Gateway + React**.
- Add localization and multi-language support.


