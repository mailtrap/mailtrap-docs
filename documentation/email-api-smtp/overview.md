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
  tags:
    visible: true
  actions:
    visible: true
---

# Overview

Mailtrap Email API/SMTP lets you send transactional and bulk emails. Integrate with the Email Sending API or SMTP.

### Choose a sending stream

Choose a stream based on the email type:

* **Transactional Stream** sends automated, non-promotional emails. Examples include password resets and order confirmations.
* [**Bulk Stream**](setup/bulk-stream.md) sends marketing campaigns to many recipients. Examples include newsletters and promotions.

### Choose an integration method

Use the method that fits your application:

* [**Email Sending API**](api-integration.md) sends emails through authenticated HTTP requests and supported SDKs.
* [**SMTP**](smtp-integration.md) works with existing email clients and libraries.

Both methods support Mailtrap Email Logs and analytics.

### Get started

{% columns %}
{% column %}
**Set up sending**

* [Set up a sending domain](setup/sending-domain.md)
* [Integrate with the Email Sending API](api-integration.md)
* [Integrate with SMTP](smtp-integration.md)
* [Warm up an IP address](deliverability/ip-warmup.md)
{% endcolumn %}

{% column %}
**Manage email sending**

* [Create email templates](email-templates/)
* [Review analytics and reports](analytics/)
* [Configure deliverability features](deliverability/)
* [Read the deliverability guide](https://mailtrap.io/email-deliverability-guide/)
{% endcolumn %}
{% endcolumns %}

### Support and resources

<a href="https://docs.mailtrap.io/developers" class="button primary" data-icon="books">API Reference</a> <a href="faqs.md" class="button primary" data-icon="messages-question">FAQs</a> <a href="troubleshooting/" class="button primary" data-icon="screwdriver-wrench">Troubleshooting</a> <a href="mailto:support@mailtrap.io" class="button primary" data-icon="envelope">Contact Support</a>

### Next steps

{% stepper %}
{% step %}
[setup](setup/ "mention")

_Set up your sending domain_
{% endstep %}

{% step %}
[api-integration.md](api-integration.md "mention")

_Integrate with the Email Sending API_
{% endstep %}

{% step %}
[email-templates](email-templates/ "mention")

_Create reusable email templates_
{% endstep %}

{% step %}
[analytics](analytics/ "mention")

_Review your email metrics_
{% endstep %}
{% endstepper %}
