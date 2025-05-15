# 📝 Blog Generation with AWS Bedrock

This project demonstrates how to dynamically generate blog content using **Meta LLaMA 2 (13B)** model via **AWS Bedrock**, and store the generated blog text in an **S3 bucket** using a serverless **AWS Lambda** function.

---

## 🚀 Features

- Generates a 200-word blog post based on user-defined topics.
- Utilizes the Meta LLaMA 3 70B Instruct model hosted on AWS Bedrock.
- Stores the generated content securely on Amazon S3.
- Deployed as a Lambda function, allowing for seamless integration with other AWS services like API Gateway or Step Functions.

---

## 🧱 Technologies Used

- **AWS Bedrock** – for accessing the Meta LLaMA 3 70B Instruct model.
- **AWS Lambda** – to host the generation logic in a serverless environment.
- **Amazon S3** – to store the blog outputs.
- **Python (Boto3)** – for interacting with AWS services.

---

## 📂 File Structure

```
.
├── app.py                 # Lambda function logic for blog generation and S3 upload
├── README.md              # Project overview and setup instructions
```

---

## 📥 Input

The function expects a POST request with a JSON body:
```json
{
  "blog_topic": "The Future of AI in Education"
}
```

---

## 📤 Output

- A generated blog (200 words) is stored in the S3 bucket: `aws_bedrock_course1`
- File path format: `blog-output/<timestamp>.txt`

---

## ⚙️ How It Works

1. The Lambda function extracts the blog topic from the event body.
2. It formats the topic into a prompt and sends a request to Bedrock using `boto3`.
3. The generated blog text is saved into a specified S3 bucket with a timestamped key.

---

## 🧪 Sample Response

```json
{
  "statusCode": 200,
  "body": "\"Blog Generation is completed\""
}
```

---

## 📸 Sample Prompt

```text
<s>[INST]Human: Write a 200 words blog on the topic The Future of AI in Education
Assistant:[/INST]
```

---

## 📝 To-Do

- Add API Gateway to trigger Lambda via HTTP request.
- Add blog title and keyword extraction.
- Store metadata in DynamoDB for indexing.

---

## 🛡️ Error Handling

- Try-except blocks handle Bedrock and S3 connection errors gracefully.
- Logs error details for easier debugging.

---
