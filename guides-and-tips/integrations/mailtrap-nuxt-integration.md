---
title: <i class="fa-vuejs">:vuejs:</i> Mailtrap Nuxt integration
description: Learn how to send emails in Nuxt applications using Mailtrap's Email API.
---

# Overview

This guide shows you how to integrate Mailtrap with Nuxt and send emails using the Email API.

Before we start, you'll need to:

- [Verify your sending domain](https://help.mailtrap.io/article/69-sending-domain-setup)
- [Create and save an API key](https://help.mailtrap.io/article/103-api-tokens)

## Send emails using Nuxt and Mailtrap

To integrate Mailtrap and send emails via Nuxt, simply copy/paste the following script into your configuration:

{% code title="Nuxt event handler" %}
```javascript
import { MailtrapClient } from "mailtrap";

const mailtrap = new MailtrapClient({ token: 'YOUR-MAILTRAP-API-KEY-HERE' });

export default defineEventHandler(async () => {
  try {
    const response = await mailtrap.send({
      from: { name: 'Mailtrap Test', email: 'YOUR-EMAIL-HERE' },
      to: [{ email: 'RECIPIENT-EMAIL-HERE' }],
      subject: 'Hello World',
      html: '<strong>it works!</strong>',
    });

    console.log(response);

    return response;
  } catch (error) {
    throw createError({
      statusCode: 400,
      statusMessage: error instanceof Error ? error.message : 'Unknown error',
    });
  }
});
```
{% endcode %}

Once you copy the script, make sure to insert your Mailtrap API token in the `token:` field and enter your and your recipient's emails in the `from:` and `to:` fields.

{% hint style="info" %}
To learn more about API integration, [click here](https://help.mailtrap.io/article/121-mailtrap-email-sending-api-integration).
{% endhint %}