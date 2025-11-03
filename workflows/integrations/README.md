# Integration Workflows

This directory contains workflows that integrate different third-party services and platforms.

## Available Workflows

### Crypto AI Agent Chatbot
**File:** `crypto-ai-agent-chatbot.json`

**Description:** An AI-powered chatbot that represents a cryptocurrency company, providing customer support, answering questions, and educating users about crypto and blockchain technology.

**Features:**
- OpenAI GPT-4 powered responses
- Context-aware conversations with company branding
- Multi-platform support (web, mobile, messaging apps)
- Analytics tracking for conversation insights
- Professional cryptocurrency domain knowledge
- Security-focused guidance

**Prerequisites:**
- OpenAI API account and API key
- N8N instance with OpenAI credentials configured
- Optional: Analytics endpoint for tracking conversations

**Use Cases:**
- Customer support automation
- Educational crypto Q&A
- Market insights and trading help
- Account assistance
- Security best practices guidance
- 24/7 availability for users

**Setup:**
1. Import the workflow into N8N
2. Configure OpenAI API credentials:
   - Go to Credentials → Add Credential → OpenAI
   - Enter your OpenAI API key
3. Customize the company context in "Process Input" node:
   - Update `companyName` to your crypto company name
   - Modify `capabilities` based on your services
4. (Optional) Configure analytics endpoint in "Send Analytics" node
5. Activate the workflow to get the webhook URL
6. Integrate the webhook into your:
   - Website chat widget
   - Mobile app
   - Telegram/Discord bot
   - WhatsApp Business

**Request Format:**
Send POST requests to the webhook URL with this payload:
```json
{
  "message": "What is Bitcoin?",
  "userId": "user123",
  "platform": "web"
}
```

**Response Format:**
```json
{
  "success": true,
  "response": "Bitcoin is a decentralized digital currency...",
  "userId": "user123",
  "platform": "web",
  "timestamp": "2025-11-03T21:30:00.000Z",
  "metadata": {
    "model": "gpt-4",
    "tokensUsed": 150,
    "conversationId": "user123-1730672400000"
  }
}
```

**Nodes Used:**
- Webhook node (receives chat messages)
- Function nodes (process input, format response, log analytics)
- OpenAI node (generates AI responses)
- Respond to Webhook node (sends response back)
- HTTP Request node (sends analytics)

**Customization:**
- Adjust AI temperature for more creative or conservative responses
- Modify system prompt to change agent personality and expertise
- Add conversation history for multi-turn conversations
- Implement rate limiting for API cost control
- Add language detection and multilingual support
- Integrate with your CRM or support ticketing system
- Add sentiment analysis for customer satisfaction tracking

**Cost Considerations:**
- GPT-4 API calls are metered by OpenAI
- Monitor token usage via analytics
- Consider using GPT-3.5-turbo for cost savings
- Implement caching for common questions

**Security Notes:**
- Never share your OpenAI API key
- Implement rate limiting to prevent abuse
- Sanitize user inputs
- Monitor for inappropriate usage
- Consider adding user authentication

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
