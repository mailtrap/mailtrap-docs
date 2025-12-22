---
title: ChatGPT and Mailtrap Integration
description: >-
  Send emails from a verified domain and manage contacts with custom fields
  using ChatGPT and Mailtrap Email API.
layout:
  width: default
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
---

# ChatGPT

This guide shows you how to send emails from a verified domain and manage contacts with custom fields and optional List IDs with ChatGPT and Mailtrap Email API.

## Prerequisites

Before you start, make sure you have:

* Verified sending domain in Mailtrap
* Admin API token with access to your domain, Contacts, and Production Email API
* Account ID (Go to Settings, then Account Settings in Mailtrap dashboard)
* Optional List IDs if you want to store contacts in specific lists
* Custom fields created in Mailtrap if you want to store extra metadata
* Node.js or Python installed in your GPT project environment
* Ability to set environment variables in your GPT hosting setup (via .env files or runtime configuration)

## Ready-made prompts for GPT integration

You can use the following prompts to instruct GPT to integrate the service for you.

### Email sending

| Prompt                                                                                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Create a Node.js app that uses the Mailtrap SDK to send an email via the Email API from a verified domain. Store credentials in environment variables. |

### Email sending + HTML template

| Prompt                                                                                                                  |
| ----------------------------------------------------------------------------------------------------------------------- |
| Generate a Python script using the Mailtrap SDK that sends a production email with HTML content and template variables. |

### Full integration

| Prompt                                                                                                                                             |
| -------------------------------------------------------------------------------------------------------------------------------------------------- |
| Build a Node.js app that sends a production email, then creates or updates a contact in Mailtrap Contacts with custom fields and optional List ID. |

{% hint style="info" %}
ChatGPT provides you with accurate, safe flows, and the code. However, it uses placeholders for credentials, and they need to be added in manually. And you need a proper IDE to test, run, and deploy your project.
{% endhint %}

{% hint style="success" %}
Use the Connectors feature under GPT Settings to link your GitHub repositories to GPT. This helps speed up the processes and may improve code quality.
{% endhint %}

## Step-by-step setup guide

{% stepper %}
{% step %}
### Prepare Mailtrap

1. Verify your sending domain in Mailtrap.
2. Create an Admin API token with `production_send` and `contacts_write` scopes.
3. Locate your Account ID in Settings > Account Settings.
4. (Optional) Create Lists if you plan to organize contacts.
5. (Optional) Create Custom Fields for storing metadata like `plan` or `signup_source`.
{% endstep %}

{% step %}
### Create/open your GPT project

Here we're assuming you already have a GPT-powered project within an IDE like Cursor or Replit. If so, simply open the project.

For manual setup:

{% tabs %}
{% tab title="Node.js" %}
```bash
npm init -y
npm install @mailtrap/node-sdk dotenv
```
{% endtab %}

{% tab title="Python" %}
```bash
pip install mailtrap
```
{% endtab %}
{% endtabs %}
{% endstep %}

{% step %}
### Send emails with Node.js and Python

{% tabs %}
{% tab title="Node.js" %}
```javascript
import 'dotenv/config';
import { MailtrapClient } from '@mailtrap/node-sdk';

const TOKEN = process.env.MAILTRAP_API_TOKEN;
const client = new MailtrapClient({ token: TOKEN });

async function sendEmail() {
  await client.send({
    from: { email: "sender@yourdomain.com", name: "Your App" },
    to: [{ email: "recipient@example.com", name: "John Doe" }],
    subject: "Your GPT-generated update",
    text: "Hello! This is your update.",
    html: "<p>Hello! This is your <strong>update</strong>.</p>"
  });
  console.log("Email sent successfully!");
}

sendEmail().catch(console.error);
```
{% endtab %}

{% tab title="Python" %}
```python
import os
from mailtrap import MailtrapClient

TOKEN = os.getenv("MAILTRAP_API_TOKEN")
client = MailtrapClient(token=TOKEN)

client.send(
    from_={"email": "sender@yourdomain.com", "name": "Your App"},
    to=[{"email": "recipient@example.com", "name": "John Doe"}],
    subject="Your GPT-generated update",
    text="Hello! This is your update.",
    html="<p>Hello! This is your <strong>update</strong>.</p>"
)

print("Email sent successfully!")
```
{% endtab %}
{% endtabs %}
{% endstep %}

{% step %}
### Create/update a contact in Mailtrap

{% tabs %}
{% tab title="Node.js" %}
```javascript
await client.contacts.upsert({
  email: "recipient@example.com",
  name: "John Doe",
  list_ids: ["your-list-id"], // optional
  custom_fields: {
    plan: "premium",
    signup_source: "gpt-generator"
  }
});
console.log("Contact saved successfully!");
```
{% endtab %}

{% tab title="Python (REST API)" %}
```python
import os
import requests

API_TOKEN = os.getenv("MAILTRAP_API_TOKEN")
ACCOUNT_ID = os.getenv("MAILTRAP_ACCOUNT_ID")

url = f"https://mailtrap.io/api/accounts/{ACCOUNT_ID}/contacts"

payload = {
    "email": "recipient@example.com",
    "name": "John Doe",
    "list_ids": ["your-list-id"],  # optional
    "custom_fields": {
        "plan": "premium",
        "signup_source": "gpt-generator"
    }
}

headers = {"Api-Token": API_TOKEN}

response = requests.post(url, json=payload, headers=headers)
print(response.json())
```

{% hint style="info" %}
At the moment a direct Contacts API is under development for the official Python SDK. You can use [REST instead](https://api-docs.mailtrap.io/docs/mailtrap-api-docs/b46b1fe35bdf1-import-contacts).
{% endhint %}
{% endtab %}
{% endtabs %}
{% endstep %}

{% step %}
### Run and verify

1. Set your environment variables in GPT's environment:

```bash
export MAILTRAP_API_TOKEN="your_api_token"
export MAILTRAP_ACCOUNT_ID="your_account_id"
```

2. Run the script:

{% tabs %}
{% tab title="Node.js" %}
```bash
node index.js
```
{% endtab %}

{% tab title="Python" %}
```bash
python main.py
```
{% endtab %}
{% endtabs %}

3. Check the recipient inbox to ensure the email landed where it's supposed to.
4. Go to Mailtrap Contacts to verify new or updated contact.
{% endstep %}
{% endstepper %}

## Troubleshooting GPT-powered environments

* **Environment variables not loading** – GPT environments may require .env loading via `dotenv` in Node.js or `python-dotenv` in Python.
* **Port access restrictions** – Some GPT hosting providers block SMTP - so use only HTTPS Email API as explained in this article.
* **Missing dependencies** – Always run `npm install` or `pip install` after GPT regenerates files to ensure all Mailtrap SDK dependencies are installed.
* **CORS or cross-domain errors** – If calling Mailtrap from a GPT web client, route requests through your backend to keep API token secure.

## Next steps

* Use [Mailtrap Templates](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/email-templates) to send branded GPT-generated emails with variables.
* [Add automation triggers](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-marketing/automations) in Mailtrap to send follow-ups to new contacts.
* Track open and click rates with Mailtrap Email Tracking.
