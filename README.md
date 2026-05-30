# AI Resume Analyzer Bot using n8n

An AI-powered Resume Analyzer Automation built with **n8n**, **Telegram Bot API**, **Gmail API**, and **Groq LLM**.

This workflow automatically analyzes resumes against a target job role and generates an ATS-style evaluation report including match score, missing keywords, weaknesses, hiring readiness, and improvement suggestions.


# Features

* Resume upload through Telegram
* Resume analysis through Gmail attachments
* AI-powered ATS scoring
* PDF, DOCX, and TXT resume support
* Target role/job description matching
* Missing keyword detection
* Hiring readiness evaluation
* Automated Telegram replies
* Automated Gmail responses
* Groq LLM integration using Llama 3.3 70B

# Workflow Architecture

| Step                  | Description                                      |
| --------------------- | ------------------------------------------------ |
| Telegram Trigger      | Receives user messages and resume uploads        |
| Gmail Trigger         | Detects unread emails with resume attachments    |
| Resume Type Detection | Identifies PDF, DOCX, or TXT files               |
| File Extraction       | Extracts text from uploaded resumes              |
| AI Resume Analysis    | Sends extracted text to Groq LLM                 |
| ATS Evaluation        | Generates ATS score and recruiter-style feedback |
| Telegram Response     | Sends analysis back to Telegram user             |
| Gmail Response        | Sends analysis report via email                  |

# Supported Platforms

* Telegram Bot
* Gmail
* Groq AI API
* n8n Automation Platform


# Supported Resume Formats

* PDF
* DOCX
* TXT


# Tech Stack

| Technology       | Purpose                       |
| ---------------- | ----------------------------- |
| n8n              | Workflow automation           |
| Telegram Bot API | Resume upload and interaction |
| Gmail API        | Email-based resume analysis   |
| Groq API         | AI resume evaluation          |
| llama-3.3-70b-versatile    | Large language model          |
| JavaScript       | Custom workflow logic         |
| PostgreSQL       | Workflow database             |


# Project Structure

```bash
resume-analyzer-bot/
│
├── workflows/
│   └── Resume Analyzer - Gmail + Telegram.json
│
├── screenshots/
│
├── README.md
├── .gitignore
└── .env.example
```


# Setup Instructions

## 1. Clone Repository

```bash
git clone https://github.com/your-username/resume-analyzer-bot.git
cd resume-analyzer-bot
```


## 2. Import Workflow into n8n

1. Open n8n dashboard
2. Go to:

   ```text
   Workflows → Import from File
   ```
3. Select:

```text
Resume Analyzer - Gmail + Telegram.json
```


# Required Credentials

Before running the workflow, configure the following credentials inside n8n.

| Credential         | Purpose                         |
| ------------------ | ------------------------------- |
| Telegram Bot Token | Telegram bot integration        |
| Gmail OAuth2       | Gmail trigger and email sending |
| Groq API Key       | AI-powered resume analysis      |


# Telegram Setup

1. Create a Telegram bot using BotFather
2. Copy the Bot Token
3. Add Telegram credentials inside n8n
4. Activate workflow


# Gmail Setup

1. Create Google Cloud project
2. Enable Gmail API
3. Configure OAuth Consent Screen
4. Create OAuth2 credentials
5. Add credentials to n8n


# Groq API Setup

1. Create Groq account
2. Generate API key
3. Add Groq credentials in n8n


# Workflow Logic

## Telegram Flow

1. User sends job role
2. User uploads resume
3. Resume text extracted
4. AI analyzes resume
5. ATS report sent back to Telegram

## Gmail Flow

1. User emails resume attachment
2. Workflow detects unread email
3. Resume text extracted
4. AI analyzes resume
5. ATS report sent via Gmail reply


# Example Output

```text
✅ ATS Match Score: 82/100

🎯 Target Role:
Backend Developer Intern

✅ Matching Skills:
• Node.js
• MongoDB
• REST APIs

❌ Missing Keywords:
• Docker
• Kubernetes

⚠️ Resume Weaknesses:
• Limited quantified achievements
• Missing deployment experience

💡 Improvement Suggestions:
• Add deployment projects
• Include measurable impact
• Mention backend scalability concepts

🚀 Hiring Readiness:
Moderate Candidate
```


