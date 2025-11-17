---
title: Mailtrap cURL Integration
description: Send emails using cURL with Mailtrap through SMTP integration or API endpoints with code samples and configuration options.
---

# Overview

Mailtrap can be integrated with cURL for email sending via SMTP or API methods. This guide shows you how to configure and send emails using cURL with Mailtrap.

Before we start, you'll need to:

- [Verify your sending domain](https://help.mailtrap.io/article/69-sending-domain-setup)
- [Create and save an API key](https://help.mailtrap.io/article/103-api-tokens)

## Send emails using cURL and Mailtrap

### SMTP integration

To integrate Mailtrap via SMTP, go to the **Integration** tab and copy/paste either the credentials or the pre-made code snippets into your configuration.

![Mailtrap SMTP integration tab showing host, port, username, password credentials and cURL command example](../.gitbook/assets/mailtrap-curl-integration-1.png)

You can get more information on SMTP integration [here](https://help.mailtrap.io/article/122-mailtrap-email-sending-smtp-integration).

### API integration

To integrate Mailtrap and send emails via cURL, use the configuration available among **Code samples** under the API section.

![Mailtrap API integration tab showing cURL command example with authorization bearer token and email recipient parameters](../.gitbook/assets/mailtrap-curl-integration-2.png)

Once you copy the script, make sure to insert your Mailtrap API token in the `Authorization` field as `Bearer` and enter your and your recipient's emails in the `--mail-from` and `--mail-rcpt` fields.

**Note**: To learn more about API integration, [click here](https://help.mailtrap.io/article/121-mailtrap-email-sending-api-integration).

# Next Steps

After setting up cURL integration, you can send test emails and monitor delivery through your Mailtrap dashboard to ensure proper configuration.