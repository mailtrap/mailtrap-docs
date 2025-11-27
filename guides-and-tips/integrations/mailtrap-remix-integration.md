---
title: <i class="fa-react">:react:</i> Mailtrap Remix integration
description: >-
  Learn how to integrate Mailtrap with Remix to send emails from your
  application using the Email API.
---

# Remix Integration

This guide shows you how to integrate Mailtrap with Remix and send emails using the Email API.

Before we start, you'll need to:

* [Verify your sending domain](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/setup/sending-domain-setup)
* [Create and save an API key](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/account-and-organization/privacy-and-security/api-tokens)

## Send emails using Remix and Mailtrap

To integrate Mailtrap and send emails via Remix, copy the following script into your configuration:

{% code title="remix-server.js" %}
```javascript
import { json } from '@remix-run/node';
import { MailtrapClient } from 'mailtrap';

const mailtrap = new MailtrapClient({ token: 'YOUR-MAILTRAP-API-KEY-HERE' });

export const loader = async () => {
  try {
    const response = await mailtrap.send({
      from: { name: 'Mailtrap Test', email: 'YOUR-EMAIL-HERE' },
      to: [{ email: 'RECIPIENT-EMAIL-HERE' }],
      subject: 'Hello World',
      html: '<strong>it works!</strong>',
    });

    console.log(response);

    return json(response, 200);
  } catch (error) {
    const message = error instanceof Error ? error.message : 'Unknown error';
    console.log(message);

    return json({ message }, 400);
  }
};
```
{% endcode %}

Once you copy the script, make sure to:

* Insert your Mailtrap API token in the `token:` field
* Enter your email address in the `from:` field
* Enter your recipient's email address in the `to:` field

{% hint style="info" %}
To learn more about API integration, see [Mailtrap Email Sending API Integration](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/api-integration).
{% endhint %}
