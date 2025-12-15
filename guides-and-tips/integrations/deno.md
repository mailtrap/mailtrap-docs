---
description: Learn how to integrate Mailtrap with Deno to send emails using the Email API.
---

# Deno Integration

This guide shows you how to integrate Mailtrap with Deno and send emails using the Email API.

Before we start, you'll need to:

* [Verify your sending domain](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/setup/sending-domain)
* [Create and save an API key](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/account-and-organization/privacy-and-security/api-tokens)

## Send emails using Deno and Mailtrap

To integrate Mailtrap and send emails via Deno, simply copy/paste the following script into your configuration:

{% code title="deno-example.ts" %}
```typescript
import { serve } from 'https://deno.land/std@0.190.0/http/server.ts';

const MAILTRAP_API_KEY = 'YOUR-MAILTRAP-API-KEY-HERE';

const handler = async (_request: Request): Promise<Response> => {
  const res = await fetch('https://send.api.mailtrap.io/api/send', {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json',
      'Authorization': `Bearer ${MAILTRAP_API_KEY}`
    },
    body: JSON.stringify({
      from: { name: 'Mailtrap Test', email: 'YOUR-EMAIL-HERE' },
      to: [{ email: 'RECIPIENT-EMAIL-HERE' }],
      subject: 'Hello World',
      html: '<strong>it works!</strong>',
    })
  });

  if (res.ok) {
    const data = await res.json();

    return new Response(JSON.stringify(data), {
      status: 200,
      headers: {
        'Content-Type': 'application/json',
      },
    });
  }

  return new Response(JSON.stringify({ error: `HTTP ${res.status}` }), {
    status: 400,
    headers: {
      'Content-Type': 'application/json',
    },
  });
};

serve(handler);
```
{% endcode %}

Once you copy the script, make sure to insert your Mailtrap API token in the `MAILTRAP_API_KEY` field and enter your and your recipient's emails in the `from` and `to` fields.

{% hint style="info" %}
To learn more about API integration, [click here](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/setup/api-integration).
{% endhint %}
