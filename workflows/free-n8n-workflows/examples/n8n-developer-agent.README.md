# n8n Developer Agent

An AI-powered workflow builder that automatically creates n8n workflows from natural language descriptions. Simply describe what you want to automate, and the agent generates a complete, importable workflow.

## What This Workflow Does

This workflow uses AI (Claude Opus 4 and GPT-4) to:

1. Accept natural language descriptions of automation needs
2. Research n8n documentation for best practices
3. Generate valid, production-ready n8n workflow JSON
4. Automatically create the workflow in your n8n instance
5. Return a link to the finished workflow

## Use Cases

- Rapidly prototype n8n workflows
- Learn n8n node configurations
- Generate workflow templates
- Accelerate automation development

## Workflow Overview

```
[Chat Trigger] → [Developer Agent] → [Developer Tool] → [n8n API] → [Workflow Link]
```

### Nodes Explained

| Node | Purpose |
|------|---------|
| **Chat Trigger** | Receives natural language workflow requests |
| **n8n Developer** | Main AI agent that processes requests |
| **Developer Tool** | Sub-workflow that generates the JSON |
| **n8n Builder** | Creates the workflow using n8n documentation |
| **n8n** | API node that creates the workflow |
| **Workflow Link** | Returns link to the created workflow |

## Setup Instructions

### Step 1: Get Your API Keys

You'll need the following credentials:

- **OpenRouter API Key** - Get one at [openrouter.ai](https://openrouter.ai/)
- **Anthropic API Key** (Optional) - For Claude Opus 4 thinking capabilities at [console.anthropic.com](https://console.anthropic.com/dashboard)
- **n8n API Key** - Create in your n8n instance under Settings → API

### Step 2: Set Up Google Drive Documentation

1. Make a copy of the [n8n Documentation template](https://docs.google.com/document/d/1TiRusVo4DbbANwAr7I0GUGDZY3pmEmHZy3k66mRxLCg/edit?usp=sharing)
2. Connect your Google credentials in n8n
3. Update the Google Drive node with your document ID

### Step 3: Configure Credentials

1. Add your **OpenRouter** credentials
2. Add your **Anthropic** credentials (optional)
3. Add your **n8n API** credentials
4. Add your **Google Drive** credentials

### Step 4: Update Workflow Settings

1. Change `YOUR N8N DOMAIN` in the Workflow Link node to your actual n8n URL
2. Link the Developer Tool to the correct sub-workflow ID

### Step 5: Test the Agent

1. Activate the workflow
2. Open the chat interface
3. Describe a workflow you want to create

## Example Prompts

- "Create a workflow that sends a Slack message every morning at 9am"
- "Build an automation that saves Gmail attachments to Google Drive"
- "Make a workflow that monitors a website and alerts me when it changes"

## Requirements

| Credential | Required | Purpose |
|------------|----------|---------|
| OpenRouter API | Yes | Powers the main AI agent |
| Anthropic API | Optional | Enables extended thinking |
| n8n API | Yes | Creates workflows automatically |
| Google Drive | Yes | Accesses n8n documentation |

## Tips for Best Results

- Be specific about triggers and actions
- Mention which apps/services you want to connect
- Describe the data flow you expect
- Include any conditions or filters needed

## Difficulty Level

**Intermediate** - Requires multiple API credentials and understanding of n8n basics

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Workflow not created | Check n8n API credentials and permissions |
| Invalid JSON generated | Try being more specific in your request |
| Missing nodes | The AI may not know about newer n8n nodes |
