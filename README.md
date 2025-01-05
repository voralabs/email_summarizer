# email_summarizer
AI-powered email summarizer that reads your specific emails and sends concise summaries.

**Setup Guide**


Prerequisites

Python 3.8+

Gmail account

OpenAI account

Google Cloud account

**Step 1: Clone Repository**

git clone https://github.com/voralabs/email_summarizer.git

cd NewsletterGPT

python -m venv .venv

source .venv/bin/activate  # Windows: .venv\Scripts\activate

pip install -r requirements.txt


**Step 2: Google Cloud Setup**

Go to Google Cloud Console


Create new project

Click top bar dropdown → "New Project"

Name: "Email Summarizer"

Click "Create"

Enable Gmail API


Search "Gmail API" in top search bar

Click "Enable API"


Create OAuth Credentials

Go to "APIs & Services" → "Credentials"

Click "Create Credentials" → "OAuth client ID"

Configure consent screen:

User Type: External

App name: "Email Summarizer"

User support email: Your email

Developer contact: Your email

Add test users:

Your Gmail address

Create OAuth Client ID:

Application type: Desktop app

Name: "Newsletter Client"

Download JSON

Rename to credentials.json

Move to project folder


**Step 3: OpenAI Setup**

Visit OpenAI Platform

Create account/login

Click "API Keys" → "Create new secret key"

Copy key


**Step 4: Environment Setup**

Create .env file:

OPENAI_API_KEY=your-openai-key

SUMMARY_EMAIL=your-email@example.com


**Step 5: Configure Newsletters**

Update NEWSLETTER_SENDERS in newsletter_processor.py:

NEWSLETTER_SENDERS = [
    'newsletter1@example.com',
    'newsletter2@example.com'
]


**Step 6: Run**

python newsletter_processor.py

First run opens browser for Gmail authorization.


**Troubleshooting**
Common Issues
"Access Blocked" error

Check OAuth consent screen setup
Verify you're logged into correct Google account
"API Key Invalid" error

Check OPENAI_API_KEY in .env
Verify key on OpenAI platform
No emails processed

Verify newsletter sender addresses
Check for unread emails
