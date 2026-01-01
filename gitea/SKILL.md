---
name: gitea
description: Interact with Gitea (self-hosted Git service) using the Gitea API. Use when working with Gitea repositories, issues, pull requests, or API operations.
allowed-tools: Bash, Read, Write, Grep, Glob
---

# Gitea Integration

This skill helps you interact with Gitea, a self-hosted Git service, using its API and CLI tools.

## Prerequisites

Before using Gitea API commands, ensure:
1. Gitea instance URL is known
2. API token is available (can be created in Gitea Settings > Applications > Generate New Token)
3. `curl` or `tea` (Gitea CLI) is installed

## Common Operations

### Repository Management

#### List Repositories
```bash
curl -H "Authorization: token YOUR_TOKEN" \
  https://gitea.example.com/api/v1/user/repos
```

#### Create Repository
```bash
curl -X POST -H "Authorization: token YOUR_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"name":"repo-name","description":"Repo description","private":false}' \
  https://gitea.example.com/api/v1/user/repos
```

#### Get Repository Info
```bash
curl -H "Authorization: token YOUR_TOKEN" \
  https://gitea.example.com/api/v1/repos/OWNER/REPO
```

### Issue Management

#### List Issues
```bash
curl -H "Authorization: token YOUR_TOKEN" \
  https://gitea.example.com/api/v1/repos/OWNER/REPO/issues
```

#### Create Issue
```bash
curl -X POST -H "Authorization: token YOUR_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"title":"Issue title","body":"Issue description"}' \
  https://gitea.example.com/api/v1/repos/OWNER/REPO/issues
```

#### Update Issue
```bash
curl -X PATCH -H "Authorization: token YOUR_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"state":"closed"}' \
  https://gitea.example.com/api/v1/repos/OWNER/REPO/issues/ISSUE_NUMBER
```

### Pull Request Management

#### List Pull Requests
```bash
curl -H "Authorization: token YOUR_TOKEN" \
  https://gitea.example.com/api/v1/repos/OWNER/REPO/pulls
```

#### Create Pull Request
```bash
curl -X POST -H "Authorization: token YOUR_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"title":"PR title","head":"feature-branch","base":"main","body":"PR description"}' \
  https://gitea.example.com/api/v1/repos/OWNER/REPO/pulls
```

#### Merge Pull Request
```bash
curl -X POST -H "Authorization: token YOUR_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"Do":"merge"}' \
  https://gitea.example.com/api/v1/repos/OWNER/REPO/pulls/PR_NUMBER/merge
```

### User and Organization Management

#### Get Current User Info
```bash
curl -H "Authorization: token YOUR_TOKEN" \
  https://gitea.example.com/api/v1/user
```

#### List Organization Repositories
```bash
curl -H "Authorization: token YOUR_TOKEN" \
  https://gitea.example.com/api/v1/orgs/ORG_NAME/repos
```

## Using Gitea CLI (tea)

If the `tea` CLI is available, you can use it for simpler commands:

```bash
# Login
tea login add --url https://gitea.example.com --token YOUR_TOKEN

# List repos
tea repos ls

# Create issue
tea issues create --title "Issue title" --body "Description"

# Create PR
tea pulls create --head feature-branch --base main --title "PR title"

# List PRs
tea pulls ls
```

## Best Practices

1. **Security**: Never hardcode API tokens. Use environment variables or ask the user for credentials.
2. **Error Handling**: Always check API responses for errors before proceeding.
3. **Rate Limiting**: Be mindful of API rate limits on the Gitea instance.
4. **Validation**: Validate repository names, branch names, and other inputs before making API calls.

## Workflow Example

When asked to create a new repository and set it up:

1. Ask user for Gitea instance URL and verify they have an API token
2. Create the repository using the API
3. If requested, initialize with README or other files
4. Set up repository settings (private/public, description, etc.)
5. Provide the repository URL to the user

## Environment Variables

Commonly used environment variables:
- `GITEA_URL`: Base URL of the Gitea instance
- `GITEA_TOKEN`: API token for authentication
- `GITEA_USER`: Username for the Gitea instance

## API Documentation

For complete API reference, refer to:
- Gitea API Swagger docs: `https://your-gitea-instance.com/api/swagger`
- Official docs: https://docs.gitea.com/api/1.20/
