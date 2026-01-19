# Hello World Webhook

A simple starter workflow demonstrating webhook handling in n8n. Perfect for beginners learning the basics of n8n automation.

## What This Workflow Does

This workflow creates a basic HTTP endpoint that responds with a greeting message. When triggered, it:

1. Receives an incoming HTTP GET request
2. Creates a response with a greeting message and timestamp
3. Returns the response as JSON

## Use Cases

- Learning n8n basics
- Testing webhook connectivity
- Creating simple API endpoints
- Building a foundation for more complex workflows

## Workflow Overview

```
[Webhook] → [Set Response] → [Respond to Webhook]
```

### Nodes Explained

| Node | Purpose |
|------|---------|
| **Webhook** | Listens for incoming HTTP GET requests at `/hello-world` |
| **Set Response** | Creates the response data with message and timestamp |
| **Respond to Webhook** | Returns the JSON response to the caller |

## Setup Instructions

### Step 1: Import the Workflow
1. Copy the workflow JSON
2. In n8n, go to **Workflows** → **Import from File/URL**
3. Paste the JSON and click **Import**

### Step 2: Activate the Workflow
1. Toggle the workflow to **Active** (top right)
2. Copy the webhook URL shown in the Webhook node

### Step 3: Test It
Open your browser or use curl:
```bash
curl https://your-n8n-instance.com/webhook/hello-world
```

## Expected Response

```json
{
  "message": "Hello from n8n!",
  "timestamp": "2025-01-19T12:00:00.000Z"
}
```

## Customization Ideas

- Change the response message
- Add query parameters handling
- Switch to POST method for receiving data
- Add authentication for security

## Requirements

- n8n instance (self-hosted or cloud)
- No external credentials needed

## Difficulty Level

**Beginner** - No prior n8n experience required

## Related Workflows

- Error Logger - Learn error handling
- Firecrawl Search - More advanced HTTP requests
