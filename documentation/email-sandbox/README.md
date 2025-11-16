---
title: Email Sandbox Overview
description: Test and preview emails safely in a sandbox environment before sending to production
---

# Email Sandbox Overview

Email Sandbox is a safe testing environment that captures all your test emails, preventing them from reaching real inboxes. Perfect for development, QA testing, and staging environments, it ensures your email functionality works flawlessly before going live.

## What is Email Sandbox?

Email Sandbox acts as a fake SMTP server that traps all emails sent from your application. Instead of delivering to actual recipients, emails are captured in a secure inbox where you can:
- Preview how emails look across different clients
- Test email workflows without risk
- Validate HTML rendering and responsiveness
- Debug email issues before production
- Share test results with your team

## Key Features

### 🧪 Safe Testing Environment
- **Zero Risk**: Emails never reach real recipients
- **Unlimited Testing**: No limits on test emails
- **Multiple Sandboxes**: Separate environments for different projects
- **Team Collaboration**: Share sandboxes with team members

### 📧 Email Analysis Tools
- **HTML/Text Preview**: See exactly how emails render
- **Spam Score Analysis**: Predict spam filter behavior
- **Email Headers**: Inspect all technical details
- **Attachment Support**: Test file attachments
- **Dark Mode Preview**: Check dark mode compatibility

### 🔍 Advanced Testing
- **Deliverability Tests**: Check authentication and content
- **Bounce Emulation**: Test bounce handling
- **Load Testing**: Verify performance under load
- **API Access**: Automate testing workflows
- **Webhook Testing**: Validate event handling

### 🤝 Collaboration Features
- **Shared Sandboxes**: Team-wide access
- **Email Forwarding**: Share specific test cases
- **Comments & Notes**: Discuss issues inline
- **Access Control**: Manage permissions

## Use Cases

### Development Testing
Perfect for developers building email features:
- Test email templates during development
- Verify dynamic content and personalization
- Debug email sending logic
- Test different email scenarios
- Validate email formatting

### QA & Staging
Essential for quality assurance:
- End-to-end workflow testing
- Cross-client compatibility checks
- Regression testing
- Performance testing
- User acceptance testing

### Email Design
Ideal for designers and marketers:
- Preview email designs
- Test responsive layouts
- Check image rendering
- Validate link tracking
- Review content formatting

## How It Works

### 1. Simple Integration
Replace your SMTP settings with Sandbox credentials:

```
Host: sandbox.smtp.mailtrap.io
Port: 2525
Username: YOUR_SANDBOX_USERNAME
Password: YOUR_SANDBOX_PASSWORD
```

### 2. Send Test Emails
Your application sends emails normally - Sandbox captures them automatically.

### 3. Review & Analyze
Access your sandbox to preview, test, and share captured emails.

## Quick Start

{% stepper %}
{% step %}
### Create a Sandbox
Log in and create your first sandbox. Name it based on your project or environment.
{% endstep %}

{% step %}
### Configure Your App
Update your application's SMTP settings with sandbox credentials.
{% endstep %}

{% step %}
### Send Test Email
Send a test email from your application to verify the connection.
{% endstep %}

{% step %}
### Analyze Results
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

### API Integration
Programmatic access for automation:
```javascript
// Fetch emails via API
const response = await fetch('https://mailtrap.io/api/v1/inboxes/INBOX_ID/messages', {
  headers: {
    'Authorization': 'Bearer YOUR_API_TOKEN'
  }
});
```

### Framework Examples
Pre-configured for popular frameworks:
- Laravel
- Ruby on Rails
- Django
- Spring Boot
- Express.js

## Testing Capabilities

### Email Validation
- **HTML Validation**: Check for rendering issues
- **Link Testing**: Verify all URLs work
- **Image Loading**: Ensure images display
- **Attachment Testing**: Validate file handling
- **Character Encoding**: UTF-8 support verification

### Deliverability Testing
- **Spam Score**: SpamAssassin scoring
- **Authentication**: SPF, DKIM, DMARC checks
- **Blacklist Check**: IP reputation verification
- **Content Analysis**: Spam trigger detection
- **Header Analysis**: Technical validation

### Performance Testing
- **Load Testing**: Send thousands of test emails
- **Response Time**: Measure email processing
- **Bulk Operations**: Test mass email scenarios
- **Rate Limiting**: Verify throttling behavior
- **Queue Management**: Test email queuing

## Pricing & Plans

### Free Plan
- 500 emails/month per inbox
- 2 sandboxes
- 5-second auto-refresh
- 7-day email retention

### Individual & Team Plans
- Unlimited emails
- Unlimited sandboxes
- API access
- Team collaboration
- Extended retention

### Enterprise
- Custom retention policies
- SSO integration
- Priority support
- SLA guarantees

## Best Practices

### Environment Separation
- Use different sandboxes for dev, staging, QA
- Name sandboxes clearly (e.g., "iOS App - Dev")
- Regular cleanup of old test emails
- Document sandbox purposes

### Testing Strategy
- Test both happy path and edge cases
- Verify email rendering across clients
- Check mobile responsiveness
- Test with real data (safely)
- Automate repetitive tests

## Getting Started

{% columns %}
{% column %}
### Setup Guides
- [Application Integration](how-to-integrate-email-sandbox-with-your-application.md)
- [Sandbox API](sandbox-api-integration.md)
- [Email Address Setup](email-address-per-sandbox.md)
{% endcolumn %}

{% column %}
### Testing Tools
- [Email Inspector](inspect-your-email-template.md)
- [HTML Check](html-check.md)
- [Deliverability Tests](deliverability-tests.md)
- [Bounce Emulator](bounce-emulator.md)
{% endcolumn %}
{% endcolumns %}

## Support & Resources

- 📚 [Features and Limits](features-and-limits.md)
- 📖 [Sandbox Glossary](sandbox-glossary.md)
- 💬 [FAQs](faqs.md)
- 🔧 [Troubleshooting](troubleshooting.md)

## Next Steps

1. **[Create your first sandbox](setup/README.md)** - Get started in minutes
2. **[Integrate with your app](how-to-integrate-email-sandbox-with-your-application.md)** - Configure SMTP settings
3. **[Test email templates](inspect-your-email-template.md)** - Validate your emails
4. **[Share with team](sharing-sandboxes.md)** - Collaborate on testing