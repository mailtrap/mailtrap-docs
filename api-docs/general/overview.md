---
title: General API Overview
description: Manage accounts, users, permissions, and billing
icon: cog
---

# General API Overview

The General API provides endpoints for managing your Mailtrap account, including user management, permissions, billing, and account settings. Control access, monitor usage, and manage your organization's email infrastructure.

## Account Management

### Account Structure

{% columns %}
{% column %}
### Organization
Top-level entity that contains all resources and billing.
{% endcolumn %}

{% column %}
### Users
Team members with specific roles and permissions.
{% endcolumn %}

{% column %}
### API Tokens
Programmatic access with scoped permissions.
{% endcolumn %}
{% endcolumns %}

## User Management

{% stepper %}
{% step %}
### Invite Team Members

Add users to your organization:

```javascript
const response = await fetch(
  'https://mailtrap.io/api/accounts/{account_id}/users',
  {
    method: 'POST',
    headers: {
      'Api-Token': 'YOUR_API_TOKEN',
      'Content-Type': 'application/json'
    },
    body: JSON.stringify({
      email: 'colleague@company.com',
      role: 'developer',
      permissions: ['send_emails', 'view_analytics']
    })
  }
);
```
{% endstep %}

{% step %}
### Manage Roles

Assign predefined roles or custom permissions:

{% tabs %}
{% tab title="Predefined Roles" %}
**Owner**
- Full account control
- Billing management
- User management

**Admin**
- Manage projects and domains
- Create API tokens
- View analytics

**Developer**
- Send emails
- Manage templates
- Access sandbox

**Viewer**
- Read-only access
- View analytics
- Export reports
{% endtab %}

{% tab title="Custom Permissions" %}
```javascript
const customRole = {
  name: 'Marketing Manager',
  permissions: [
    'send_emails',
    'manage_templates',
    'view_analytics',
    'manage_contacts',
    'export_data'
  ]
};
```
{% endtab %}
{% endtabs %}
{% endstep %}

{% step %}
### Set User Permissions

Update user access levels:

```javascript
await fetch(
  `https://mailtrap.io/api/accounts/{account_id}/users/${userId}`,
  {
    method: 'PATCH',
    headers: {
      'Api-Token': 'YOUR_API_TOKEN',
      'Content-Type': 'application/json'
    },
    body: JSON.stringify({
      role: 'admin',
      permissions: {
        projects: ['create', 'read', 'update', 'delete'],
        domains: ['create', 'read'],
        billing: ['read']
      }
    })
  }
);
```
{% endstep %}
{% endstepper %}

## Permission System

### Permission Scopes

| Scope | Description | Operations |
|-------|-------------|------------|
| `account` | Account settings | View, update account info |
| `users` | User management | Invite, remove, update users |
| `billing` | Billing access | View invoices, update payment |
| `projects` | Project management | Create, update, delete projects |
| `domains` | Domain management | Add, verify, remove domains |
| `emails` | Email sending | Send transactional/bulk emails |
| `templates` | Template management | Create, edit, delete templates |
| `analytics` | Analytics access | View stats and reports |
| `sandbox` | Sandbox access | Manage test inboxes |
| `webhooks` | Webhook management | Configure webhooks |

### API Token Management

Create tokens with specific scopes:

```javascript
// Create API token
const response = await fetch(
  'https://mailtrap.io/api/accounts/{account_id}/api_tokens',
  {
    method: 'POST',
    headers: {
      'Api-Token': 'YOUR_API_TOKEN',
      'Content-Type': 'application/json'
    },
    body: JSON.stringify({
      name: 'Production API',
      scopes: ['emails:send', 'templates:read', 'analytics:read'],
      expires_at: '2025-12-31'
    })
  }
);

const { token } = await response.json();
```

## Account Access

### List Account Accesses

View all users and their access levels:

```javascript
const response = await fetch(
  'https://mailtrap.io/api/accounts/{account_id}/account_accesses',
  {
    headers: { 'Api-Token': 'YOUR_API_TOKEN' }
  }
);

const accesses = await response.json();
// Returns array of user access objects
```

### Revoke Access

Remove user from account:

```javascript
await fetch(
  `https://mailtrap.io/api/accounts/{account_id}/account_accesses/${accessId}`,
  {
    method: 'DELETE',
    headers: { 'Api-Token': 'YOUR_API_TOKEN' }
  }
);
```

## Billing Management

### Get Current Plan

```javascript
const response = await fetch(
  'https://mailtrap.io/api/accounts/{account_id}/billing',
  {
    headers: { 'Api-Token': 'YOUR_API_TOKEN' }
  }
);

const billing = await response.json();
// {
//   plan: 'Business',
//   emails_sent: 45000,
//   emails_limit: 100000,
//   billing_cycle: 'monthly',
//   next_billing_date: '2024-02-01'
// }
```

### Usage Statistics

Monitor email usage and limits:

```javascript
const usage = await fetch(
  'https://mailtrap.io/api/accounts/{account_id}/billing/usage',
  {
    headers: { 'Api-Token': 'YOUR_API_TOKEN' }
  }
);

// Returns current month usage
{
  "transactional_sent": 25000,
  "bulk_sent": 20000,
  "total_sent": 45000,
  "limit": 100000,
  "percentage_used": 45
}
```

### Billing History

```javascript
const invoices = await fetch(
  'https://mailtrap.io/api/accounts/{account_id}/billing/invoices',
  {
    headers: { 'Api-Token': 'YOUR_API_TOKEN' }
  }
);

