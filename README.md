# AI Resume Analyzer Bot using n8n

An AI-powered Resume Analyzer Automation built with **n8n**, **Telegram Bot API**, **Gmail API**, and **Groq LLM**.

This workflow automatically analyzes resumes against a target job role and generates an ATS-style evaluation report including ATS score, missing keywords, weaknesses, hiring readiness, and improvement suggestions.

# Automation Workflow
<img width="1710" height="619" alt="Workflow Architecture" src="https://github.com/user-attachments/assets/ecba2744-63c1-4463-b2af-e5c677e5f051" />
Gmail Trigger
<img width="1816" height="833" alt="Gmail Trigger" src="https://github.com/user-attachments/assets/14bd865d-9dc0-406d-8044-47bc007be29e" />
Telegram Trigger

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
* Multi-platform workflow automation
* Recruiter-style AI evaluation

# Workflow Architecture

| Step                  | Description                                         |
| --------------------- | --------------------------------------------------- |
| Telegram Trigger      | Receives Telegram messages and resume uploads       |
| Gmail Trigger         | Detects unread emails containing resume attachments |
| Resume Type Detection | Identifies PDF, DOCX, or TXT files                  |
| File Extraction       | Extracts resume text from uploaded files            |
| AI Resume Analysis    | Sends extracted content to Groq LLM                 |
| ATS Evaluation        | Generates ATS score and recruiter-style feedback    |
| Telegram Response     | Sends AI-generated analysis to Telegram user        |
| Gmail Response        | Sends ATS analysis report via Gmail                 |

# Supported Platforms

* Telegram Bot API
* Gmail API
* Groq AI API
* n8n Workflow Automation

# Supported Resume Formats

* PDF
* DOCX
* TXT


# Tech Stack

| Technology              | Purpose                               |
| ----------------------- | ------------------------------------- |
| n8n                     | Workflow automation platform          |
| Telegram Bot API        | Resume upload and user interaction    |
| Gmail API               | Email-based resume processing         |
| Groq API                | AI-powered resume evaluation          |
| llama-3.3-70b-versatile | Large Language Model for ATS analysis |
| JavaScript              | Custom workflow routing and logic     |
| PostgreSQL              | Workflow data persistence and storage |
| Docker Desktop          | Local n8n container deployment        |


# Project Structure

```bash
resume-analyzer-bot/
│
├── workflows/
│   └── Resume Analyzer - Gmail + Telegram.json
│
├── screenshots/
└── README.md
```

# Local Setup using Docker Desktop

## 1. Install Docker Desktop

Download Docker Desktop:

* https://www.docker.com/products/docker-desktop/

After installation:

```bash
docker --version
```

## 2. Run n8n Locally

### Windows CMD

```bash
docker run -it --rm ^
-p 5678:5678 ^
-e N8N_SECURE_COOKIE=false ^
-e TZ=Asia/Kolkata ^
-v ~/.n8n:/home/node/.n8n ^
docker.n8n.io/n8nio/n8n
```

### Mac/Linux

```bash
docker run -it --rm \
-p 5678:5678 \
-e N8N_SECURE_COOKIE=false \
-e TZ=Asia/Kolkata \
-v ~/.n8n:/home/node/.n8n \
docker.n8n.io/n8nio/n8n
```

## 3. Open n8n

Open browser:

```text
http://localhost:5678
```

Create your n8n owner account.

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

## Create Telegram Bot

1. Open Telegram
2. Search:

```text
@BotFather
```

3. Run:

```text
/newbot
```

4. Create bot name and username
5. Copy generated Bot Token

## Connect Telegram in n8n

1. Open Credentials
2. Create new:

```text
Telegram API
```

3. Paste Bot Token
4. Save credential

# Gmail Setup

## Create Google Cloud Project

1. Open:

```text
https://console.cloud.google.com/
```

2. Create new project
3. Enable Gmail API

## Configure OAuth Consent Screen

1. Open:

```text
APIs & Services → OAuth Consent Screen
```

2. Select External
3. Add application information
4. Add test user email

## Create OAuth Credentials

1. Open:

```text
APIs & Services → Credentials
```

2. Create OAuth Client ID
3. Application Type:

```text
Web Application
```

4. Add Redirect URI:

```text
http://localhost:5678/rest/oauth2-credential/callback
```

## Connect Gmail in n8n

1. Create Gmail OAuth2 credential
2. Add:

   * Client ID
   * Client Secret
3. Authorize Gmail access

# Groq API Setup

## Generate API Key

1. Open:

```text
https://console.groq.com/
```

2. Create account
3. Generate API key

## Connect Groq in n8n

1. Create:

```text
Groq API Credential
```

2. Paste API key
3. Save credential

# Workflow Logic

## Telegram Flow

1. User sends target job role
2. User uploads resume
3. Resume text extracted
4. AI analyzes resume
5. ATS report generated
6. Report sent back to Telegram

## Gmail Flow

1. User sends email with resume attachment
2. Workflow detects unread email
3. Resume text extracted
4. AI analyzes resume
5. ATS report emailed back automatically

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
