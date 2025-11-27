---
title: Help & Support
description: Get help with Email API/SMTP issues and find answers to common questions.
layout:
  width: default
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
---

# Help & Support

Find answers to common questions and troubleshoot issues with Mailtrap's Email API/SMTP service. Our comprehensive help resources are designed to get you back on track quickly.

## Resources

<table data-card-size="large" data-view="cards"><thead><tr><th></th><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><strong>Frequently Asked Questions</strong></td><td><em>Browse our comprehensive FAQ section for quick answers to common questions about Email API/SMTP setup, integration, and best practices.</em></td><td><a href="../faqs.md">faqs.md</a></td></tr><tr><td><strong>Troubleshooting Guide</strong></td><td><em>Step-by-step solutions for common issues including authentication errors, domain configuration problems, and delivery issues.</em></td><td><a href="../troubleshooting/">troubleshooting</a></td></tr></tbody></table>

## Common Issues

### Authentication & Access

* [401 Unauthorized Error](../troubleshooting/unauthorized-401-error.md) - Fix API token and authentication issues
* [Domain Not Allowed](../troubleshooting/sending-from-domain-not-allowed.md) - Resolve domain verification problems

### Email Delivery Issues

* [From Header Mismatch](../troubleshooting/from-header-domain-mismatch.md) - Fix sender address configuration
* [SSL Cipher Error](../troubleshooting/ssl-cipher-overlap-error.md) - Resolve SSL/TLS connection issues
* [Office 365 Quarantine](../troubleshooting/ms-office-365-quarantine.md) - Handle Microsoft email filtering

## Getting Help

### Self-Service Resources

1. Check the [FAQs](../faqs.md) for quick answers
2. Review the [Troubleshooting Guide](../troubleshooting/)
3. Search our documentation using the search bar
4. Check our [API Reference](https://api-docs.mailtrap.io/)

### Contact Support

If you can't find the answer you need:

* **Email**: support@mailtrap.io
* **Status Page**: [status.mailtrap.io](https://status.mailtrap.io)

### Before Contacting Support

Please have the following information ready:

* Your account email
* Error messages (exact wording)
* Request IDs from email logs
* Steps to reproduce the issue
* Screenshots if applicable

## Quick Solutions

### Can't send emails?

1. Verify your [API token](../../account-and-organization/api-tokens.md) is correct
2. Check your [sending domain](../sending-domain-setup.md) is verified
3. Review your [sending limits](../setup/sending-limits.md)
4. Confirm your [integration](../api-integration.md) is properly configured

### Emails not reaching inbox?

1. Check [email logs](../statistics/email-logs.md) for delivery status
2. Review [bounce categorization](../bounce-categorization.md) for issues
3. Verify SPF, DKIM, and DMARC records
4. Check if recipients are on [suppressions list](../suppressions-list.md)

### Integration issues?

1. Review the [API integration guide](../api-integration.md)
2. Check the [SMTP integration guide](../smtp-integration.md)
3. Test with [Email Sandbox](../../email-sandbox/) first
4. Use our [API reference](https://api-docs.mailtrap.io/) for detailed endpoints
