# Deep Research Tool

A free, automated AI research workflow that generates structured, fact-based reports using Jina AI's DeepSearch. No API key required for the AI research functionality.

## What This Workflow Does

This workflow automates deep research and report generation:

1. Accepts research queries via a chat interface
2. Sends queries to Jina AI's DeepSearch API
3. Processes and formats the AI-generated insights
4. Returns well-structured Markdown reports with sources

## Use Cases

- Academic research assistance
- Market research and analysis
- Competitive intelligence gathering
- Content research for writers
- Quick fact-finding and verification

## Workflow Overview

```
[Chat Trigger] → [Jina DeepSearch API] → [Format Response] → [Output]
```

### Nodes Explained

| Node | Purpose |
|------|---------|
| **User Research Query Input** | Chat interface for entering research topics |
| **Jina AI DeepSearch Request** | Sends query to Jina's free DeepSearch API |
| **Format & Clean AI Response** | Processes and formats the Markdown output |

## Setup Instructions

### Step 1: Import the Workflow
1. Copy the workflow JSON
2. In n8n, go to **Workflows** → **Import from File/URL**
3. Paste the JSON and click **Import**

### Step 2: Activate and Test
1. Toggle the workflow to **Active**
2. Open the chat interface
3. Enter a research topic

**That's it!** No API keys needed for basic usage.

## Example Queries

- "What are the latest developments in quantum computing?"
- "Provide an analysis of renewable energy trends in 2025"
- "Research the impact of AI on healthcare diagnostics"
- "Summarize recent findings on climate change mitigation"

## How It Works

### The Research Process

1. **Query Analysis** - Your question is formatted for optimal AI processing
2. **Deep Search** - Jina AI searches and analyzes multiple sources
3. **Synthesis** - Information is compiled into a coherent report
4. **Formatting** - Results are cleaned and formatted as readable Markdown

### Output Format

The research reports include:
- Key insights and findings
- Structured analysis
- Source citations
- Formatted footnotes and URLs

## Requirements

| Requirement | Details |
|-------------|---------|
| n8n Instance | Self-hosted or cloud |
| API Keys | **None required** - Jina DeepSearch is free |

## Customization Options

### Adjust Research Depth
Modify the `reasoning_effort` parameter in the HTTP Request node:
- `"low"` - Quick results (default)
- `"medium"` - Balanced depth
- `"high"` - Thorough analysis

### Change Output Format
Edit the Code node to customize how results are formatted.

## Limitations

- Rate limits may apply to free Jina AI usage
- Best for general research topics
- Results quality depends on available online information

## Difficulty Level

**Beginner** - No credentials or complex setup required

## Related Workflows

- Firecrawl Search - For web scraping research
- Newsletter Automation - Use research for content creation