// List of invoice objects
[
  {
    "id": "INV-2024-001",
    "date": "2024-01-01",
    "amount": 99.00,
    "status": "paid",
    "download_url": "https://..."
  }
]
```

## Account Settings

### Update Account Information

```javascript
await fetch(
  'https://mailtrap.io/api/accounts/{account_id}',
  {
    method: 'PATCH',
    headers: {
      'Api-Token': 'YOUR_API_TOKEN',
      'Content-Type': 'application/json'
    },
    body: JSON.stringify({
      name: 'Updated Company Name',
      timezone: 'America/New_York',
      notification_email: 'alerts@company.com'
    })
  }
);
```

### Configure Notifications

Set up account-level notifications:

```javascript
await fetch(
  'https://mailtrap.io/api/accounts/{account_id}/notifications',
  {
    method: 'PUT',
    headers: {
      'Api-Token': 'YOUR_API_TOKEN',
      'Content-Type': 'application/json'
    },
    body: JSON.stringify({
      low_credits: true,
      weekly_report: true,
      bounce_alerts: true,
      threshold_percentage: 80
    })
  }
);
```

## Security Settings

### Two-Factor Authentication

Enforce 2FA for all users:

```javascript
await fetch(
  'https://mailtrap.io/api/accounts/{account_id}/security',
  {
    method: 'PUT',
    headers: {
      'Api-Token': 'YOUR_API_TOKEN',
      'Content-Type': 'application/json'
    },
    body: JSON.stringify({
      require_2fa: true,
      ip_whitelist: ['192.168.1.0/24'],
      password_policy: {
        min_length: 12,
        require_special: true,
        require_numbers: true
      }
    })
  }
);
```

### Audit Logs

Review account activity:

```javascript
const logs = await fetch(
  'https://mailtrap.io/api/accounts/{account_id}/audit_logs',
  {
    headers: { 'Api-Token': 'YOUR_API_TOKEN' }
  }
);

// Returns audit log entries
[
  {
    "timestamp": "2024-01-15T10:30:00Z",
    "user": "admin@company.com",
    "action": "domain.verified",
    "resource": "example.com",
    "ip_address": "192.168.1.100"
  }
]
```

## Team Collaboration

### Projects & Permissions

Organize resources by project:

```javascript
// Create project with team access
const project = await fetch(
  'https://mailtrap.io/api/accounts/{account_id}/projects',
  {
    method: 'POST',
    headers: {
      'Api-Token': 'YOUR_API_TOKEN',
      'Content-Type': 'application/json'
    },
    body: JSON.stringify({
      name: 'Marketing Campaigns',
      team_members: [
        { user_id: 1, role: 'manager' },
        { user_id: 2, role: 'contributor' }
      ]
    })
  }
);
```

### Resource Sharing

Share specific resources with team members:

```javascript
// Share template with team
await fetch(
  `https://mailtrap.io/api/accounts/{account_id}/templates/${templateId}/share`,
  {
    method: 'POST',
    headers: {
      'Api-Token': 'YOUR_API_TOKEN',
      'Content-Type': 'application/json'
    },
    body: JSON.stringify({
      user_ids: [userId1, userId2],
      permission: 'read'
    })
  }
);
```

## API Rate Limits

### Check Rate Limit Status

```javascript
// Rate limit info in response headers
const response = await fetch('https://mailtrap.io/api/...');

console.log({
  limit: response.headers.get('X-RateLimit-Limit'),
  remaining: response.headers.get('X-RateLimit-Remaining'),
  reset: response.headers.get('X-RateLimit-Reset')
});
```

### Rate Limit Tiers

| Plan | Requests/Second | Requests/Hour |
|------|----------------|---------------|
| Free | 1 | 100 |
| Starter | 10 | 1,000 |
| Business | 50 | 10,000 |
| Enterprise | 100+ | Custom |

## Integrations

### SSO Configuration

Set up Single Sign-On:

```javascript
await fetch(
  'https://mailtrap.io/api/accounts/{account_id}/sso',
  {
    method: 'POST',
    headers: {
      'Api-Token': 'YOUR_API_TOKEN',
      'Content-Type': 'application/json'
    },
    body: JSON.stringify({
      provider: 'okta',
      metadata_url: 'https://company.okta.com/metadata',
      default_role: 'developer'
    })
  }
);
```

## Best Practices

{% hint style="success" %}
**Least Privilege**: Grant users only the permissions they need.
{% endhint %}

{% hint style="info" %}
**API Token Rotation**: Regularly rotate API tokens for security.
{% endhint %}

{% hint style="warning" %}
**Audit Regularly**: Review audit logs monthly for unusual activity.
{% endhint %}

## Troubleshooting

{% expand title="Permission denied errors" %}
- Verify API token has required scopes
- Check user role permissions
- Ensure resource ownership
{% endexpand %}

{% expand title="Rate limit exceeded" %}
- Implement exponential backoff
- Cache responses when possible
- Consider upgrading plan
{% endexpand %}

{% expand title="Billing issues" %}
- Check payment method validity
- Review usage vs. plan limits
- Contact support for adjustments
{% endexpand %}

## Next Steps

{% hint style="success" %}
Configure your account settings and manage your team effectively. Check the API reference below for detailed endpoints.
{% endhint %}