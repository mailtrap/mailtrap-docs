---
title: Email API/SMTP Overview
description: >-
  Overview of Mailtrap Email API and SMTP service: key features, use cases, and
  target audience.
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

# Overview

Mailtrap Email API/SMTP is a reliable email delivery service designed for developers and businesses to send transactional and bulk emails at scale. Whether you're sending password resets, order confirmations, or marketing campaigns, we ensure your emails reach the inbox.

## What is Email API/SMTP?

Email API/SMTP provides two powerful methods for sending emails:

* **RESTful API**: Modern, flexible API for programmatic email sending
* **SMTP Service**: Traditional protocol compatible with any email client or library

Both methods offer the same features, deliverability, and analytics - choose based on your technical requirements.

## Key Features

#### Reliable Delivery

* Enterprise-grade infrastructure: Built for reliability and scale
* Automatic Failover: Redundant systems ensure delivery
* Smart Routing: Optimal rules selection for each email depending on recipient MX

#### Analytics & Monitoring

* Real-Time Analytics: Track opens, clicks, bounces instantly
* Detailed Email Logs: Full visibility into email journey
* Custom Categories: Organize and analyze by type/templates/etc
* Webhook Events: Real-time notifications for email events

#### Deliverability + Support

* Deliverability and Support teams: helps with migration, monitoring and all questions you might have
* [Complete Deliverability Guide](https://mailtrap.io/email-deliverability-guide/): Best practices for optimal inbox placement
* Domain Authentication: SPF, DKIM, DMARC setup
* Dedicated IP + Warmup: Gradual reputation building
* Suppressions Management: Automatic bounce handling
* Feedback Loops: ISP complaint processing

#### Developer-Friendly

* Official SDKs: Node.js, PHP, Python, Ruby, and more
* RESTful API: Simple JSON-based communication
* SMTP Integration: Works with existing email libraries
* Sandbox Testing: Test before production

## Use Cases

#### Transactional Emails

Perfect for critical user communications:

* Password resets and account verification
* Order confirmations and shipping notifications
* Appointment reminders and alerts
* System notifications and updates
* Two-factor authentication codes

#### Bulk Emails

Dedicated infrastructure for marketing:

* Newsletters and announcements
* Promotional campaigns
* Product updates and releases
* Event invitations
* Customer surveys

## Quick Start Guide

{% stepper %}
{% step %}
**Choose Your Integration Method**

{% tabs %}
{% tab title="API" %}
```bash
curl -X POST "https://send.api.mailtrap.io/api/send" \
  -H "Authorization: Bearer YOUR_API_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "from": {"email": "hello@example.com"},
    "to": [{"email": "user@example.com"}],
    "subject": "Hello from Mailtrap!",
    "text": "Welcome to Mailtrap Email API"
  }'
```
{% endtab %}

{% tab title="SMTP" %}
```
Host: live.smtp.mailtrap.io
Port: 587
Username: YOUR_USERNAME
Password: YOUR_PASSWORD
Encryption: STARTTLS
```
{% endtab %}

{% tab title="Node.js SDK" %}
```javascript
const { MailtrapClient } = require("mailtrap");

const client = new MailtrapClient({
  token: "YOUR_API_TOKEN"
});

await client.send({
  from: { email: "hello@example.com" },
  to: [{ email: "user@example.com" }],
  subject: "Hello from Mailtrap!",
  text: "Welcome to Mailtrap Email API"
});
```
{% endtab %}
{% endtabs %}
{% endstep %}

{% step %}
**Verify Your Domain**

Add DNS records to authenticate your sending domain and improve deliverability.
{% endstep %}

{% step %}
**Start Sending**

Begin with transactional emails, then expand to bulk campaigns as needed.
{% endstep %}
{% endstepper %}

## Two Streams Architecture

Mailtrap separates email traffic for optimal deliverability:

| Stream                                       | Purpose               | Features                                                              |
| -------------------------------------------- | --------------------- | --------------------------------------------------------------------- |
| **Transactional**                            | Triggered user emails | High priority, immediate delivery                                     |
| [**Bulk**](setup/get-started-bulk-stream.md) | Marketing campaigns   | Built-in compliance, unsubscribe management, separate suppresion list |

## Getting Started

{% columns %}
{% column %}
**Setup & Configuration**

* [Sending Domain Setup](sending-domain-setup.md)
* [API Integration](api-integration.md)
* [SMTP Integration](smtp-integration.md)
* [IP Warmup](deliverability/ip-warmup.md)
{% endcolumn %}

{% column %}
**Essential Features**

* [Deliverability Guide](https://mailtrap.io/email-deliverability-guide/)
* [Email Templates](email-templates/)
* [Analytics & Reports](statistics/)
* [Deliverability Features](deliverability/)


{% endcolumn %}
{% endcolumns %}

## Why Choose Mailtrap?

**For Developers**

* Clean, well-documented APIs
* Multiple integration options
* Comprehensive SDKs
* Sandbox environment for testing

**For Businesses**

* High deliverability rates
* Detailed analytics and reporting
* Scalable infrastructure
* Enterprise-grade reliability

**For Teams**

* Multi-user access control
* Shared resources and templates
* Collaborative workflows
* Activity logging

## Support & Resources

Need help getting started or have questions?

<a href="https://api-docs.mailtrap.io/" class="button primary" data-icon="books">API Reference</a>  <a href="faqs.md" class="button primary" data-icon="messages-question">FAQs</a>  <a href="troubleshooting/" class="button primary" data-icon="screwdriver-wrench">Troubleshooting</a>  <a href="mailto:support@mailtrap.io" class="button primary" data-icon="envelope">Contact Support</a>

## Next Steps

{% stepper %}
{% step %}
#### [setup](setup/ "mention")

_Authenticate your sending domain_
{% endstep %}

{% step %}
#### [api-integration.md](api-integration.md "mention")

_Choose integration method - API or SMTP_
{% endstep %}

{% step %}
#### [email-templates](email-templates/ "mention")

_Design reusable emails_
{% endstep %}

{% step %}
#### [statistics](statistics/ "mention")

_Track your email metrics_
{% endstep %}
{% endstepper %}
