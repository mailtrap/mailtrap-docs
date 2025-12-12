---
description: >-
  Learn how to integrate Mailtrap with Cloudflare Workers to send emails using
  the Mailtrap Email API.
---

# Cloudflare Workers Integration

## Overview

This guide explains how to integrate Mailtrap with Cloudflare Workers to send emails programmatically using the Mailtrap Email API.

### Prerequisites

Before you start, make sure you have:

* [Verified your sending domain](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/setup/sending-domain)
* [Created and saved an API key](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/account-and-organization/privacy-and-security/api-tokens)

## Send emails using Cloudflare Workers and Mailtrap

To integrate Mailtrap and send emails via Cloudflare Workers, copy and paste the following script into your worker configuration:

{% code title="cloudflare-worker-mailtrap.ts" %}
```typescript
export default {
  async fetch(request: Request, env: Env, ctx: ExecutionContext): Promise<Response> {
    try {
      const response = await fetch("https://send.api.mailtrap.io/api/send", {
        method: "POST",
        headers: {
          "Authorization": "Bearer YOUR-MAILTRAP-API-KEY-HERE",
          "Content-Type": "application/json",
        },
        body: JSON.stringify({
          from: { name: 'Mailtrap Test', email: 'YOUR-EMAIL-HERE' },
          to: [{ email: 'RECIPIENT-EMAIL-HERE' }],
          subject: 'Hello World',
          html: '<strong>it works!</strong>',
        }),
      });

      const data = await response.json();

      return new Response(JSON.stringify(data), {
        headers: {
          'Content-Type': 'application/json',
        },
      });
    } catch (error) {
      return new Response(JSON.stringify({
        error: error instanceof Error ? error.message : 'Unknown error'
      }), {
        status: 400,
        headers: { 'Content-Type': 'application/json' },
      });
    }
  },
};
```
{% endcode %}

### Configuration

Once you copy the script, update the following fields with your information:

* Replace `YOUR-MAILTRAP-API-KEY-HERE` in the `Authorization` header with your actual API token as a `Bearer` token
* Replace `YOUR-EMAIL-HERE` with your verified sender email
* Replace `RECIPIENT-EMAIL-HERE` with the recipient's email address

### Learn more

For additional details about the Email API, refer to the [Mailtrap Email Sending API Integration guide](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/setup/api-integration).
