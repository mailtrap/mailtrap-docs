# Overview

Inbound Email lets you receive incoming emails, read them via API, and get webhook notifications when new messages arrive. Mailtrap accepts messages on your behalf, parses them into structured JSON.

Inbound email is most commonly used for:

* **Internal system automations** – Receive and process/categorize emails (support tickets, invoices, notifications) without running a mail server
* **Admin panels** – Display incoming emails in your own web app or admin panel
* **AI agents** – Give your  AI agent its own email address to receive and process messages
* **Agent frameworks** – You're building with OpenClaw, LangChain, CrewAI, or other agent frameworks and need email as a tool via MCP

{% embed url="https://docs.mailtrap.io/developers/inbound/" %}
Link to official API documentation
{% endembed %}

{% hint style="info" %}
The UI, as well as support for custom receiving domains, is coming soon.
{% endhint %}

### How it works

First, you need to create an inbox via the API and get an address like **app1@inbound-mailtrap.io** (for Mailtrap-hosted inbound inboxes). From there you have two options: configure a webhook to get notified on every new message, or poll the Messages API on your own schedule. Or both.

{% content-ref url="receiving-emails.md" %}
[receiving-emails.md](receiving-emails.md)
{% endcontent-ref %}

{% content-ref url="webhooks.md" %}
[webhooks.md](webhooks.md)
{% endcontent-ref %}
