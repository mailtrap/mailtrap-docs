---
title: <i class="fa-aws">:aws:</i> Mailtrap AWS Lambda Integration
description: Learn how to integrate Mailtrap with AWS Lambda functions to send emails using the Mailtrap Email API.
---

# Overview

This guide explains how to integrate Mailtrap with AWS Lambda functions to send emails programmatically using the Mailtrap Email API.

## Prerequisites

Before you start, make sure you have:

- [Verified your sending domain](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/setup/sending-domain-setup)
- [Created and saved an API key](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/account-and-organization/api-tokens)

# Send emails using AWS Lambda and Mailtrap

To integrate Mailtrap and send emails via AWS Lambda, copy and paste the following script into your Lambda function:

{% code title="lambda-mailtrap-handler.js" %}
```javascript
/* global fetch */
const MAILTRAP_API_KEY = 'YOUR-MAILTRAP-API-KEY-HERE';

export const handler = async (event) => {
  try {
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

      return {
        statusCode: 200,
        headers: {
          'Content-Type': 'application/json',
        },
        body: JSON.stringify(data),
      };
    }

    return {
      statusCode: 400,
      headers: {
        'Content-Type': 'application/json',
      },
      body: JSON.stringify({ error: `HTTP ${res.status}` }),
    };
  } catch (error) {
    return {
      statusCode: 500,
      headers: {
        'Content-Type': 'application/json',
      },
      body: JSON.stringify({
        error: error instanceof Error ? error.message : 'Unknown error'
      }),
    };
  }
};
```
{% endcode %}

## Configuration

Once you copy the script, update the following fields with your information:

- Replace `YOUR-MAILTRAP-API-KEY-HERE` in the `MAILTRAP_API_KEY` constant with your actual API token
- Replace `YOUR-EMAIL-HERE` with your verified sender email
- Replace `RECIPIENT-EMAIL-HERE` with the recipient's email address

## Learn more

For additional details about the Email API, refer to the [Mailtrap Email Sending API Integration guide](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/api-integration).