---
description: Learn how to send emails in Astro using Mailtrap's Email API.
---

# Astro

## Overview

This guide explains how to integrate Mailtrap with your Astro project to send emails programmatically using the Mailtrap Email API.

### Prerequisites

Before you start, make sure you have:

* [Verified your sending domain](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/setup/sending-domain)
* [Created and saved an API key](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/setup/api-tokens)

## Send emails using Astro and Mailtrap

To integrate Mailtrap and send emails via Astro, copy and paste the following script into your configuration:

{% code title="astro-mailtrap-integration.js" %}
```javascript
import { ActionError, defineAction } from "astro:actions";
import { MailtrapClient } from "mailtrap";

const mailtrap = new MailtrapClient({ token: 'YOUR-MAILTRAP-API-KEY-HERE' });

export const server = {
  send: defineAction({
    accept: "form",
    handler: async () => {
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
        const message = error instanceof Error ? error.message : 'Unknown error';
        console.log(message);

        throw new ActionError({
          code: "BAD_REQUEST",
          message,
        });
      }
    },
  }),
};
```
{% endcode %}

### Configuration

Once you copy the script, update the following fields with your information:

* Replace `YOUR-MAILTRAP-API-KEY-HERE` with your actual Mailtrap API token in the `token:` field
* Replace `YOUR-EMAIL-HERE` with your verified sender email
* Replace `RECIPIENT-EMAIL-HERE` with the recipient's email address

### Learn more

For additional details about the Email API, refer to the [Mailtrap Email Sending API Integration guide](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/setup/api-integration).
