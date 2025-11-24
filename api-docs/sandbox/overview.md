---
title: Email Sandbox Overview
description: Test email sending in a safe environment before going to production
---

# Email Sandbox Overview

Mailtrap Email Sandbox provides a safe testing environment for email development. Capture and inspect emails without sending them to real recipients, perfect for development, staging, and QA environments.

## Why Use Email Sandbox?

{% columns %}
{% column %}
### Safe Testing
Test email functionality without risk of sending to real recipients or affecting email reputation.
{% endcolumn %}

{% column %}
### Email Inspection
View HTML/text content, headers, attachments, and spam scores for every test email.
{% endcolumn %}

{% column %}
### Team Collaboration
Share test inboxes with your team for collaborative testing and debugging.
{% endcolumn %}
{% endcolumns %}

## Getting Started

{% stepper %}
{% step %}
### Create a Project

Projects organize your test inboxes by application or environment.

```javascript
// Using Mailtrap API
const response = await fetch('https://mailtrap.io/api/accounts/{account_id}/projects', {
  method: 'POST',
  headers: {
    'Api-Token': 'YOUR_API_TOKEN',
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({
    project: { name: 'My App Development' }
  })
});
```
{% endstep %}

{% step %}
### Create Test Inboxes

Each project can have multiple inboxes for different environments or features.

```javascript
// Create an inbox for staging environment
const inbox = await createInbox(projectId, {
  name: 'Staging Environment'
});
```
{% endstep %}

{% step %}
### Configure Your Application

Update your application to send emails to the sandbox:

{% tabs %}
{% tab title="Node.js" %}
```javascript
import { MailtrapClient } from "mailtrap";

const client = new MailtrapClient({
  token: process.env.MAILTRAP_API_KEY,
  sandbox: true,
  testInboxId: 123456 // Your inbox ID
});

// Emails will be captured in sandbox
await client.send({
  from: { email: "test@example.com" },
  to: [{ email: "user@example.com" }],
  subject: "Test Email",
  text: "This will be captured in sandbox"
});
```
{% endtab %}

{% tab title="Python" %}
```python
import mailtrap as mt

client = mt.MailtrapClient(
    token="YOUR_API_KEY",
    sandbox=True,
    inbox_id=123456
)

mail = mt.Mail(
    sender=mt.Address(email="test@example.com"),
    to=[mt.Address(email="user@example.com")],
    subject="Test Email",
    text="This will be captured in sandbox"
)

client.send(mail)
```
{% endtab %}

{% tab title="SMTP" %}
```yaml
# SMTP Configuration
Host: sandbox.smtp.mailtrap.io
Port: 2525 (or 25, 465, 587)
Username: <inbox_username>
Password: <inbox_password>
TLS/STARTTLS: Optional
```
{% endtab %}
{% endtabs %}
{% endstep %}

{% step %}
### Inspect Test Emails

View captured emails in the Mailtrap dashboard or via API:

```javascript
// Get messages from inbox
const messages = await fetch(
  'https://mailtrap.io/api/accounts/{account_id}/inboxes/{inbox_id}/messages'
);

// Get specific message details
const message = await fetch(
  'https://mailtrap.io/api/accounts/{account_id}/inboxes/{inbox_id}/messages/{message_id}'
);
```
{% endstep %}
{% endstepper %}

## Key Features

### Email Analysis

{% tabs %}
{% tab title="Content" %}
**HTML & Text Preview**
- Desktop and mobile preview
- Raw HTML source code
- Plain text version
- Dark mode testing
{% endtab %}

{% tab title="Spam Check" %}
**Spam Score Analysis**
- SpamAssassin score
- Detailed spam report
- Blacklist checking
- Content analysis
{% endtab %}

{% tab title="Headers" %}
**Email Headers**
- Full header inspection
- DKIM/SPF validation
- Authentication results
- Routing information
{% endtab %}

{% tab title="Attachments" %}
**Attachment Handling**
- View all attachments
- Download files
- Inline image preview
- Size validation
{% endtab %}
{% endtabs %}

