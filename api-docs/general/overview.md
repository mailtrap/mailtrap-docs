---
title: General API
description: Manage accounts, users, permissions, and billing
icon: memo-circle-check
---

# General API

Manage your Mailtrap account, users, permissions, and billing settings.

## Capabilities

| Feature | Description |
|---------|-------------|
| **Accounts** | Get account information and settings |
| **Users** | Invite, manage, and remove team members |
| **Permissions** | Control access levels and roles |

## Base URL

```
https://mailtrap.io/api/accounts/{account_id}
```

## Authentication

Include your API token in the request header:

```
Api-Token: YOUR_API_TOKEN
```

Or use Bearer authentication:

```
Authorization: Bearer YOUR_API_TOKEN
```

## Available Endpoints

- `GET /accounts` - List all accounts
- `GET /accounts/{id}` - Get account details
- `GET /account_accesses` - List user accesses
- `DELETE /account_accesses/{id}` - Remove user access
- `GET /permissions` - List available permissions

{% hint style="info" %}
See the full API reference below for detailed request/response schemas and examples.
{% endhint %}
