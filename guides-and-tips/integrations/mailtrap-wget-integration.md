---
title: <i class="fa-download">:download:</i> Mailtrap Wget integration
description: >-
  Learn how to integrate Mailtrap with Wget to send emails via the command line
  using the Email API.
---

# Wget Integration

This guide shows you how to integrate Mailtrap with Wget and send emails using the Email API.

Before we start, you'll need to:

* [Verify your sending domain](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/setup/sending-domain-setup)
* [Create and save an API key](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/account-and-organization/privacy-and-security/api-tokens)

## Send emails using Wget and Mailtrap

To integrate Mailtrap and send emails via Wget, copy the following script into your terminal:

{% code title="send-email.sh" %}
```bash
wget --method POST \
  --header 'Authorization: Bearer YOUR-MAILTRAP-API-KEY-HERE' \
  --header 'Content-Type: application/json' \
  --body-data $'{
    "from": {
      "name": "Mailtrap Test",
      "email": "YOUR-EMAIL-HERE"
    },
    "to": [
      {
        "email": "RECIPIENT-EMAIL-HERE"
      }
    ],
    "subject": "Hello World",
    "html": "<strong>it works!</strong>"
  }' \
  'https://send.api.mailtrap.io/api/send'
```
{% endcode %}

Once you copy the script, make sure to:

* Insert your Mailtrap API token in the `Authorization` field as `Bearer`
* Enter your email address in the `from:` field
* Enter your recipient's email address in the `to:` field

{% hint style="info" %}
To learn more about API integration, see [Mailtrap Email Sending API Integration](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/api-integration).
{% endhint %}
