# Contributing to N8N Workflows

Thank you for your interest in contributing to this repository! We appreciate your help in building a comprehensive collection of N8N workflow templates.

## 📝 How to Contribute

### Adding a New Workflow

1. **Fork the repository** and create a new branch for your workflow
2. **Export your workflow** from N8N as a JSON file
3. **Choose the appropriate category** or create a new one if needed
4. **Name your file** descriptively: `workflow-name.json`
5. **Add documentation** - Create a README.md in the workflow directory if needed

### Workflow Guidelines

#### Before Submitting

- ✅ Test your workflow thoroughly
- ✅ Remove any sensitive credentials or personal information
- ✅ Ensure the workflow uses generic placeholder values
- ✅ Add clear node names and descriptions
- ✅ Include error handling where appropriate

#### Workflow Documentation

Each workflow should include:

- **Clear description** of what the workflow does
- **Required credentials** (e.g., API keys, OAuth apps)
- **Setup instructions** for any special configuration
- **Example use cases**
- **Any prerequisites or dependencies**

#### Example README Template

```markdown
# Workflow Name

## Description
Brief description of what this workflow does.

## Features
- Feature 1
- Feature 2
- Feature 3

## Prerequisites
- List any required services
- List any required credentials
- Any other setup requirements

## Setup Instructions
1. Step-by-step setup guide
2. Configuration details
3. Testing instructions

## Trigger
Describe how the workflow is triggered

## Nodes Used
- Node 1
- Node 2
- Node 3

## Configuration
Explain any configuration options

## Notes
Any additional information or tips
```

### Pull Request Process

1. Update the main README.md if you're adding a new category
2. Ensure your workflow file is valid JSON
3. Provide a clear description of your workflow in the PR
4. Link to any related issues or discussions

## 🎯 Workflow Categories

Current categories:
- **data-processing** - Data transformation and processing workflows
- **notifications** - Alert and notification workflows
- **integrations** - Third-party service integrations
- **utilities** - General-purpose utilities

If your workflow doesn't fit existing categories, propose a new one!

## ✅ Code of Conduct

- Be respectful and constructive
- Help others learn and grow
- Share knowledge and best practices
- Keep workflows well-documented

## 🐛 Reporting Issues

If you find issues with existing workflows:
1. Check if the issue already exists
2. Provide detailed information about the problem
3. Include N8N version and environment details
4. Share steps to reproduce the issue

## 💡 Suggestions

Have ideas for improving the repository structure or documentation? Open an issue to discuss!

## 📧 Questions

If you have questions, feel free to:
- Open an issue
- Start a discussion
- Check existing documentation

Thank you for contributing! 🎉
