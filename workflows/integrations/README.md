# Integration Workflows

This directory contains workflows that integrate different third-party services and platforms.

## Available Workflows

### GitHub to Discord Integration
**File:** `github-to-discord.json`

**Description:** Automatically post GitHub events (PRs, issues, commits) to a Discord channel.

**Features:**
- Webhook-based GitHub integration
- Automatic event parsing
- Formatted Discord messages
- Support for multiple event types

**Prerequisites:**
- GitHub repository with admin access
- Discord server with webhook permissions
- Discord webhook URL

**Use Cases:**
- Team notifications for repository activity
- Project management updates
- Development workflow tracking
- Community engagement

**Setup:**
1. Import the workflow into N8N
2. Create a Discord webhook in your target channel:
   - Go to Server Settings → Integrations → Webhooks
   - Click "New Webhook"
   - Copy the webhook URL
3. Update the "Send to Discord" node with your webhook URL
4. Activate the workflow to get the webhook URL
5. Configure GitHub webhook:
   - Go to your repository Settings → Webhooks
   - Click "Add webhook"
   - Paste the N8N webhook URL
   - Select the events you want to track
   - Set content type to `application/json`

**Supported Events:**
- Pull requests (opened, closed, merged)
- Issues (opened, closed, commented)
- Push events
- And more GitHub events

**Nodes Used:**
- Webhook node (GitHub)
- Function node (event parsing)
- Discord node

**Customization:**
- Modify event parsing logic for different GitHub events
- Change message formatting
- Add filtering for specific events
- Include additional event details
