# Newsletter Automation

An AI-powered newsletter generation workflow that creates fully researched, formatted newsletters from simple topic inputs. Uses multiple AI agents for planning, research, writing, and editing.

## What This Workflow Does

This workflow automates the entire newsletter creation process:

1. Accepts topic, tone, and audience via a web form
2. AI plans a table of contents based on research
3. Multiple agents research each section independently
4. An editor compiles everything into a cohesive newsletter
5. Generates a title and sends via Gmail

## Use Cases

- Automated content marketing
- Internal company newsletters
- Industry news roundups
- Educational content distribution
- Client communication

## Workflow Overview

```
[Form] → [Newsletter Expert] → [Project Planner] → [Split Sections]
                                                          ↓
[Editor] ← [Aggregate] ← [Merge] ← [Research Team] ← [Each Section]
    ↓
[Create Title] → [Send via Gmail]
```

### Nodes Explained

| Node | Purpose |
|------|---------|
| **Form Trigger** | Collects topic, tone, and target audience |
| **Newsletter Expert** | Plans the table of contents |
| **Project Planner** | Structures sections for research |
| **Split Out** | Separates sections for parallel processing |
| **Research Team** | Researches and writes each section |
| **Merge/Aggregate** | Combines all sections |
| **Editor** | Polishes and formats the final newsletter |
| **Create Title** | Generates an engaging title |
| **Send Newsletter** | Delivers via Gmail |

## Setup Instructions

### Step 1: Get Required API Keys

| Service | Purpose | Where to Get |
|---------|---------|--------------|
| OpenAI | Planning & titling | [platform.openai.com](https://platform.openai.com) |
| Anthropic | Research & editing | [console.anthropic.com](https://console.anthropic.com) |
| Tavily | Web research | [tavily.com](https://tavily.com) |

### Step 2: Configure Credentials
1. Add **OpenAI** credentials
2. Add **Anthropic** credentials
3. Add **Gmail** OAuth2 credentials
4. Update Tavily API key in the HTTP Request node

### Step 3: Set Up Tavily Tool
The workflow includes a sub-workflow for Tavily searches:
1. Configure the "Tavily" HTTP Request node with your API key
2. Link the "tavily" tool node to this sub-workflow

### Step 4: Configure Gmail
1. Set up Gmail OAuth2 credentials
2. Update the recipient email in the Gmail node

### Step 5: Test the Workflow
1. Activate the workflow
2. Open the form URL
3. Submit a topic, tone, and audience

## Form Fields

| Field | Description | Example |
|-------|-------------|---------|
| **Topic** | Newsletter subject | "Voice AI" |
| **Tone** | Writing style | Professional, Funny |
| **Target Audience** | Who receives it | "Dentist Offices" |

## AI Agent Roles

### Newsletter Expert
- Analyzes the topic
- Researches trending subtopics
- Creates a structured table of contents

### Project Planner
- Splits TOC into individual sections
- Maintains audience and tone context

### Research Team
- Researches each section independently
- Writes content with citations
- Includes hyperlinked sources

### Editor
- Compiles all sections
- Ensures consistent formatting
- Creates the sources section
- Limits output to 1000 words

## Requirements

| Credential | Required | Purpose |
|------------|----------|---------|
| OpenAI | Yes | TOC and title generation |
| Anthropic | Yes | Research and editing |
| Tavily | Yes | Web research |
| Gmail | Yes | Newsletter delivery |

## Output Format

The newsletter includes:
- Multiple researched sections
- Inline citations with hyperlinks
- Consistent formatting (HTML)
- Complete sources list
- Auto-generated title

## Customization Options

### Change Delivery Method
Replace Gmail with:
- Mailchimp for lists
- SendGrid for bulk sending
- Slack for team updates

### Adjust Section Count
Modify the Newsletter Expert prompt to generate more/fewer sections.

### Add Images
Integrate with image generation workflows for visuals.

### Save to CMS
Add nodes to publish to WordPress, Ghost, etc.

## Example Output Structure

```
[Section 1 Title]
[Researched content with citations]

[Section 2 Title]
[Researched content with citations]

...

Sources:
- [Source 1](url)
- [Source 2](url)
```

## Difficulty Level

**Advanced** - Multiple AI integrations and complex data flow

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Sections missing | Check Split Out node configuration |
| No citations | Verify Tavily API key |
| Email not sending | Check Gmail OAuth permissions |
| Formatting issues | Review Editor system prompt |

## Related Workflows

- Deep Research Tool - Standalone research
- Firecrawl Search - Alternative research method