### API Capabilities

The Sandbox API allows you to:

- **Projects**: Create, update, delete projects
- **Inboxes**: Manage test inboxes
- **Messages**: Read, delete, forward test emails
- **Attachments**: Download email attachments
- **Automation**: Integrate with CI/CD pipelines

## Testing Workflows

### Development Environment

```javascript
// Development configuration
if (process.env.NODE_ENV === 'development') {
  emailConfig = {
    host: 'sandbox.smtp.mailtrap.io',
    port: 2525,
    auth: {
      user: process.env.MAILTRAP_INBOX_USER,
      pass: process.env.MAILTRAP_INBOX_PASS
    }
  };
}
```

### Automated Testing

```javascript
// Jest test example
describe('Email Notifications', () => {
  it('should send welcome email', async () => {
    // Send email
    await sendWelcomeEmail(user);

    // Check inbox via API
    const messages = await getInboxMessages();
    const welcomeEmail = messages.find(
      m => m.subject === 'Welcome!'
    );

    expect(welcomeEmail).toBeDefined();
    expect(welcomeEmail.to_email).toBe(user.email);
  });
});
```

### CI/CD Integration

```yaml
# GitHub Actions example
- name: Run Email Tests
  env:
    MAILTRAP_API_TOKEN: ${{ secrets.MAILTRAP_TOKEN }}
    MAILTRAP_INBOX_ID: ${{ secrets.MAILTRAP_INBOX }}
  run: |
    npm test -- --testPathPattern=email
```

## Inbox Management

### Clean Inbox Automatically

```javascript
// Clean inbox before tests
async function cleanInbox(inboxId) {
  await fetch(
    `/api/accounts/${accountId}/inboxes/${inboxId}/clean`,
    { method: 'PATCH' }
  );
}
```

### Forward Test Emails

```javascript
// Forward email for manual review
async function forwardEmail(messageId, to) {
  await fetch(
    `/api/accounts/${accountId}/inboxes/${inboxId}/messages/${messageId}/forward`,
    {
      method: 'POST',
      body: JSON.stringify({ to })
    }
  );
}
```

## SMTP vs API

{% columns %}
{% column %}
### SMTP Integration
**Best for:**
- Legacy applications
- Third-party services
- No code changes
- Standard email clients

**Configuration:**
- Host: sandbox.smtp.mailtrap.io
- Ports: 25, 465, 587, 2525
- Authentication: Required
{% endcolumn %}

{% column %}
### API Integration
**Best for:**
- Modern applications
- Full control
- Automated testing
- Advanced features

**Benefits:**
- Faster delivery
- Better error handling
- Rich metadata
{% endcolumn %}
{% endcolumns %}

## Best Practices

{% hint style="success" %}
**Environment Separation**: Use different inboxes for dev, staging, and QA environments.
{% endhint %}

{% hint style="info" %}
**Automated Cleanup**: Regularly clean test inboxes to maintain performance.
{% endhint %}

{% hint style="warning" %}
**Security**: Never use production API keys in sandbox environment.
{% endhint %}

## Limitations

- **Message Retention**: Messages older than 7 days are automatically deleted
- **Inbox Size**: Maximum 300 messages per inbox
- **Attachment Size**: Maximum 25 MB per email
- **Rate Limits**: 100 emails per second per inbox

## Troubleshooting

{% expand title="Emails not appearing in inbox" %}
- Verify SMTP/API credentials
- Check inbox ID is correct
- Ensure sandbox mode is enabled
- Verify network connectivity
{% endexpand %}

{% expand title="Authentication failed" %}
- Check API token has correct permissions
- Verify inbox credentials for SMTP
- Ensure account is active
{% endexpand %}

{% expand title="Attachment issues" %}
- Check file size (max 25 MB)
- Verify MIME types are correct
- Ensure base64 encoding for API
{% endexpand %}

## Next Steps

{% hint style="success" %}
Ready to start testing? Explore the full API reference below to integrate Email Sandbox into your development workflow.
{% endhint %}