---
title: Email Sandbox API Overview
description: Test email sending in a safe environment before going to production
icon: memo-circle-check
---

# Overview

Mailtrap Email Sandbox provides a safe testing environment for email development. Capture and inspect emails without sending them to real recipients, perfect for development, staging, and QA environments.

## Get Your Sandbox ID

To use the Sandbox API, you need your Sandbox (Inbox) ID. There are two ways to get it:

### From the URL

Navigate to your Sandbox inbox in [Mailtrap](https://mailtrap.io/inboxes) and get the ID from the URL:

```
https://mailtrap.io/inboxes/2564102/messages
                         ↑
                   Sandbox ID: 2564102
```

### Via API

Use the API to get a list of your Sandboxes:

```bash
curl -X GET "https://mailtrap.io/api/accounts/{account_id}/inboxes" \
  -H "Api-Token: YOUR_API_TOKEN"
```

The response will include all your inboxes with their IDs:

```json
[
  {
    "id": 2564102,
    "name": "My Test Inbox",
    "username": "abc123",
    "password": "xyz789",
    ...
  }
]
```

{% hint style="info" %}
Use the `id` field from the response as your Sandbox ID when making API calls.
{% endhint %}
