# Managing Inbound Emails in the UI

In this article, you'll learn how to create and manage inbound inboxes, view email threads, set up webhooks, and configure auto-forwarding rules directly from the Mailtrap web interface.

While all Inbound Email features are available via the [Inbound API](https://docs.mailtrap.io/developers/inbound/inboxes), the Mailtrap UI provides a visual workspace to organize inboxes, view incoming messages and attachments, reply or forward in-thread, monitor delivery statuses, and create auto-forwarding rules.

### How it works

Each inbox has its own address, which can be:

* **Mailtrap-hosted** – A generated address under `@inbound-mailtrap.io`. No DNS setup is needed.
* **Custom domain** – Receives email sent to any address under your domain (`*@your-domain.com`), once the domain’s MX record points to Mailtrap.

When an email arrives, Mailtrap accepts it on your behalf, parses it into structured JSON, and groups it with related messages into a thread. From there, you can:

* **View and act on it in the UI** – Open the thread, preview attachments, and reply or forward from the inbox address.
* **Get notified by webhook** – Have your app or AI agent notified the moment a new email arrives.
* **Forward it automatically** – Send matching emails to other addresses with auto-forwarding rules.

#### Step 1. Create an inbound inbox

* Navigate to the **Inbound** tab and click **Create Your First Inbox**.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/Pasted image 2026-11-25 07.08.29.png" alt="" height="349" width="624"></div>

* Enter an **Inbox name**, choose the **Domain**, and hit **Create**:

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/Pasted image 2026-11-25 07.08.35.png" alt="" height="349" width="624"></div>

* **Mailtrap-hosted (inbound-mailtrap.io)**: Generates an instant address (for example, `test-demo-5-526ee427@inbound-mailtrap.io`) with no DNS setup required.

{% hint style="info" %}
Mailtrap-hosted inboxes (`@inbound-mailtrap.io`) have a lifetime limit of 20 replies per inbox, and this limit does not reset. To send unlimited replies or use custom aliases like `support@` or `invoices@`, use a custom domain.
{% endhint %}

* **Custom domain (catch-all)**: Select one of your verified sending domains or subdomains to receive emails sent to any address under that domain (`*@your-domain.com`).

The first inbox you create will be automatically placed inside a new folder. Folders help you categorize and group inbound inboxes by project, team, or workflow (similar to [Sandbox projects](https://mailtrap.io/sandboxes/projects)).&#x20;

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/Pasted image 2026-11-25 07.08.38.png" alt="" height="103" width="624"></div>

If you open an inbox, you can see the:

1. The inbox where emails you receive will show up
2. Automatically generated inbound inbox address
3. Tools you can connect it with (e.g., Mailtrap CLI, MCP, Zapier, n8n, etc.)
4. Code samples you can use to add inbound functionality to your app

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/Pasted image 2026-11-25 07.08.40.png" alt="" height="348" width="624"></div>

#### Step 2. View, reply, and forward messages

When you receive an email in your inbound inbox, you can:

* Use the toolbar on any message to **Reply**, **Forward**, **Download** the raw message, or **Delete** it.
* **Preview or download incoming files**, (such as PDFs or images) which appear directly inside the message pane.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/Pasted image 2026-11-25 07.08.46.png" alt="" height="203" width="624"></div>

* **Replies and forwards** belonging to the same conversation are automatically grouped into a single thread with a message counter.
* **Real-time delivery badges** (such as **Delivered** or **Bounced**) are also displayed.&#x20;

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/Pasted image 2026-11-25 07.08.49.png" alt="" height="203" width="624"></div>

* If you click the status link, you will jump straight to **Email Logs** for full event details and headers.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/Pasted image 2026-11-25 07.08.52.png" alt="" height="235" width="624"></div>

#### Step 3. Set up webhooks

Webhooks notify your application or AI agent the moment a new email arrives.

* Open your inbound inbox, go to the **Webhooks** tab and hit **Set Up in Webhooks**.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/Pasted image 2026-11-25 07.08.58.png" alt="" height="235" width="624"></div>

You will be taken to the **Webhooks** configuration page with **Inbound Inboxes** and your specific inbox pre-selected.

* Paste your destination **Webhook URL** and click **Save**.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/Pasted image 2026-11-25 07.09.00.png" alt="" height="349" width="624"></div>

Once you receive a message in your Inbound Inbox, you should see the following output from your webhook:

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/Pasted image 2026-11-25 07.09.06.png" alt="" height="252" width="624"></div>

**Note**: Webhook payloads contain event metadata only (such as `event`, `message_id`, `inbox_id`, `from`, and `timestamp`). To retrieve the full parsed email body or attachments, fetch the message using the **Messages API** (`GET /api/inbound/inboxes/{inbox_id}/messages/{id}`) or view it in the UI.

### Step 4. Configure Forward rules

**Inbound Auto-Forwarding rules** automatically route matching emails to external addresses (for example, forwarding `support@` to your helpdesk or `invoices@` to your accounting team) while preserving the full thread in Mailtrap.

* Open your inbox, select the **Forward Rules** tab, and click **Create Rule**.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/Pasted image 2026-11-25 07.09.09.png" alt="" height="211" width="624"></div>

* Enter a unique rule **Name**, and click **Create**.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/Pasted image 2026-11-25 07.09.11.png" alt="" height="257" width="624"></div>

* Under Conditions, define what incoming messages must match:

| **Field**     | **What it matches**                                                                 | **Available operators**                                                            |
| ------------- | ----------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| **Sender**    | The sender's email address (`From`)                                                 | `equal`, `not_equal`, `contains`, `starts_with`, `ends_with`                       |
| **Recipient** | The recipient address (`To` or `Cc`) – ideal for catch-all custom domains           | `equal`, `not_equal`, `contains`, `starts_with`, `ends_with`                       |
| **Header**    | Any email header specified by Header Key (e.g., `Subject` or custom system headers) | `equal`, `not_equal`, `contains`, `starts_with`, `ends_with`, `empty`, `not_empty` |

* Under **Destination**, enter one or more recipient email addresses, and click **Save**.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/Pasted image 2026-11-25 07.09.14.png" alt=""></div>

Once you create an Auto-Forwarding rule, you can see it under the **Forward Rules** tab.&#x20;

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/Pasted image 2026-11-25 07.09.16.png" alt="" height="191" width="624"></div>

And when an incoming email triggers a rule, Mailtrap displays a **1 rule triggered** banner on the message. Click **View Details** to see which rule matched, check its delivery status, or inspect the forwarded message in **Email Logs**.

<div data-with-frame="true"><img src="../.gitbook/assets/Pasted image 2026-11-25 07.09.19.png" alt=""></div>

### Enabling inbound receiving on a custom domain

If you select a custom domain that hasn't been configured for inbound traffic yet, you'll see a prompt stating that the inbox isn't receiving emails yet.&#x20;

<div data-with-frame="true"><img src="../.gitbook/assets/Pasted image 2026-11-25 07.09.22.png" alt=""></div>

To enable the receiving on the domain:

* Click **View Domain Settings** (or go to **Sending Domains** in the left menu and select your domain).

<div data-with-frame="true"><img src="../.gitbook/assets/Pasted image 2026-11-25 07.09.24.png" alt=""></div>

* Open the **Domain Verification** tab.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/Pasted image 2026-11-25 07.09.27.png" alt=""></div>

* Toggle **Inbound domain receiving** to **ON**.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/Pasted image 2026-11-25 07.09.29.png" alt=""></div>

* Add the displayed **MX record** (`10 inbound.smtp.mailtrap.io`) to your domain provider's DNS settings and click **Verify DNS records**.

Once verified, any message sent to any username at that domain (such as `support@your-domain.com` or `billing@your-domain.com`) routes into your catch-all inbox.

### Limits, retention, and billing

* **Message retention**: Inbound emails follow the same retention period as your **Email Logs** based on your current Mailtrap plan (for example, 30 days). Messages are not stored indefinitely.
* **Plan quota usage**: All incoming emails, in-thread replies, manual forwards, and triggered auto-forwards count toward your monthly **Email Live Sending** (API/SMTP) plan quota.
* **Auto-forwarding limits**: You can create **up to 5 rules per inbox**, with **up to 5 condition**s (combined using `AND` logic) and **5 destinations per rule**. Regex matching and email body filtering are not supported.
