# OpenWebUI with Azure OpenAI and Traefik

This project sets up OpenWebUI with Azure OpenAI integration, secured behind Traefik reverse proxy with SSL certification through Cloudflare DNS.

## Prerequisites

- Docker and Docker Compose installed
- Cloudflare account with DNS API token
- Azure OpenAI subscription
- Azure AD application for SSO

## Project Structure
```
.
├── .env
├── docker-compose.yml
├── litellm_config.yaml
└── letsencrypt/
└── acme.json
```
## Configuration

### Environment Variables

Create a `.env` file with the following configurations:

```env
# Cloudflare Settings
CLOUDFLARE_EMAIL=your-email
CLOUDFLARE_DNS_API_TOKEN=your-token

# Azure OpenAI Settings
AZURE_API_KEY=your-api-key
AZURE_API_BASE=your-api-base
AZURE_API_VERSION=your-api-version

# Domain Settings
DOMAIN=your-domain
OPENWEBUI_SUBDOMAIN=your-subdomain

# OpenWebUI SSO Settings
AZURE_AD_CLIENT_ID=your-client-id
AZURE_AD_CLIENT_SECRET=your-client-secret
AZURE_AD_TENANT_ID=your-tenant-id

# Setup data path
DATA_PATH=your-data-path
```
## Services

## Traefik Reverse Proxy

- Handles SSL termination
- Automatic certificate management via Cloudflare DNS
- Secure HTTPS routing

## OpenWebUI
- Web interface for AI interaction
- Azure AD SSO integration
- Persistent data storage

## LiteLLM Proxy
- Model management interface
- Supports multiple Azure OpenAI models:
 - GPT-4o-mini
 - GPT-4o
 - DALL-E 3

## Setup Instructions
1. Create the letsencrypt directory:
```
mkdir letsencrypt
touch letsencrypt/acme.json
chmod 600 letsencrypt/acme.json
```

2. Start the services:
```
docker-compose up -d
```

## Security Features
- SSL/TLS encryption via Cloudflare
- Azure AD Single Sign-On
- Secure API key management
- Rate limiting for DALL-E 3
