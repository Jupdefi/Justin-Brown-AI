# Error Logger

A centralized error handling workflow that captures errors from all your n8n workflows, logs them to Google Sheets, and sends Slack notifications. Essential for monitoring and debugging your automations.

## What This Workflow Does

When any workflow in your n8n instance encounters an error:

1. Captures the error details automatically
2. Logs error information to a Google Sheet
3. Sends an alert to your Slack channel
4. Provides a direct link to the failed execution

## Use Cases

- Centralized error monitoring
- Debugging workflow failures
- Creating an audit trail
- Real-time error notifications
- Team collaboration on issues

## Workflow Overview

```
[Error Trigger] → [Log Error to Sheets]
                → [Send Slack Notification]
```

### Nodes Explained

| Node | Purpose |
|------|---------|
| **Error Trigger** | Automatically catches errors from other workflows |
| **Log Error** | Appends error details to Google Sheets |
| **Notification** | Sends formatted error alert to Slack |

## Setup Instructions

### Step 1: Create Your Error Log Spreadsheet
1. Make a copy of the [Error Logs template](https://docs.google.com/spreadsheets/d/1Aiz1cpv1k6Qlmp1Cjmj0ZtNuG6fC_cG24O_XaiP8NOs/edit?usp=sharing)
2. The template includes columns: Timestamp, Workflow, URL, Node, Error Message

### Step 2: Configure Google Sheets
1. Add your **Google Sheets** credentials in n8n
2. Update the Google Sheets node with your spreadsheet ID
3. Verify the sheet name matches (default: "Sheet1")

### Step 3: Set Up Slack Notifications (Optional)
1. Create a Slack app or use an existing one
2. Add **Slack OAuth2** credentials in n8n
3. Update the Slack node with your channel ID
4. Test the connection

### Step 4: Link as Error Workflow
1. Go to **Settings** → **Workflows** → **Error Workflow**
2. Select this workflow as your global error handler
3. **Important**: This workflow must be **Active**

### Step 5: Activate the Workflow
1. Toggle the workflow to **Active**
2. Test by triggering an error in another workflow

## Logged Information

| Field | Description |
|-------|-------------|
| Timestamp | When the error occurred |
| Workflow | Name of the failed workflow |
| URL | Direct link to the execution |
| Node | Which node caused the error |
| Error Message | The actual error description |

## Slack Notification Format

```
Workflow Error: [Workflow Name]

[Node Name] errored at [Timestamp].

The error message was: [Error Details]

See this execution here: [Link]
```

## Requirements

| Credential | Required | Purpose |
|------------|----------|---------|
| Google Sheets | Yes | Error logging |
| Slack | Optional | Real-time notifications |

## Customization Options

### Add Email Notifications
Add a Gmail or SMTP node to send email alerts.

### Add More Fields
Log additional data like workflow ID, execution ID, or custom tags.

### Filter Errors
Add a Switch node to only alert on critical errors.

### Multiple Channels
Route different workflows' errors to different Slack channels.

## Best Practices

1. **Keep Active**: This workflow must always be active
2. **Monitor the Sheet**: Review errors regularly
3. **Clean Up**: Archive old errors periodically
4. **Set Permissions**: Control who can access error logs

## Difficulty Level

**Beginner** - Simple setup with standard integrations

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Errors not logging | Verify workflow is active and set as error workflow |
| Slack not sending | Check OAuth credentials and channel permissions |
| Missing data | Ensure spreadsheet columns match expected fields |

## Related Workflows

- Hello World Webhook - Basic workflow testing
- Newsletter Automation - Example workflow to monitor
