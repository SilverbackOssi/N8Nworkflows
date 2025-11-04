# Notification Workflows

This directory contains workflows for sending alerts and notifications through various channels.

## Available Workflows

### Slack Alert Notification
**File:** `slack-alert-notification.json`

**Description:** A webhook-triggered workflow that sends formatted alerts to Slack channels.

**Features:**
- Webhook trigger for easy integration
- Flexible message formatting
- Severity levels support
- Timestamp tracking

**Prerequisites:**
- Slack workspace
- Slack API credentials configured in N8N
- A Slack channel for alerts

**Use Cases:**
- System monitoring alerts
- Error notifications
- Status updates
- Event notifications

**Setup:**
1. Import the workflow into N8N
2. Configure your Slack API credentials
3. Update the target channel in the "Send to Slack" node
4. Activate the workflow to get the webhook URL
5. Send POST requests to the webhook URL with this payload structure:
   ```json
   {
     "title": "Alert Title",
     "message": "Alert details",
     "severity": "info|warning|error"
   }
   ```

**Nodes Used:**
- Webhook Trigger node
- Function node (for message formatting)
- Slack node

**Customization:**
- Modify the message format in the Function node
- Change the Slack channel
- Add additional fields or formatting
- Add filtering logic for different severity levels
