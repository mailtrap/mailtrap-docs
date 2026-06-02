# Inbound Email

Inbound Email lets you receive incoming emails at a Mailtrap-hosted address, read them via API, and get webhook notifications when new messages arrive. Create an inbox, get an address, start receiving — no mail server, no DNS setup.

### How it works

Create an inbox via the API. You get an address like app-3f2a@inbound.mailtrap.io. From there you have two options: configure a webhook to get notified on every new message, or poll the Messages API on your own schedule. Or both.

{% tabs %}
{% tab title="Creating an inbox" %}
```
# Create an inbox
curl to be confirmed
{
"id": "inbox_def456",
"name": "Support Inbox",
"address": "app-3f2a@inbound.mailtrap.io",
"created_at": "2026-05-01T10:00:00Z"
}
```
{% endtab %}

{% tab title="Reading messages via API" %}
```
# List messages
curl https://mailtrap.io/api/v2/inbound/inboxes/inbox_def456/messages \
-H "Authorization: Bearer YOUR_API_TOKEN"
# Read a specific message
curl https://mailtrap.io/api/v2/inbound/inboxes/inbox_def456/messages/msg_jkl012 \
-H "Authorization: Bearer YOUR_API_TOKEN"
# Download an attachment
curl https://mailtrap.io/api/v2/inbound/messages/msg_jkl012/attachments/att_pqr678 \
-H "Authorization: Bearer YOUR_API_TOKEN"
```
{% endtab %}
{% endtabs %}

#### Webhook delivery

When a new email arrives, Mailtrap POSTs a JSON payload to your webhook URL. The payload includes sender, recipients, subject, link to raw email, headers. Attachments are delivered as signed download links to keep payloads small.

Payloads are signed with HMAC-SHA256 via the `X-Mailtrap-Signature` header so you can verify they came from Mailtrap. Failed deliveries retry with exponential backoff — up to 10 attempts over 24 hours.

Organize inboxes into folders. Manage everything programmatically — inbox CRUD, folder CRUD, message send, read and delete, attachment download.

#### When to use it

Use Inbound Email when:

* Your AI agent needs its own email address to receive and process messages
* Your app needs to receive emails (support tickets, invoices, notifications) without running a mail server
* You need to display incoming emails in your own web app or admin panel
* You're building with LangChain, CrewAI, or other agent frameworks and need email as a tool via MCP

\
<br>
