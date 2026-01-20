# Firecrawl Search Agent

An AI-powered web search workflow using Firecrawl's search API. Features an intelligent agent that converts natural language queries into optimized search requests.

## What This Workflow Does

This workflow enables powerful web searching through:

1. A chat interface for natural language queries
2. An AI agent that constructs optimized search queries
3. Firecrawl API integration for comprehensive results
4. Structured output with URLs, content, and screenshots

## Use Cases

- Lead generation and research
- Competitive analysis
- Content discovery
- Market research
- Finding specific resources online

## Workflow Overview

```
[Chat Trigger] → [Search Agent] → [Firecrawl API] → [Results]
```

### Nodes Explained

| Node | Purpose |
|------|---------|
| **Chat Trigger** | Accepts natural language search requests |
| **Search Agent** | AI converts requests to Firecrawl queries |
| **GPT 4.1 mini** | Powers the agent's query construction |
| **Firecrawl Search** | HTTP tool that calls the Firecrawl API |

## Setup Instructions

### Step 1: Get Your Firecrawl API Key
1. Sign up at [firecrawl.dev](https://firecrawl.dev)
2. Navigate to your dashboard
3. Copy your API key

### Step 2: Configure Credentials
1. In n8n, go to **Credentials**
2. Create a new **HTTP Header Auth** credential
3. Set Header Name: `Authorization`
4. Set Header Value: `Bearer YOUR_API_KEY`

### Step 3: Add OpenRouter Credentials
1. Get an API key from [openrouter.ai](https://openrouter.ai/)
2. Add OpenRouter credentials in n8n

### Step 4: Activate and Test
1. Toggle the workflow to **Active**
2. Open the chat interface
3. Try a search query

## Query Operators

The AI agent understands these search operators:

| Operator | Purpose | Example |
|----------|---------|---------|
| `"phrase"` | Exact match | `"AI automation"` |
| `-term` | Exclude | `-site:linkedin.com` |
| `site:` | Specific domain | `site:youtube.com` |
| `inurl:` | Word in URL | `inurl:tutorial` |
| `intitle:` | Word in title | `intitle:guide` |
| `related:` | Similar sites | `related:example.com` |

## API Parameters

| Parameter | Default | Description |
|-----------|---------|-------------|
| `query` | Required | Search string with operators |
| `limit` | 5 | Results count (1-100) |
| `lang` | en | Language code |
| `country` | us | Country bias |
| `tbs` | - | Time filter (e.g., `qdr:d` for past day) |

## Example Queries

- "Find YouTube videos about n8n automation tutorials"
- "Search for AI startups but exclude LinkedIn"
- "Look for documentation about webhook integration"
- "Find recent news about automation tools from the past week"

## Requirements

| Credential | Required | Purpose |
|------------|----------|---------|
| Firecrawl API | Yes | Web search functionality |
| OpenRouter API | Yes | Powers the AI agent |

## Scrape Options

The workflow can return multiple formats:
- `markdown` - Page content as Markdown
- `html` - Raw HTML
- `links` - Extracted links
- `screenshot` - Full page screenshots
- `json` - Structured data

## Difficulty Level

**Intermediate** - Requires API credentials setup

## Troubleshooting

| Issue | Solution |
|-------|----------|
| No results | Check API key and query format |
| Rate limited | Reduce request frequency |
| Missing content | Try different scrape options |

## Related Workflows

- Deep Research Tool - For AI-powered research
- n8n Developer Agent - For building automations
