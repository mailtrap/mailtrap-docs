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
* **Replies in-thread with one API call** – Mailtrap handles the headers and sender address; your agent just sends the body.

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
  "id": "msg_01HZX...",
  "inbox": "support-bot",
  "from": { "name": "Sarah Chen", "email": "sarah@acme.co" },
  "to":   [{ "email": "support-bot@inboundly.dev" }],
  "subject": "Need help with our last invoice",
  "received_at": "2026-05-27T10:42:11Z",
  "text": "Hey team, we were charged twice...",
  "html": "<p>Hey team,</p>...",
  "attachments": [
    { "filename": "invoice-4821.png",
      "size": 188416,
      "content_type": "image/png",
      "url": "https://cdn.inboundly.dev/..." }
  ],
  "spam_score": 0.04,
  "spf": "pass",
  "dkim": "pass",
  "thread_id": "thr_8Pz..."
}
```

#### Endpoints

| `GET /inbound/folders`               | Group inboxes by agent, project, or workflow |
| ------------------------------------ | -------------------------------------------- |
| `POST /inbound/folders/{id}/inboxes` | Create a hosted or custom-domain inbox       |
| `GET /inbound/inboxes/{id}/messages` | List, search, and fetch parsed messages      |
| `POST /api/webhooks`                 | Register a webhook; reply in-thread          |

### Use cases

Once an inbox is wired up, teams typically build:

* **AI support agent** – Receive support emails, create tickets, draft replies.
* **Invoice processing** – Extract attached PDFs and trigger accounting workflows.
* **AI receptionist** – Read appointment requests and schedule meetings.
* **GitHub automation** – Convert alert emails into issues and tasks.
* **Human-in-the-loop review** – Route emails to an agent first, escalate to a human when needed.
* **Workflow automation** – Trigger n8n, Make, or custom pipelines from incoming mail.
