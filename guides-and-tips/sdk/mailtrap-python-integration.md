---
title: <i class="fa-python">:python:</i> Mailtrap Python Integration
description: >-
  Learn how to integrate Mailtrap with Python apps and projects for email
  sending using SDK, SMTP, and RESTful API.
icon: python
---

<a href="https://github.com/mailtrap/mailtrap-python" class="button secondary">Mailtrap Python SDK on GitHub</a>

# Python Integration

## Overview

Mailtrap can be integrated with Python apps and projects for email sending purposes.

## Email API/SMTP for Python

### SDK Integration

The [Mailtrap Python SDK](https://github.com/mailtrap/mailtrap-python) is a Pythonic library for sending transactional and bulk emails with full type hints support. The SDK supports:

- Transactional email sending
- Batch email sending
- Template management
- Contact management
- Sandbox testing
- Account management
- Type hints for better IDE support

## Installation

Install the SDK using pip:

{% code title="pip" %}
```bash
pip install mailtrap
```
{% endcode %}

## Minimal Example

Here's a minimal example to send your first email:

{% code title="send_email.py" %}
```python
from mailtrap import Mail, MailtrapClient

client = MailtrapClient(token="your-api-token")

mail = Mail(
    sender={"email": "hello@example.com", "name": "Mailtrap Test"},
    to=[{"email": "recipient@example.com"}],
    subject="Hello from Mailtrap!",
    text="Welcome to Mailtrap Email Sending!",
    html="<p>Welcome to <strong>Mailtrap</strong> Email Sending!</p>"
)

try:
    response = client.send(mail)
    print(response)
except Exception as e:
    print(f"Error: {e}")
```
{% endcode %}

{% hint style="info" %}
Get your API token from the Mailtrap dashboard under **Settings → API Tokens**.
{% endhint %}

### SMTP Integration

To integrate SMTP with your Python app, navigate to the **Integrations** tab, choose the desired Python framework, and copy-paste the credentials or ready-made code snippets.

{% hint style="info" %}
SMTP integration is compatible with any Python framework or library that sends emails using SMTP.
{% endhint %}

![SMTP integration for Python](../.gitbook/assets/mailtrap-python-smtp-integration.png)

Read more about SMTP integration in the [Email API/SMTP - SMTP Integration](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/smtp-integration) article.

### RESTful API Integration

To integrate Mailtrap using RESTful API, use the configuration available among **Code samples** under the API section.

API integration can be used with any Python framework or library that supports HTTP requests. For more details, refer to the [API documentation](https://api-docs.mailtrap.io/docs/mailtrap-api-docs/5tjdeg9545058-mailtrap-api).

![API integration for Python](../.gitbook/assets/mailtrap-python-api-integration.png)

Read more about API integration in the [Email API/SMTP - API Integration](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/api-integration) article.
