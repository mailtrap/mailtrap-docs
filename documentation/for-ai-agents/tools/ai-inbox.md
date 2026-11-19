# AI inbox

With Mailtrap, you can give your AI agent its own inbox so that every inbound email lands as structured JSON over a webhook, ready to parse and reply to in one API call.

**Useful links**:

* [Receiving emails tutorial](https://docs.mailtrap.io/inbound-email/receiving-emails)
* [Official API documentation](https://docs.mailtrap.io/developers/inbound/folders)

### How an agent inbox works

Mailtrap's inbound email infrastructure is built for AI agents, assistants, and automated workflows. Instead of handing your agent an OAuth token into a personal Gmail account, you create a dedicated, isolated inbox through the API (hosted or on your own domain) and your agent receives, reads, and replies to real email without a mail server to operate.

In summary, an agent inbox:

* **Turns raw email into clean JSON** – Sender, recipients, subject, headers, plain text, HTML body, and attachment download URLs, all in one structured object. No MIME parsing, no header extraction to write yourself.
* **Notifies your agent in real time** – A webhook fires the moment mail arrives, carrying the event ID and key metadata; your agent fetches the full parsed message from the Messages API. No polling.
* **Threads conversations automatically** – Replies are grouped into a single conversation, so your agent pulls the whole back-and-forth instead of stitching messages together itself.
* **Keeps attachments out of your context window** – Files arrive as URLs on the parsed message, so your agent fetches only what it actually needs.
* **Replies in-thread with one API call** – Mailtrap handles the threading headers and, for hosted inboxes, the sender address. On a custom-domain inbox, your agent sets `from` to an address on that domain.

### Quick setup

1. Create a folder to group inboxes by agent, project, or workflow.
2. Create an inbox inside that folder; hosted (no DNS, no MX records) or on your own custom domain.
3. Register a webhook URL. Mailtrap posts to it the moment a new message lands.
4. On webhook receipt, call the Messages API to fetch the fully parsed email.
5. Reply in-thread with a single API call when your agent is ready to respond.

```bash
curl -X GET https://mailtrap.io/api/inbound/folders \
  -H 'Authorization: Bearer YOUR_API_KEY'
```

{% hint style="info" %}
Start on a hosted address to prototype immediately. When you're ready for production, connect your own domain through the same API and webhook flow.
{% endhint %}

#### Example parsed message

```json
{
  "id": "1866872391602282496",
  "inbox_id": 15,
  "from": "Sarah Chen <sarah@acme.co>",
  "to": ["support-bot-62fedace@inbound-mailtrap.io"],
  "cc": [],
  "bcc": [],
  "reply_to": null,
  "subject": "Need help with our last invoice",
  "headers": { "mime-version": "1.0" },
  "size": 190000,
  "html_size": 512,
  "text_size": 120,
  "received_at": "2026-05-27T10:42:11Z",
  "rfc_message_id": "CAF2xY8kq3@mail.acme.co",
  "in_reply_to": null,
  "references": [],
  "thread_id": "1866872391602282497",
  "attachments": [
    {
      "attachment_id": "a1b2c3d4",
      "size": 188416,
      "filename": "invoice-4821.png",
      "content_type": "image/png",
      "content_disposition": "attachment",
      "content_id": null,
      "download_url": "https://...",
      "download_url_expires_at": "2026-05-27T11:42:11Z"
    }
  ],
  "forwards": [],
  "raw_message_url": "https://...",
  "raw_message_expires_at": "2026-05-27T11:42:11Z",
  "html_body": "<p>Hey team,</p>...",
  "text_body": "Hey team, we were charged twice..."
}
```

#### Endpoints

| `GET /api/inbound/folders`                                  | Group inboxes by agent, project, or workflow |
| ----------------------------------------------------------- | -------------------------------------------- |
| `POST /api/inbound/folders/{folder_id}/inboxes`             | Create a hosted or custom-domain inbox       |
| `GET /api/inbound/inboxes/{inbox_id}/messages`              | List and fetch parsed messages               |
| `POST /api/webhooks`                                        | Register an `inbound_receiving` webhook      |
| `POST /api/inbound/inboxes/{inbox_id}/messages/{id}/reply`  | Reply in-thread                              |

### Use cases

Once an inbox is wired up, teams typically build:

* **AI support agent** – Receive support emails, create tickets, draft replies.
* **Invoice processing** – Extract attached PDFs and trigger accounting workflows.
* **AI receptionist** – Read appointment requests and schedule meetings.
* **GitHub automation** – Convert alert emails into issues and tasks.
* **Human-in-the-loop review** – Route emails to an agent first, escalate to a human when needed.
* **Workflow automation** – Trigger n8n, Make, or custom pipelines from incoming mail.
