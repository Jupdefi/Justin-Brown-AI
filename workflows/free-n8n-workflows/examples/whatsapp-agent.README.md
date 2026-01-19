# WhatsApp AI Chatbot

A comprehensive AI-powered WhatsApp chatbot that handles text, voice, images, and PDF documents. Features conversation memory and multi-modal responses.

## What This Workflow Does

This workflow creates a full-featured WhatsApp AI assistant:

1. Receives messages from WhatsApp (text, voice, images, PDFs)
2. Processes each type appropriately
3. Uses GPT-4 for intelligent responses
4. Maintains conversation context with memory
5. Can respond with audio for voice messages

## Use Cases

- Customer support automation
- Personal AI assistant via WhatsApp
- Document analysis on the go
- Voice message transcription and response
- Image description and analysis

## Workflow Overview

```
[WhatsApp Trigger] → [Detect Input Type] → [Process Content] → [AI Agent] → [Respond]
```

### Input Types Handled

| Type | Processing |
|------|------------|
| **Text** | Direct to AI agent |
| **Voice** | Transcribe → AI → Optional audio response |
| **Image** | Analyze with GPT-4V → AI response |
| **PDF** | Extract text → AI analysis |

## Setup Instructions

### Step 1: Create Meta Business Account
1. Go to [business.facebook.com](https://business.facebook.com)
2. Create a Business Account
3. Complete business verification

### Step 2: Set Up WhatsApp Business API
1. Go to [developers.facebook.com](https://developers.facebook.com/apps)
2. Create a new app (type: Business)
3. Add WhatsApp product
4. Link your Business Manager

### Step 3: Configure WhatsApp
1. Add a phone number
2. Verify with the code received
3. Note your:
   - **Phone Number ID**
   - **WhatsApp Business Account ID**
   - **Access Token**

### Step 4: Set Up Webhook
1. In n8n, activate the workflow
2. Copy the WhatsApp Trigger webhook URL
3. In Meta Developer Dashboard:
   - Go to WhatsApp → Configuration
   - Add your webhook URL
   - Add a verify token
4. Subscribe to: `messages`, `message_status`

### Step 5: Configure n8n Credentials

**WhatsApp Credentials:**
1. Create HTTP Header Auth credential
2. Header Name: `Authorization`
3. Header Value: `Bearer YOUR_ACCESS_TOKEN`

**OpenAI Credentials:**
1. Add your OpenAI API key
2. Used for chat, transcription, and image analysis

### Step 6: Update Phone Number ID
Replace `470271332838881` in all WhatsApp nodes with your Phone Number ID.

## Nodes Explained

| Node | Purpose |
|------|---------|
| **WhatsApp Trigger** | Receives incoming messages |
| **Input type** | Routes based on message type |
| **Get Audio/Image URL** | Retrieves media URLs |
| **Download Audio/Image** | Downloads media files |
| **Transcribe Audio** | Converts voice to text |
| **Analyze Image** | Describes image content |
| **Extract from File** | Extracts PDF text |
| **AI Agent1** | Processes all inputs and generates responses |
| **Simple Memory** | Maintains conversation context |
| **Send message/audio** | Responds to user |

## AI Agent Configuration

The agent is configured to:
- Process all input types
- Maintain professional tone
- Acknowledge limitations
- Respect privacy
- Format for mobile reading

## Requirements

| Credential | Required | Purpose |
|------------|----------|---------|
| Meta/WhatsApp | Yes | Messaging platform |
| OpenAI | Yes | AI processing |

## Supported Message Types

| Input | Output |
|-------|--------|
| Text message | Text response |
| Voice message | Audio or text response |
| Image | Text analysis |
| PDF document | Text analysis |
| Other | "Unsupported" message |

## Response Flow

### Voice Messages
Voice input can trigger audio responses:
1. Transcribe incoming audio
2. Process with AI
3. Generate audio response
4. Send as voice message

### PDF Handling
Only PDF files are supported:
- Other document types receive an error message
- PDFs are extracted and analyzed

## Memory System

The workflow uses Window Buffer Memory:
- Maintains last 10 exchanges
- Session based on sender's WhatsApp ID
- Enables contextual conversations

## Customization Options

### Change AI Model
Update the OpenAI Chat Model node to use GPT-4, GPT-3.5, etc.

### Adjust Memory Length
Modify `contextWindowLength` in Simple Memory node.

### Add Languages
Update system prompts for multi-language support.

### Custom Responses
Modify the AI Agent system message for your use case.

## Difficulty Level

**Advanced** - Requires Meta Business setup and multiple integrations

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Webhook not receiving | Check URL and verify token |
| Media download fails | Verify authorization header |
| Audio transcription error | Check OpenAI API key |
| Messages not sending | Verify Phone Number ID |

## API Rate Limits

Be aware of WhatsApp Business API limits:
- Message templates for first contact
- Rate limits on API calls
- Media size restrictions

## Security Notes

- Keep access tokens secure
- Use environment variables
- Monitor for unusual activity
- Implement rate limiting if needed

## Related Workflows

- Deep Research Tool - Enhance with research capability
- Error Logger - Monitor for failures
