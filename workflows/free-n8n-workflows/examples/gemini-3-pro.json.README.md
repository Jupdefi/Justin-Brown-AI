# Gemini 3 Pro Workflow Builder

An AI workflow generator powered by Google's Gemini 3 Pro model. Converts natural language descriptions into complete n8n workflows and automatically creates them in your instance.

## What This Workflow Does

This workflow provides AI-assisted workflow creation:

1. Accepts workflow descriptions via chat interface
2. Uses Gemini 3 Pro for intelligent workflow design
3. References n8n documentation for accuracy
4. Generates valid workflow JSON
5. Creates the workflow via n8n API
6. Returns a direct link to the new workflow

## Use Cases

- Rapid workflow prototyping
- Learning n8n patterns and best practices
- Automating repetitive workflow creation
- Exploring different automation approaches

## Workflow Overview

```
[Chat Trigger] → [Get Docs] → [Extract Text] → [n8n Builder] → [Create Workflow] → [Link]
```

### Nodes Explained

| Node | Purpose |
|------|---------|
| **Chat Trigger** | Receives workflow requests |
| **Get n8n Docs** | Downloads documentation from Google Drive |
| **Extract from File** | Converts docs to text for AI context |
| **n8n Builder** | Gemini-powered workflow generator |
| **n8n** | Creates the workflow via API |
| **Workflow Link** | Returns the link to created workflow |

## Setup Instructions

### Step 1: Get Required API Keys

| Service | Where to Get It |
|---------|-----------------|
| Google AI (Gemini) | [ai.google.dev](https://ai.google.dev/) |
| n8n API | Your n8n instance → Settings → API |

### Step 2: Set Up Documentation
1. Copy the [n8n Documentation](https://docs.google.com/document/d/1TiRusVo4DbbANwAr7I0GUGDZY3pmEmHZy3k66mRxLCg/edit?usp=sharing)
2. Connect Google Drive credentials
3. Update the node with your document ID

### Step 3: Configure Credentials
1. Add **Google AI** credentials for Gemini
2. Add **n8n API** credentials
3. Add **Google Drive** credentials

### Step 4: Update Instance URL
1. Find the "Workflow Link" node
2. Replace `your-n8n-instance.app.n8n.cloud` with your actual URL

### Step 5: Activate and Test
1. Toggle the workflow to **Active**
2. Open the chat interface
3. Describe a workflow you want to create

## Example Prompts

- "Build a workflow that monitors RSS feeds and posts to Discord"
- "Create an automation that backs up Notion pages to Google Drive daily"
- "Make a workflow that converts incoming emails to Trello cards"
- "Design a system that aggregates social media mentions"

## Requirements

| Credential | Required | Purpose |
|------------|----------|---------|
| Google AI (Gemini) | Yes | Powers the AI builder |
| n8n API | Yes | Creates workflows |
| Google Drive | Yes | Accesses documentation |

## Output Format

The generated workflows include:
- Properly configured nodes
- Correct node connections
- Descriptive sticky notes
- Workflow settings
- Ready-to-use configuration

## Customization Options

### Change AI Model
Swap Gemini for other models by updating the language model node.

### Enhance Documentation
Add more examples to the Google Doc for better results.

### Add Validation
Include a validation step before creating the workflow.

## Tips for Best Results

1. **Be Specific**: Include details about triggers, data sources, and outputs
2. **Name Services**: Mention specific apps (Slack, Gmail, etc.)
3. **Describe Flow**: Explain the sequence of operations
4. **Include Conditions**: Mention any filtering or branching logic

## Difficulty Level

**Intermediate** - Requires multiple credentials and API setup

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Invalid JSON | Try simpler workflow descriptions |
| Missing nodes | AI may not know newest n8n nodes |
| Creation fails | Verify n8n API permissions |
| No documentation | Check Google Drive connection |

## Related Workflows

- n8n Developer Agent - Alternative with Claude
- Deep Research Tool - AI-powered research
