---
title: Email Sandbox Overview
description: >-
  Test and preview emails safely in a sandbox environment before sending to
  production
---

# Overview

Email Sandbox is a safe testing environment that captures all your test emails, preventing them from reaching real inboxes. Perfect for development, QA testing, and staging environments, it ensures your email functionality works flawlessly before going live.

## What is Email Sandbox?

Email Sandbox acts as a **fake SMTP** server that traps all emails sent from your application. Instead of delivering to actual recipients, emails are captured in a secure inbox where you can:

* Preview how emails look across different clients
* Test email workflows without risk
* Validate HTML rendering and responsiveness
* Debug email issues before production
* Share test results with your team

## Key Features

### Safe Testing Environment

* **Zero Risk**: Emails never reach real recipients
* **Multiple Sandboxes**: Separate environments for different projects
* **Email Address per Sandbox**: Unique inbound email addresses for each sandbox
* **Team Collaboration**: Share sandboxes with team members

### Email Analysis Tools

* **HTML/Text Preview**: See exactly how emails render
* **Spam Score Analysis**: Predict spam filter behavior
* **Email Headers**: Inspect all technical details
* **Attachment Support**: Test file attachments

### Advanced Testing

* **Bounce Emulation**: Test bounce handling
* **API & SDKs**: Full programmatic access with official SDKs

### Collaboration Features

* **Shared Sandboxes**: Team-wide access
* **Email Forwarding**: Share specific test cases
* **Access Control**: Manage permissions

## Use Cases

### Development Testing

Perfect for developers building email features:

* Test email templates during development
* Verify dynamic content and personalization
* Debug email sending logic
* Test different email scenarios
* Validate email formatting

### QA & Staging

Essential for quality assurance:

* End-to-end workflow testing
* Cross-client compatibility checks
* Regression testing
* Performance testing
* User acceptance testing

### Email Design

Ideal for designers and marketers:

* Preview email designs
* Test responsive layouts
* Check image rendering
* Validate link tracking
* Review content formatting

## How It Works

### 1. Simple Integration

Choose your integration method:

**SMTP Configuration:**

```
Host: sandbox.smtp.mailtrap.io
Port: 2525
Username: YOUR_SANDBOX_USERNAME
Password: YOUR_SANDBOX_PASSWORD
```

**Unique Email Addresses:** Each sandbox provides unique @mailtrap.io addresses for inbound testing.

### 2. Send & Receive Test Emails

* **Outbound**: Your application sends emails normally - Sandbox captures them
* **Inbound**: Send emails to your sandbox's unique addresses for testing replies and parsing

### 3. Review & Analyze

Access your sandbox to preview, test, and share all captured emails (both sent and received).

## Quick Start

{% stepper %}
{% step %}
**Create a Sandbox**

Log in and create your first sandbox. Name it based on your project or environment.
{% endstep %}

{% step %}
**Configure Your App**

Update your application's SMTP settings with sandbox credentials.
{% endstep %}

{% step %}
**Send Test Email**

Send a test email from your application to verify the connection.
{% endstep %}

{% step %}
**Analyze Results**

Review the captured email in your sandbox inbox.
{% endstep %}
{% endstepper %}

## Integration Methods

### SMTP Integration

Works with any application or framework:

```python
# Python example
import smtplib

server = smtplib.SMTP('sandbox.smtp.mailtrap.io', 2525)
server.login('username', 'password')
server.sendmail(from_addr, to_addr, message)
```

### API Integration with Official SDKs

Full programmatic access with our official SDKs for all major languages:

**Node.js SDK:**

```javascript
const { MailtrapClient } = require("mailtrap");

const client = new MailtrapClient({
  token: "YOUR_API_TOKEN",
  testInboxId: INBOX_ID
});

// Send test email
await client.testing.send({
  from: { email: "test@example.com" },
  to: [{ email: "user@example.com" }],
  subject: "Test Email",
  text: "Testing in sandbox"
});
```

**PHP SDK:**

```php
use Mailtrap\MailtrapClient;
use Mailtrap\Helper\ResponseHelper;

$mailtrap = new MailtrapClient('YOUR_API_TOKEN');

// Get sandbox messages
$response = $mailtrap->sandbox()
    ->inbox(INBOX_ID)
    ->messages()
    ->get();
```

**Available SDKs:**

* Node.js/TypeScript
* PHP
* Python
* Ruby
* Java
* Go
* .NET

### Email Address per Sandbox

Each sandbox automatically gets unique email addresses:

```
# Example addresses for your sandbox:
sandbox-12345@inbox.mailtrap.net
test-project-67890@inbox.mailtrap.net

# Test inbound email processing:
1. Send email to your sandbox address
2. Process received email via API/SDK or review in your Sandbox
3. Test reply handling and parsing
```

### Framework Examples

Pre-configured for popular frameworks:

* Laravel
* Ruby on Rails
* Django
* Spring Boot
* others

## Testing Capabilities

### Email Validation

* **HTML Validation**: Check for rendering issues
* **Attachment Testing**: Validate file handling

### Deliverability Testing

* **Spam Score**: SpamAssassin scoring
* **Blacklist Check**: IP reputation verification
* **Header Analysis**: Technical validation

## Best Practices

### Environment Separation

* Use different sandboxes for dev, staging, QA
* Name sandboxes clearly (e.g., "iOS App - Dev")
* Document sandbox purposes

### Testing Strategy

* Test both happy path and edge cases
* Check mobile responsiveness
* Test with real data (safely)
* Automate repetitive tests

## Getting Started

{% columns %}
{% column %}
**Setup Guides**

* [Application Integration](setup/sandbox-smtp-integration.md)
* [Sandbox API](sandbox-api-integration.md)
* [Email Address Setup](email-address-per-sandbox.md)
{% endcolumn %}

{% column %}
**Testing Tools**

* [Email Inspector](inspect-your-email-template.md)
* [HTML Check](html-check.md)
* [Deliverability Tests](testing/spam-blacklist-reports.md)
* [Bounce Emulator](testing/bounce-rate.md)
{% endcolumn %}
{% endcolumns %}

## Support & Resources

* [Features and Limits](help/features-and-limits.md)
* [Sandbox Glossary](help/glossary.md)
* [FAQs](faqs.md)
* [Troubleshooting](troubleshooting.md)

## Next Steps

1. [**Create your first sandbox**](setup/) - Get started in minutes
2. [**Integrate with your app**](setup/sandbox-smtp-integration.md) - Configure SMTP settings
3. [**Test email templates**](inspect-your-email-template.md) - Validate your emails
4. [**Share with team**](sharing-sandboxes.md) - Collaborate on testing
