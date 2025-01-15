# Email Summarizer

AI-powered email summarizer that automatically processes your selected emails and delivers concise summaries directly to your inbox. Perfect for staying on top of newsletters, updates, and important communications without getting overwhelmed.

## Features

- Automatically processes emails from specified senders
- Generates concise, actionable summaries using OpenAI's GPT models
- Sends summary digests to your preferred email address
- Customizable sender list and processing frequency
- Secure authentication using Google OAuth 2.0

## Prerequisites

- Python 3.8 or higher
- Gmail account
- OpenAI API account (paid)
- Google Cloud Platform account (free tier works)

## Installation and Setup

### 1. Clone and Set Up Repository

```bash
# Clone the repository
git clone https://github.com/voralabs/email_summarizer.git
cd email_summarizer

# Create and activate virtual environment
python -m venv .venv
source .venv/bin/activate  # On Windows: .venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

### 2. Configure Google Cloud Platform

1. **Create a New Project**
   - Navigate to [Google Cloud Console](https://console.cloud.google.com)
   - Click the top bar dropdown → "New Project"
   - Name it "Email Summarizer" (or your preferred name)
   - Click "Create"

2. **Enable Gmail API**
   - Use the search bar at the top to find "Gmail API"
   - Click "Enable API"

3. **Set Up OAuth Credentials**
   - Go to "APIs & Services" → "Credentials"
   - Click "Create Credentials" → "OAuth client ID"
   - Configure the consent screen:
     - User Type: External
     - App name: "Email Summarizer"
     - User support email: Your email
     - Developer contact: Your email
   - Add your Gmail address as a test user
   - Create OAuth Client ID:
     - Application type: Desktop app
     - Name: "Newsletter Client"
   - Download the credentials JSON file
   - Rename it to `credentials.json` and move it to the project root folder

### 3. Set Up OpenAI API

1. Visit the [OpenAI Platform](https://platform.openai.com)
2. Create an account or log in
3. Navigate to "API Keys" → "Create new secret key"
4. Copy your API key for the next step

### 4. Configure Environment Variables

Create a `.env` file in the project root with the following:

```plaintext
OPENAI_API_KEY=your-openai-key
SUMMARY_EMAIL=your-email@example.com
```

### 5. Configure Email Senders

Update the `NEWSLETTER_SENDERS` list in `newsletter_processor.py`:

```python
NEWSLETTER_SENDERS = [
    'newsletter1@example.com',
    'newsletter2@example.com'
    # Add more email addresses as needed
]
```

### 6. Run the Application

```bash
python newsletter_processor.py
```

On first run, your browser will open for Gmail authorization. Follow the prompts to grant access.

## Troubleshooting

### Common Issues and Solutions

1. **"Access Blocked" Error**
   - Verify OAuth consent screen configuration
   - Ensure you're logged into the correct Google account
   - Check if your email is added as a test user

2. **"API Key Invalid" Error**
   - Verify `OPENAI_API_KEY` in `.env` file
   - Check key status in OpenAI platform
   - Generate a new key if needed

3. **No Emails Being Processed**
   - Double-check newsletter sender addresses
   - Verify emails are unread
   - Check Gmail spam/filter settings

4. **Authentication Issues**
   - Delete `token.json` (if exists) and reauthorize
   - Ensure `credentials.json` is in the correct location
   - Verify Google Cloud project is properly configured

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.


## Support

For issues and feature requests, please [open an issue](https://github.com/voralabs/email_summarizer/issues) on GitHub.
