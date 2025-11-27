---
title: <i class="fa-fire">:fire:</i> Mailtrap Hono integration
description: Learn how to integrate Mailtrap with Hono to send emails using the Email API.
---

# Hono Integration

This guide shows you how to integrate Mailtrap with Hono and send emails using the Email API.

Before we start, you'll need to:

* [Verify your sending domain](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/setup/sending-domain-setup)
* [Create and save an API key](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/account-and-organization/privacy-and-security/api-tokens)

## Send emails using Hono and Mailtrap

To integrate Mailtrap and send emails via Hono, simply copy/paste the following script into your configuration:

{% code title="hono-example.ts" %}
```typescript
import { Hono } from 'hono';
import { MailtrapClient } from 'mailtrap';

const app = new Hono();
const mailtrap = new MailtrapClient({ token: 'YOUR-MAILTRAP-API-KEY-HERE' });

app.get('/', async (c) => {
  try {
    const response = await mailtrap.send({
      from: { name: 'Mailtrap Test', email: 'YOUR-EMAIL-HERE' },
      to: [{ email: 'RECIPIENT-EMAIL-HERE' }],
      subject: 'Hello World',
      html: '<strong>it works!</strong>',
    });

    console.log(response);

    return c.json(response);
  } catch (error) {
    const message = error instanceof Error ? error.message : 'Unknown error';
    console.log(message);
    
    return c.json({ message }, 400);
  }
});

export default app;
```
{% endcode %}

Once you copy the script, make sure to insert your Mailtrap API token in the `token` field and enter your and your recipient's emails in the `from` and `to` fields.

{% hint style="info" %}
To learn more about API integration, [click here](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/api-integration).
{% endhint %}
