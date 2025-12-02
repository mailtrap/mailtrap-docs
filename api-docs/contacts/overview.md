---
title: Contacts API
description: Manage email contacts and lists for targeted campaigns
icon: address-book
---

# Contacts API

Manage your email contacts, create targeted lists, and organize your audience for email marketing campaigns.

## Capabilities

| Feature | Description |
|---------|-------------|
| **Contacts** | Create, update, delete, and search contacts |
| **Lists** | Organize contacts into lists for targeted campaigns |
| **Fields** | Define custom fields to store additional contact data |
| **Import/Export** | Bulk import from CSV and export contacts |
| **Events** | Track contact interactions and engagement |

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

- `GET /contacts` - List all contacts
- `POST /contacts` - Create a contact
- `GET /contacts/{id}` - Get a contact
- `PATCH /contacts/{id}` - Update a contact
- `DELETE /contacts/{id}` - Delete a contact
- `GET /contact_lists` - List all contact lists
- `POST /contact_lists` - Create a list
- `GET /contact_fields` - List custom fields
- `POST /contact_fields` - Create a custom field
- `POST /contact_imports` - Import contacts from CSV
- `POST /contact_exports` - Export contacts

{% hint style="info" %}
See the full API reference below for detailed request/response schemas and examples.
{% endhint %}
