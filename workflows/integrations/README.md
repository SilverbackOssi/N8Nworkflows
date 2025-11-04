# Integration Workflows

This directory contains workflows that integrate different third-party services and platforms.

## Available Workflows

### Crypto AI Agent Chatbot
**File:** `crypto-ai-agent-chatbot.json`

**Description:** An AI-powered chatbot that represents a cryptocurrency company, providing customer support, answering questions, and educating users about crypto and blockchain technology. **The chatbot dynamically pulls company information from a file or website** to ensure up-to-date, accurate responses.

**Features:**
- OpenAI GPT-4 powered responses
- **Dynamic company information loading from file or website API**
- Context-aware conversations with company branding
- Multi-platform support (web, mobile, messaging apps)
- Analytics tracking for conversation insights
- Professional cryptocurrency domain knowledge
- Security-focused guidance
- Automatic fallback to default values if data source is unavailable

**Prerequisites:**
- OpenAI API account and API key
- N8N instance with OpenAI credentials configured
- Company information source (choose one):
  - JSON file at `/data/company-info.json` on your N8N server
  - OR website API endpoint returning company information
- Optional: Analytics endpoint for tracking conversations

**Use Cases:**
- Customer support automation with current product information
- Educational crypto Q&A
- Market insights and trading help
- Account assistance with up-to-date policies
- Security best practices guidance
- 24/7 availability for users

**Setup:**
1. Import the workflow into N8N

2. Configure OpenAI API credentials:
   - Go to Credentials → Add Credential → OpenAI
   - Enter your OpenAI API key

3. **Set up company information source (choose one method):**

   **Option A: Use a JSON file**
   - Create a file at `/data/company-info.json` on your N8N server
   - Use the provided `company-info-sample.json` as a template
   - Update the file path in "Read Company Info (File)" node if needed

   **Option B: Use a website API**
   - Update the URL in "Fetch Company Info (Website)" node
   - Point it to your company's API endpoint (e.g., `https://yourcompany.com/api/company-info`)
   - Ensure the endpoint returns JSON with company information

4. (Optional) Configure analytics endpoint in "Send Analytics" node

5. Activate the workflow to get the webhook URL

6. Integrate the webhook into your:
   - Website chat widget
   - Mobile app
   - Telegram/Discord bot
   - WhatsApp Business

**Company Information Format:**
See `company-info-sample.json` for the complete structure. The JSON should include:
```json
{
  "companyName": "Your Company Name",
  "industry": "Cryptocurrency & Blockchain",
  "description": "Brief company description",
  "products": ["Product 1", "Product 2"],
  "features": ["Feature 1", "Feature 2"],
  "capabilities": ["Capability 1", "Capability 2"],
  "website": "https://yourcompany.com",
  "support_email": "support@yourcompany.com",
  "trading_pairs": ["BTC/USD", "ETH/USD"],
  "supported_networks": ["Bitcoin", "Ethereum"],
  "faq": {
    "minimum_deposit": "$10",
    "withdrawal_time": "1-24 hours",
    "verification_required": "Yes",
    "available_countries": "150+ countries",
    "mobile_app": "Available on iOS and Android"
  }
}
```

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
    "conversationId": "user123-1730672400000",
    "companyContext": "CryptoVision"
  }
}
```

**Nodes Used:**
- Webhook node (receives chat messages)
- **HTTP Request node (fetches company info from website API)**
- **Read Binary File node (reads company info from file)**
- Function nodes (process input, merge company context, format response, log analytics)
- OpenAI node (generates AI responses with company context)
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
- **Update company information dynamically without redeploying the workflow**
- **Use webhooks to trigger company info refresh**

**Dynamic Information Updates:**
The workflow automatically pulls fresh company information on each request, meaning:
- Update your company info file or API and changes take effect immediately
- No need to redeploy or modify the workflow
- Perfect for keeping product catalogs, pricing, and features current
- Supports A/B testing different company descriptions

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
- Secure your company info file/API endpoint

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
