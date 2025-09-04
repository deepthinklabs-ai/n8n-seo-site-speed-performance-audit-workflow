# Setup Guide for SEO Site Speed/Performance Review Workflow

This guide walks you through setting up the n8n workflow step by step.

## 📋 Prerequisites

Before starting, ensure you have:

- [ ] n8n instance (cloud account or self-hosted)
- [ ] Google Cloud Platform account
- [ ] Anthropic Claude API account
- [ ] Email service (Gmail, Outlook, or SMTP server)

## 🔑 API Keys Setup

### 1. Google PageSpeed Insights API

#### Create Google Cloud Project
1. Go to [Google Cloud Console](https://console.cloud.google.com/)
2. Click "New Project" or select existing project
3. Name your project (e.g., "SEO Performance Analysis")

#### Enable PageSpeed Insights API
1. In the Cloud Console, go to "APIs & Services" → "Library"
2. Search for "PageSpeed Insights API"
3. Click on it and press "Enable"

#### Create API Key
1. Go to "APIs & Services" → "Credentials"
2. Click "Create Credentials" → "API Key"
3. Copy the generated API key
4. (Recommended) Click "Restrict Key" and limit to PageSpeed Insights API

### 2. Anthropic Claude API

1. Visit [Anthropic Console](https://console.anthropic.com/)
2. Sign up for an account
3. Go to "API Keys" section
4. Click "Create Key"
5. Copy the generated API key (starts with `sk-ant-`)

### 3. Email SMTP Setup

#### For Gmail:
1. Enable 2-factor authentication on your Google account
2. Generate an "App Password":
   - Go to Google Account settings
   - Security → 2-Step Verification → App passwords
   - Generate password for "Mail"
   - Use this password (not your regular password)

#### SMTP Settings:
- **Gmail**: smtp.gmail.com, port 587, TLS
- **Outlook**: smtp-mail.outlook.com, port 587, TLS
- **Other**: Check your email provider's SMTP settings

## 🔧 n8n Configuration

### 1. Import Workflow

1. Download `workflow.json` from this repository
2. In n8n interface:
   - Go to "Workflows"
   - Click "Import from file"
   - Select the downloaded `workflow.json`
   - Click "Import"

### 2. Configure Credentials

#### Google API Credential
1. In the workflow, click on any node that uses "Query Auth account"
2. Click on the credential dropdown
3. Select "Create New Credential"
4. Choose "Query Auth"
5. Set:
   - **Name**: "Google PageSpeed API"
   - **Key**: `key`
   - **Value**: Your Google API key
6. Save the credential

#### Anthropic API Credential
1. Click on the "Anthropic Chat Model" node
2. Click on credential dropdown → "Create New Credential"
3. Choose "Anthropic API"
4. Set:
   - **Name**: "Claude API"
   - **API Key**: Your Anthropic API key
6. Save the credential

#### SMTP Email Credential
1. Click on the "Send email" node
2. Click on credential dropdown → "Create New Credential"
3. Choose "SMTP"
4. Configure based on your email provider:
   - **Host**: Your SMTP server
   - **Port**: SMTP port (usually 587)
   - **Security**: STARTTLS
   - **Username**: Your email address
   - **Password**: Your email password/app password
5. Save the credential

### 3. Customize Workflow Settings

#### Update Target Website
1. Click on the "Init Site" node
2. Change the `site` value to your target website
3. Example: `https://yourwebsite.com`

#### Update Email Settings
1. Click on the "Send email" node
2. Update:
   - **From Email**: Your sending email address
   - **To Email**: Recipient email address
   - **Subject**: Customize if desired

## ✅ Testing

### 1. Test API Connections

#### Test Google API
1. Click on "PSI Mobile" node
2. Click "Test step" to verify API connection
3. Should return PageSpeed data

#### Test Claude API
1. Click on "Anthropic Chat Model" node
2. Click "Test step"
3. Should connect successfully

#### Test Email
1. Click on "Send email" node
2. Click "Test step"
3. Check if test email is received

### 2. Full Workflow Test

1. Click "Execute Workflow" button
2. Monitor execution progress
3. Check for any errors in red nodes
4. Verify email report is received

## 🔍 Troubleshooting

### Common Issues

#### "API key not valid" Error
- Verify API key is correct
- Ensure PageSpeed Insights API is enabled
- Check API key restrictions

#### "Authentication failed" for Email
- Verify SMTP settings
- For Gmail, ensure using App Password, not regular password
- Check if 2FA is enabled

#### "Rate limit exceeded"
- PageSpeed API has rate limits
- Add delays between requests
- Consider reducing batch size

#### Claude API Errors
- Verify API key format (starts with `sk-ant-`)
- Check account credits/billing
- Ensure API access is active

### Debug Steps

1. **Check Node Outputs**: Click on nodes to see data flow
2. **Enable Error Workflows**: Set up error handling
3. **Test Individual Nodes**: Use "Test step" on problematic nodes
4. **Check Logs**: Review n8n execution logs

## 🎛️ Advanced Configuration

### Customize Analysis Scope

- **Page Limits**: Modify limits in "Parse Sitemap" and related nodes
- **URL Filtering**: Add custom filters in JavaScript nodes
- **Analysis Depth**: Adjust which metrics to focus on

### Performance Tuning

- **Batch Processing**: Adjust "Loop Over Items" batch size
- **Rate Limiting**: Add delays to respect API limits
- **Error Handling**: Configure "Continue on Error" for resilience

### Report Customization

- **Email Template**: Modify HTML formatting in email nodes
- **Analysis Prompt**: Customize Claude AI system message
- **Scoring Logic**: Adjust performance scoring thresholds

## 📞 Support

If you encounter issues:

1. Check this guide and README.md
2. Review n8n documentation
3. Create an issue in this repository
4. Include error messages and node configurations

---

**Next Steps**: Once setup is complete, see README.md for usage instructions and customization options.