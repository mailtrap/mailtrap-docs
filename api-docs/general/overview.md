---
title: General API Overview
description: Manage accounts, users, permissions, and billing
icon: memo-circle-check
---

# Overview

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
      email: 'colleague@company.com'
    })
  }
);
```
{% endstep %}

{% step %}
### Manage Roles

Assign predefined roles:

**Account Owner**
- Full account control
- Billing management
- User management
- Transfer ownership

**Account Admin**
- Same as Owner, except delete account and transfer ownership

**Account Viewer**
- Read-only access to all entities
- View projects, sandboxes, billing
{% endstep %}
{% endstepper %}

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
