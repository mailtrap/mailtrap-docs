---
title: Help & Support
description: Get help with Email API/SMTP issues and find answers to common questions.
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

### <i class="fa-comments-question-check">:comments-question-check:</i>Contact Support

If you can’t find the answer you need in our documentation and would like to contact support and speak with an agent, we’re here to help.

You can get in touch with the Mailtrap Support team using one of the following ways:

* **From your Mailtrap account**&#x20;

1. Log in to your account [here](https://mailtrap.io/signin).
2. Go to the <i class="fa-circle-question">:circle-question:</i>[<mark style="color:$primary;">**Help Center**</mark>](https://mailtrap.io/help-center) > <i class="fa-message-dots">:message-dots:</i> Get Help
3. Click <mark style="color:$primary;">**Start conversation.**</mark>&#x20;

<figure><img src="../../.gitbook/assets/Screenshot 2026-02-19 at 17.12.57.png" alt=""><figcaption></figcaption></figure>

* **Email us at** 📧 support@mailtrap.io

Whether you need technical assistance, help troubleshooting an issue, or simply want to talk to customer support, our team will be happy to assist you.

### Before Contacting Support

Please have the following information ready:

* Your account email
* Error messages (exact wording)
* Request IDs from email logs
* Steps to reproduce the issue
* Screenshots if applicable

## Quick Solutions

### Can't send emails?

1. Verify your [API token](../setup/api-tokens.md) is correct
2. Check your [sending domain](../setup/sending-domain.md) is verified
3. Review your [sending limits](../setup/sending-limits.md)
4. Confirm your [integration](../api-integration.md) is properly configured

### Emails not reaching inbox?

1. Check [email logs](../analytics/logs.md) for delivery status
2. Review [bounce categorization](../bounce-categorization.md) for issues
3. Verify SPF, DKIM, and DMARC records
4. Check if recipients are on [suppressions list](../suppressions-list.md)

### Integration issues?

1. Review the [API integration guide](../api-integration.md)
2. Check the [SMTP integration guide](../smtp-integration.md)
3. Test with [Email Sandbox](../../email-sandbox/overview.md) first
4. Use our [API reference](https://api-docs.mailtrap.io/) for detailed endpoints
