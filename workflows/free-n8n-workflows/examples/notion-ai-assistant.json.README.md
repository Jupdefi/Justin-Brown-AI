# Notion AI Assistant Generator

An AI workflow that generates custom Notion database assistant chatbots. Input a Notion database URL and receive a complete n8n workflow for querying that database via chat.

## What This Workflow Does

This workflow creates custom AI assistants for any Notion database:

1. Accepts a Notion database URL via chat
2. Fetches and analyzes the database schema
3. Uses AI to generate a custom workflow
4. Validates the generated workflow JSON
5. Outputs the workflow ready for import

## Use Cases

- Creating knowledge base chatbots
- Building FAQ assistants
- Generating database query interfaces
- Automating Notion interactions
- Customer support bots from Notion docs

## Workflow Overview

```
[Chat] → [Get Notion Schema] → [Simplify Properties] → [AI Generator] → [Validate] → [Output]
```

### Nodes Explained

| Node | Purpose |
|------|---------|
| **Chat Trigger** | Accepts Notion database URLs |
| **Notion** | Fetches database schema |
| **Simplify Properties** | Cleans schema for AI processing |
| **Set Input Data** | Prepares data with template |
| **Generate Workflow Agent** | Creates the custom workflow |
| **Check for WF JSON errors** | Validates output |
| **Valid n8n workflow JSON?** | Confirms validity |
| **Return success to chat** | Outputs the workflow |

## Setup Instructions

### Step 1: Connect Notion
1. Create a Notion integration at [notion.so/my-integrations](https://www.notion.so/my-integrations)
2. Get your API key
3. Share your databases with the integration
4. Add Notion credentials in n8n

### Step 2: Configure Anthropic
1. Get an API key from [console.anthropic.com](https://console.anthropic.com)
2. Add Anthropic credentials in n8n
3. The workflow uses Claude for generation

### Step 3: Test the Workflow
1. Activate the workflow
2. Open the chat interface
3. Paste a Notion database URL

## Input Requirements

The workflow accepts:
- Public Notion database URLs
- Private database URLs (if integration has access)
- Format: `https://www.notion.so/...`

## Generated Workflow Features

The output workflow includes:

| Component | Description |
|-----------|-------------|
| **Chat Trigger** | Public chat interface |
| **Database Fetch** | Gets database info |
| **AI Agent** | Processes queries |
| **Search Tool** | Queries the database |
| **Content Retrieval** | Gets page details |
| **Memory** | Maintains conversation context |

## Example Usage

1. **Input**: Paste URL of your company FAQ database
2. **Output**: A chatbot workflow that can answer questions from that FAQ
3. **Result**: Users can ask natural language questions about your FAQ content

## Requirements

| Credential | Required | Purpose |
|------------|----------|---------|
| Notion | Yes | Access database schemas |
| Anthropic | Yes | AI workflow generation |

## How It Works

### Schema Analysis
1. Fetches database properties
2. Identifies field types (text, select, multi-select, etc.)
3. Extracts options for select fields
4. Simplifies for AI processing

### Workflow Generation
1. Uses a template workflow as a base
2. AI customizes for the specific schema
3. Updates search queries and filters
4. Adjusts prompts for the database content

### Validation
1. Checks for common errors
2. Verifies JSON structure
3. Retries if invalid
4. Confirms workflow is importable

## Output Format

The workflow is returned as JSON that can be:
1. Copied from the chat
2. Pasted into n8n (v1.52.0+)
3. Immediately used

## Customization Options

### Modify the Template
Edit the template workflow in "Set Input Data" to change:
- Default AI model
- System prompts
- Search parameters

### Add Features
Extend generated workflows with:
- Additional tools
- Different memory types
- Custom output formatting

## Tips for Best Results

1. **Simple Schemas**: Works best with clear property names
2. **Select Fields**: Include options for better filtering
3. **Descriptions**: Add descriptions to Notion properties
4. **Test First**: Try generated workflow before deploying

## Difficulty Level

**Advanced** - Complex AI generation with validation loops

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Invalid URL error | Ensure database is shared with integration |
| Generation fails | Try a simpler database first |
| Invalid JSON | Workflow will auto-retry |
| Missing fields | Check database schema in Notion |

## Limitations

- Works best with databases under 100 properties
- May need manual adjustments for complex schemas
- Generated workflows require credential setup

## Related Workflows

- n8n Developer Agent - General workflow generation
- Deep Research Tool - AI-powered research
