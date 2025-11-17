---
title: <i class="fa-tree">:tree:</i> Mailtrap Redwood integration
description: Learn how to send emails in Redwood applications using Mailtrap's Email API.
---

# Overview

This guide shows you how to integrate Mailtrap with Redwood and send emails using the Email API.

Before we start, you'll need to:

- [Verify your sending domain](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/setup/sending-domain-setup)
- [Create and save an API key](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/account-and-organization/api-tokens)

## Send emails using Redwood and Mailtrap

To integrate Mailtrap and send emails via Redwood, simply copy/paste the following script into your configuration:

{% code title="Redwood API handler" %}
```typescript
import { MailtrapClient } from 'mailtrap';
import type { APIGatewayEvent, Context } from 'aws-lambda';

export const handler = async (event: APIGatewayEvent, context: Context) => {
  const mailtrap = new MailtrapClient({ token: 'YOUR-MAILTRAP-API-KEY-HERE' });

  try {
    const response = await mailtrap.send({
      from: { name: 'Mailtrap Test', email: 'YOUR-EMAIL-HERE' },
      to: [{ email: 'RECIPIENT-EMAIL-HERE' }],
      subject: 'Hello World',
      html: '<strong>it works!</strong>',
    });

    console.log(response);

    return {
      statusCode: 200,
      headers: {
        'Content-Type': 'application/json',
      },
      body: JSON.stringify(response),
    };
  } catch (error) {
    const message = error instanceof Error ? error.message : 'Unknown error';
    console.log(message);

    return {
      statusCode: 400,
      headers: {
        'Content-Type': 'application/json',
      },
      body: JSON.stringify({ message }),
    };
  }
};
```
{% endcode %}

Once you copy the script, make sure to insert your Mailtrap API token in the `token:` field and enter your and your recipient's emails in the `from:` and `to:` fields.

{% hint style="info" %}
To learn more about API integration, [click here](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/api-integration).
{% endhint %}