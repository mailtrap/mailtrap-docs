---
title: Contacts API Overview
description: Manage email contacts and lists for targeted campaigns
icon: address-book
---

# Contacts API Overview

The Contacts API enables you to manage email contacts, create targeted lists, and organize your audience for email marketing campaigns. Build and maintain your subscriber base with powerful segmentation and field management.

## Key Features

{% columns %}
{% column %}
### Contact Management
Import, update, and organize contacts with custom fields and tags.
{% endcolumn %}

{% column %}
### List Segmentation
Create targeted lists based on contact properties and behaviors.
{% endcolumn %}

{% column %}
### Import & Export
Bulk import contacts from CSV/Excel and export for analysis.
{% endcolumn %}
{% endcolumns %}

## Getting Started

{% stepper %}
{% step %}
### Create Custom Fields

Define custom fields to store additional contact information:

```javascript
const response = await fetch(
  'https://mailtrap.io/api/accounts/{account_id}/contact_fields',
  {
    method: 'POST',
    headers: {
      'Api-Token': 'YOUR_API_TOKEN',
      'Content-Type': 'application/json'
    },
    body: JSON.stringify({
      name: 'company_size',
      type: 'select',
      options: ['1-10', '11-50', '51-200', '200+']
    })
  }
);
```
{% endstep %}

{% step %}
### Import Contacts

Bulk import contacts from CSV or add individually:

{% tabs %}
{% tab title="Bulk Import" %}
```javascript
// Import from CSV
const formData = new FormData();
formData.append('file', csvFile);
formData.append('list_id', listId);
formData.append('update_existing', true);

const response = await fetch(
  'https://mailtrap.io/api/accounts/{account_id}/contact_imports',
  {
    method: 'POST',
    headers: { 'Api-Token': 'YOUR_API_TOKEN' },
    body: formData
  }
);
```
{% endtab %}

{% tab title="Add Individual" %}
```javascript
// Add single contact
const response = await fetch(
  'https://mailtrap.io/api/accounts/{account_id}/contacts',
  {
    method: 'POST',
    headers: {
      'Api-Token': 'YOUR_API_TOKEN',
      'Content-Type': 'application/json'
    },
    body: JSON.stringify({
      email: 'john@example.com',
      fields: {
        first_name: 'John',
        last_name: 'Doe',
        company: 'Acme Corp',
        company_size: '51-200'
      }
    })
  }
);
```
{% endtab %}
{% endtabs %}
{% endstep %}

{% step %}
### Create Contact Lists

Organize contacts into lists for targeted campaigns:

```javascript
const response = await fetch(
  'https://mailtrap.io/api/accounts/{account_id}/contact_lists',
  {
    method: 'POST',
    headers: {
      'Api-Token': 'YOUR_API_TOKEN',
      'Content-Type': 'application/json'
    },
    body: JSON.stringify({
      name: 'Newsletter Subscribers',
      description: 'Users who opted in for weekly newsletter'
    })
  }
);

const list = await response.json();
```
{% endstep %}

{% step %}
### Add Contacts to Lists

Assign contacts to specific lists:

```javascript
// Add multiple contacts to a list
await fetch(
  `https://mailtrap.io/api/accounts/{account_id}/contact_lists/${listId}/contacts`,
  {
    method: 'POST',
    headers: {
      'Api-Token': 'YOUR_API_TOKEN',
      'Content-Type': 'application/json'
    },
    body: JSON.stringify({
      contact_ids: [contactId1, contactId2, contactId3]
    })
  }
);
```
{% endstep %}
{% endstepper %}

## Contact Fields

### Default Fields

Every contact has these built-in fields:

| Field | Type | Description |
|-------|------|-------------|
| `email` | Email | Primary email address (required) |
| `first_name` | Text | Contact's first name |
| `last_name` | Text | Contact's last name |
| `created_at` | DateTime | When contact was added |
| `updated_at` | DateTime | Last modification time |
| `subscribed` | Boolean | Email subscription status |

### Custom Field Types

Create custom fields to match your needs:

{% tabs %}
{% tab title="Text Fields" %}
```javascript
{
  name: 'job_title',
  type: 'text',
  required: false
}
```
{% endtab %}

{% tab title="Number Fields" %}
```javascript
{
  name: 'age',
  type: 'number',
  min: 18,
  max: 120
}
```
{% endtab %}

{% tab title="Select Fields" %}
```javascript
{
  name: 'plan',
  type: 'select',
  options: ['Free', 'Basic', 'Pro', 'Enterprise'],
  default: 'Free'
}
```
{% endtab %}

{% tab title="Date Fields" %}
```javascript
{
  name: 'signup_date',
  type: 'date',
  format: 'YYYY-MM-DD'
}
```
{% endtab %}

{% tab title="Boolean Fields" %}
```javascript
{
  name: 'is_verified',
  type: 'boolean',
  default: false
}
```
{% endtab %}
{% endtabs %}

## List Management

### Dynamic Segmentation

Create smart lists that update automatically based on criteria:

```javascript
// Contacts from specific companies
const enterpriseList = await createSmartList({
  name: 'Enterprise Customers',
  criteria: {
    company_size: '200+',
    plan: 'Enterprise',
    subscribed: true
  }
});
```

### List Operations

```javascript
// Get all lists
const lists = await fetch(
  'https://mailtrap.io/api/accounts/{account_id}/contact_lists'
);

// Get contacts in a list
const contacts = await fetch(
  `https://mailtrap.io/api/accounts/{account_id}/contact_lists/${listId}/contacts`
);

