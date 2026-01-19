# Nano Banana Image Generator

An AI image generation workflow using KIE.ai's Nano Banana Pro model. Supports text-to-image, image-to-image editing, and multi-image composition.

## What This Workflow Does

This workflow provides three image generation modes:

1. **Text to Image**: Generate images from text prompts
2. **Image to Image**: Edit existing images with AI
3. **Multiple Images to Image**: Combine multiple images into one

## Use Cases

- Creating marketing visuals
- Product mockup generation
- Social media content creation
- Concept art and visualization
- Image editing and enhancement

## Workflow Overview

### Text to Image Flow
```
[Schedule] → [Prompt] → [Create Image] → [Wait] → [Get Result] → [Output]
```

### Image to Image Flow
```
[Form] → [Upload to IMGBB] → [Edit Image] → [Wait] → [Get Result] → [Output]
```

### Multi-Image Flow
```
[Schedule] → [Prompts/Images] → [Edit Images] → [Wait] → [Get Result] → [Output]
```

## Setup Instructions

### Step 1: Get Your KIE.ai API Key
1. Sign up at [kie.ai](https://kie.ai)
2. Navigate to your API settings
3. Copy your API key

### Step 2: Get Your IMGBB API Key
1. Sign up at [imgbb.com](https://imgbb.com/)
2. Go to API settings
3. Generate and copy your API key

### Step 3: Configure API Keys
1. Find all HTTP Request nodes pointing to `kie.ai`
2. Replace `YOUR API KEY` with your KIE API key
3. Find the IMGBB upload node
4. Replace `YOUR API KEY` with your IMGBB key

### Step 4: Test Each Mode

**Text to Image:**
1. Edit the "Image Prompt" node with your prompt
2. Run the workflow manually

**Image to Image:**
1. Activate the workflow
2. Open the form trigger URL
3. Upload an image and add a prompt

**Multi-Image:**
1. Edit "Prompt/Images" node with image URLs
2. Run the workflow manually

## API Configuration

### Nano Banana Pro Parameters

| Parameter | Options | Description |
|-----------|---------|-------------|
| `aspect_ratio` | 1:1, 16:9, 9:16, etc. | Image dimensions |
| `resolution` | 4K, HD, SD | Output quality |
| `output_format` | png, jpeg | File format |
| `image_input` | URLs array | Source images for editing |

## Nodes Explained

| Node | Purpose |
|------|---------|
| **Schedule Trigger** | Starts text-to-image generation |
| **Form Trigger** | Accepts image uploads for editing |
| **Image Prompt** | Defines the generation prompt |
| **Create/Edit Image** | Calls KIE.ai API |
| **Wait** | Pauses for image generation |
| **Get Image** | Retrieves the generated image |
| **Switch** | Routes based on generation status |
| **Result** | Extracts the final image URL |

## Example Prompts

**Text to Image:**
- "A hyper-realistic image of the Chicago skyline at sunset"
- "A cozy coffee shop interior with warm lighting"
- "A futuristic cityscape with flying cars"

**Image to Image:**
- "Transform this photo into an oil painting style"
- "Add snow to this landscape image"
- "Make this portrait look like a comic book character"

**Multi-Image Composition:**
- "A person wearing the shirt from image 1, holding the item from image 2"
- "Combine these product images into a lifestyle scene"

## Requirements

| Credential | Required | Purpose |
|------------|----------|---------|
| KIE.ai API | Yes | Image generation |
| IMGBB API | Yes | Image hosting for uploads |

## Generation Status Flow

The workflow handles three states:
- **Success**: Image is ready, extract URL
- **Generating**: Still processing, wait and retry
- **Fail**: Generation failed, check logs

## Customization Options

### Change Resolution
Edit the API request body to adjust quality settings.

### Add Post-Processing
Include image optimization or format conversion.

### Store Results
Add Google Drive or S3 upload for permanent storage.

### Add Notifications
Send completed images via email or Slack.

## Difficulty Level

**Intermediate** - Requires API setup and understanding of async processing

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Generation stuck | Check KIE API key and rate limits |
| Image upload fails | Verify IMGBB API key |
| Poor quality | Try more specific prompts |
| Timeout errors | Increase wait times |

## Related Workflows

- Nano Banana Image Link - Sub-workflow for image processing
- Newsletter Automation - Use generated images in content
