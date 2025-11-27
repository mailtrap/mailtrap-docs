---
title: Setup & Configuration
description: >-
  Set up and configure Mailtrap email API and SMTP service and start sending
  emails in minutes.
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

# Setup & Configuration

Complete guide to setting up and configuring Mailtrap Email API/SMTP for your application. Follow these steps to start sending emails in production.

### Quick Start Checklist

Get up and running with this essential setup checklist:

* [ ] Create your Mailtrap account
* [ ] Verify your sending domain
* [ ] Choose integration method (API or SMTP)
* [ ] Configure authentication
* [ ] Send test email

### Configuration Steps

<table data-card-size="large" data-view="cards"><thead><tr><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><strong>Sending Domain Setup</strong><br><br>The foundation of email delivery. Verify your domain ownership and configure authentication records (SPF, DKIM, DMARC) for optimal deliverability.</td><td><a href="../sending-domain-setup.md">sending-domain-setup.md</a></td></tr><tr><td><strong>API Integration</strong><br><br>Modern RESTful API for programmatic email sending. Best for new applications and microservices architecture.</td><td><a href="../api-integration.md">api-integration.md</a></td></tr><tr><td><strong>SMTP Integration</strong><br><br>Traditional SMTP protocol for universal compatibility. Works with any email library or legacy system.</td><td><a href="../smtp-integration.md">smtp-integration.md</a></td></tr><tr><td><strong>Dedicated IP</strong><br><br>Gradually build your sending reputation. Essential for high-volume senders and dedicated IPs.</td><td><a href="../deliverability/ip-warmup.md">ip-warmup.md</a></td></tr></tbody></table>

### Choose Your Integration Method

#### When to Use API

**Best for:**

* Modern web applications
* Microservices architecture
* Cloud-native applications
* Real-time sending needs
* Advanced analytics requirements

**Advantages:**

* Faster performance
* Better error handling
* Detailed response data
* Webhook support
* Easier debugging

**Example:**

```bash
curl -X POST "https://send.api.mailtrap.io/api/send" \
  -H "Authorization: Bearer YOUR_API_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "from": {"email": "hello@example.com"},
    "to": [{"email": "user@example.com"}],
    "subject": "Test Email",
    "text": "This is a test email"
  }'
```

#### When to Use SMTP

**Best for:**

* Legacy applications
* Email clients
* CMS platforms
* Standard libraries
* Minimal code changes

**Advantages:**

* Universal compatibility
* No code changes required
* Works with any language
* Familiar protocol
* Easy migration
