# Nano Banana Image Link (Sub-workflow)

A utility workflow that combines multiple images using AI. Designed to be called by other workflows for image composition tasks.

## What This Workflow Does

This sub-workflow:

1. Accepts image URLs and a prompt from a parent workflow
2. Downloads images from Google Drive
3. Uploads them to IMGBB for public URLs
4. Sends to Fal.ai's Nano Banana for AI composition
5. Saves the result to Google Drive
6. Returns a link to the final image

## Use Cases

- Image composition automation
- Product photo manipulation
- Marketing asset generation
- Batch image processing

## Workflow Overview

```
[Input] → [Download Images] → [Get URLs] → [Create Image] → [Poll Result] → [Upload to Drive] → [Return Link]
```

### Nodes Explained

| Node | Purpose |
|------|---------|
| **When Executed by Another Workflow** | Receives input from parent workflow |
| **Edit Fields** | Prepares image URLs array |
| **Split Out** | Processes each image separately |
| **Download file** | Gets images from Google Drive |
| **Get URL** | Uploads to IMGBB for public URLs |
| **Aggregate** | Combines processed data |
| **Create Image** | Calls Fal.ai Nano Banana API |
| **10 Seconds / 5 Seconds** | Wait nodes for polling |
| **Get Result** | Retrieves generated image |
| **Download Image** | Downloads the result |
| **Upload file** | Saves to Google Drive |
| **Result** | Returns success message with link |

## Input Parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `prompt` | String | Description of desired output |
| `image1` | String | Google Drive file ID |
| `image2` | String | Google Drive file ID |
| `imageTitle` | String | Name for the output file |

## Setup Instructions

### Step 1: Configure Credentials

**Required credentials:**
- **IMGBB** - HTTP Query Auth with API key
- **Fal.ai** - HTTP Header Auth with API key
- **Google Drive** - OAuth2 connection

### Step 2: Set Up Google Drive Folder
1. Create a folder in Google Drive for outputs
2. Update the "Upload file" node with your folder ID

### Step 3: Configure Fal.ai
1. Sign up at [fal.ai](https://fal.ai)
2. Get your API key
3. Add as HTTP Header Auth: `Authorization: Key YOUR_KEY`

### Step 4: Link to Parent Workflow
This workflow is called by other workflows using the "Execute Workflow" node.

## API Configuration

### Nano Banana Edit Parameters

```json
{
  "prompt": "Your composition description",
  "image_urls": ["url1", "url2"],
  "num_images": 1,
  "output_format": "jpeg"
}
```

## Polling Logic

The workflow handles async image generation:

1. Submit request → Receive request ID
2. Wait 10 seconds
3. Check status
4. If not ready, wait 5 seconds and retry
5. When complete, download result

## Requirements

| Credential | Required | Purpose |
|------------|----------|---------|
| Google Drive | Yes | Source/destination for images |
| IMGBB | Yes | Temporary public URLs |
| Fal.ai | Yes | AI image composition |

## Error Handling

The "Get Result" node has error handling enabled:
- Success: Continue to download
- Error: Loop back to retry after 5 seconds

## Customization Options

### Change Output Location
Update the Google Drive folder ID in the Upload node.

### Adjust Wait Times
Modify the Wait nodes for faster/slower polling.

### Add More Images
Extend the workflow to handle 3+ input images.

### Change Output Format
Modify the API request to use PNG or other formats.

## Difficulty Level

**Advanced** - Complex async handling and multiple integrations

## Calling This Workflow

From another workflow, use the "Execute Workflow" node:

```javascript
{
  "prompt": "Combine these images into a product scene",
  "image1": "google-drive-file-id-1",
  "image2": "google-drive-file-id-2",
  "imageTitle": "Combined Product Image"
}
```

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Images not downloading | Check Google Drive permissions |
| IMGBB upload fails | Verify API key and file format |
| Generation timeout | Increase wait times |
| Result not saved | Check Drive folder permissions |

## Related Workflows

- Nano Banana Image - Parent workflow for image generation
- Newsletter Automation - Use combined images in content
