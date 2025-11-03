# Quick Start Guide

Welcome to the N8N Workflows repository! This guide will help you get started quickly.

## What is N8N?

N8N is a powerful workflow automation tool that allows you to connect different services and automate tasks without writing code. It's like Zapier or Make, but open-source and self-hosted.

## Getting N8N

### Cloud Version (Easiest)
1. Sign up at [n8n.cloud](https://n8n.cloud)
2. Get instant access to a hosted N8N instance

### Self-Hosted Version
```bash
# Using npx (no installation needed)
npx n8n

# Using npm (global installation)
npm install n8n -g
n8n

# Using Docker
docker run -it --rm \
  --name n8n \
  -p 5678:5678 \
  -v ~/.n8n:/home/node/.n8n \
  n8nio/n8n
```

Access N8N at: `http://localhost:5678`

## Importing a Workflow

### Method 1: Import from File
1. Download a workflow JSON file from this repository
2. Open your N8N instance
3. Click **"Workflows"** in the sidebar
4. Click **"Import from File"**
5. Select the downloaded JSON file
6. Click **"Import"**

### Method 2: Import from URL
1. Get the raw URL of a workflow JSON file from GitHub
2. In N8N, go to **Workflows** → **Import from URL**
3. Paste the URL
4. Click **"Import"**

### Method 3: Copy & Paste
1. Open the JSON file in GitHub
2. Copy the entire contents
3. In N8N, click **"Workflows"** → **"Add Workflow"**
4. Click the **"..."** menu → **"Import from Clipboard"**
5. Paste the JSON content

## First Workflow to Try

We recommend starting with the **Scheduled Data Backup** workflow:
- Location: `workflows/utilities/scheduled-data-backup.json`
- Simple to understand
- No external credentials needed initially
- Good introduction to N8N concepts

## Understanding N8N Workflows

### Key Concepts

**Nodes:** Individual steps in your workflow
- **Trigger nodes:** Start the workflow (webhook, schedule, manual)
- **Action nodes:** Perform tasks (HTTP request, database query, API call)
- **Function nodes:** Custom JavaScript code
- **Logic nodes:** IF conditions, switches, merges

**Connections:** Links between nodes that pass data

**Credentials:** Stored authentication for external services

**Executions:** Each time a workflow runs

## Configuring Credentials

Many workflows require credentials for external services:

1. Go to **"Credentials"** in the N8N sidebar
2. Click **"Add Credential"**
3. Select the service type (Slack, GitHub, etc.)
4. Fill in the required information
5. Test and save

## Testing Your Workflow

1. **Manual Testing:**
   - Open the workflow
   - Click **"Execute Workflow"** button
   - Check the output of each node

2. **With Test Data:**
   - Use the "Listen for Event" feature on webhook nodes
   - Send test data to your workflow
   - Verify results

3. **Step-by-Step:**
   - Execute node by node
   - Inspect data between nodes
   - Debug any issues

## Activating a Workflow

Once tested:
1. Toggle the **"Active"** switch in the workflow header
2. For scheduled workflows, verify the next execution time
3. For webhooks, copy the webhook URL for use in external services

## Common Workflows to Explore

1. **Notifications** (`workflows/notifications/`)
   - Great for learning webhook triggers
   - Quick setup with Slack or Discord

2. **Integrations** (`workflows/integrations/`)
   - Connect different services
   - Learn about API integrations

3. **Data Processing** (`workflows/data-processing/`)
   - Transform and manipulate data
   - Practice using Function nodes

4. **Utilities** (`workflows/utilities/`)
   - Scheduled tasks
   - Automation helpers

## Getting Help

- **N8N Documentation:** [docs.n8n.io](https://docs.n8n.io)
- **N8N Community Forum:** [community.n8n.io](https://community.n8n.io)
- **N8N Discord:** Join the community Discord server
- **This Repository:** Check workflow README files for specific help

## Next Steps

1. ✅ Install/access N8N
2. ✅ Import your first workflow
3. ✅ Test it manually
4. ✅ Configure any needed credentials
5. ✅ Activate the workflow
6. ✅ Monitor executions
7. ✅ Customize for your needs

## Tips for Success

- Start simple - don't try to build complex workflows immediately
- Test each node individually before connecting them
- Use the Function node to transform data as needed
- Check execution logs when things don't work as expected
- Save different versions as you experiment
- Read the documentation for nodes you're using

## Contributing Back

Once you're comfortable:
- Modify existing workflows for your needs
- Create new workflows
- Share them back to this repository!

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

---

Happy automating! 🚀