// Remove contact from list
await fetch(
  `https://mailtrap.io/api/accounts/{account_id}/contact_lists/${listId}/contacts/${contactId}`,
  { method: 'DELETE' }
);
```

## Import & Export

### CSV Import Format

```csv
email,first_name,last_name,company,tags
john@example.com,John,Doe,Acme Corp,"customer,premium"
jane@example.com,Jane,Smith,Tech Inc,"lead,trial"
```

### Import Options

```javascript
const importOptions = {
  file: csvFile,
  list_id: targetListId,
  update_existing: true,       // Update if email exists
  skip_invalid: false,         // Stop on invalid data
  field_mapping: {
    'Email Address': 'email',  // Map CSV columns
    'First': 'first_name',
    'Company Name': 'company'
  }
};
```

### Export Contacts

```javascript
// Export all contacts
const response = await fetch(
  'https://mailtrap.io/api/accounts/{account_id}/contact_exports',
  {
    method: 'POST',
    headers: {
      'Api-Token': 'YOUR_API_TOKEN',
      'Content-Type': 'application/json'
    },
    body: JSON.stringify({
      format: 'csv',
      list_id: listId,  // Optional: specific list
      fields: ['email', 'first_name', 'company']
    })
  }
);

// Check export status
const status = await fetch(
  `https://mailtrap.io/api/accounts/{account_id}/contact_exports/${exportId}`
);
```

## Contact Events

Track contact interactions and engagement:

```javascript
// Get contact events
const events = await fetch(
  `https://mailtrap.io/api/accounts/{account_id}/contacts/${contactId}/events`
);

// Event types:
// - subscribed
// - unsubscribed
// - email_sent
// - email_opened
// - email_clicked
// - email_bounced
```

## Subscription Management

### Handle Unsubscribes

```javascript
// Unsubscribe contact
await fetch(
  `https://mailtrap.io/api/accounts/{account_id}/contacts/${contactId}/unsubscribe`,
  {
    method: 'POST',
    headers: { 'Api-Token': 'YOUR_API_TOKEN' }
  }
);
```

### Resubscribe Process

```javascript
// Resubscribe (requires double opt-in)
await fetch(
  `https://mailtrap.io/api/accounts/{account_id}/contacts/${contactId}/resubscribe`,
  {
    method: 'POST',
    headers: { 'Api-Token': 'YOUR_API_TOKEN' },
    body: JSON.stringify({
      send_confirmation: true
    })
  }
);
```

## Search & Filter

### Search Contacts

```javascript
// Search by email or name
const results = await fetch(
  'https://mailtrap.io/api/accounts/{account_id}/contacts?q=john'
);

// Filter by field values
const filtered = await fetch(
  'https://mailtrap.io/api/accounts/{account_id}/contacts?company=Acme&subscribed=true'
);

// Pagination
const page2 = await fetch(
  'https://mailtrap.io/api/accounts/{account_id}/contacts?page=2&per_page=50'
);
```

## Bulk Operations

### Update Multiple Contacts

```javascript
// Batch update
await fetch(
  'https://mailtrap.io/api/accounts/{account_id}/contacts/batch',
  {
    method: 'PATCH',
    headers: {
      'Api-Token': 'YOUR_API_TOKEN',
      'Content-Type': 'application/json'
    },
    body: JSON.stringify({
      contact_ids: [id1, id2, id3],
      fields: {
        plan: 'Premium',
        renewal_date: '2025-01-01'
      }
    })
  }
);
```

### Bulk Delete

```javascript
// Delete multiple contacts
await fetch(
  'https://mailtrap.io/api/accounts/{account_id}/contacts/batch',
  {
    method: 'DELETE',
    headers: {
      'Api-Token': 'YOUR_API_TOKEN',
      'Content-Type': 'application/json'
    },
    body: JSON.stringify({
      contact_ids: [id1, id2, id3]
    })
  }
);
```

## GDPR Compliance

### Data Export

Export all data for a specific contact:

```javascript
const gdprExport = await fetch(
  `https://mailtrap.io/api/accounts/{account_id}/contacts/${contactId}/export`,
  {
    headers: { 'Api-Token': 'YOUR_API_TOKEN' }
  }
);

// Returns all contact data, events, and history
```

### Right to Deletion

Permanently delete contact and all associated data:

```javascript
await fetch(
  `https://mailtrap.io/api/accounts/{account_id}/contacts/${contactId}/gdpr_delete`,
  {
    method: 'DELETE',
    headers: { 'Api-Token': 'YOUR_API_TOKEN' }
  }
);
```

## Best Practices

{% hint style="success" %}
**Data Quality**: Validate email addresses before import to maintain list health.
{% endhint %}

{% hint style="info" %}
**Consent**: Always obtain explicit consent before adding contacts to marketing lists.
{% endhint %}

{% hint style="warning" %}
**Rate Limits**: Bulk operations are limited to 1000 contacts per request.
{% endhint %}

## Integration Examples

### Signup Form

```javascript
// Handle form submission
async function handleSignup(formData) {
  // Add to contacts
  const contact = await createContact({
    email: formData.email,
    fields: {
      first_name: formData.firstName,
      source: 'website_signup'
    }
  });

  // Add to newsletter list
  await addToList(contact.id, 'newsletter');

  // Send welcome email
  await sendTemplate('welcome_email', contact.email);
}
```

### CRM Sync

```javascript
// Sync with external CRM
async function syncWithCRM() {
  // Get updated contacts from CRM
  const crmContacts = await fetchFromCRM();

  // Bulk import to Mailtrap
  const importId = await importContacts(crmContacts);

  // Wait for import completion
  await waitForImport(importId);

  // Update CRM with Mailtrap IDs
  await updateCRMMapping();
}
```

## Next Steps

{% hint style="success" %}
Ready to build your contact database? Explore the API reference below for detailed endpoints and advanced features.
{% endhint %}