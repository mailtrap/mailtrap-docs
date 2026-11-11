# Inbound Auto-Forwarding rules

In this article, you'll learn how to set up rules that automatically forward incoming emails from your inbound inbox to one or more email addresses.

Some of the most common use cases include:

* **Support** – Forward everything sent to **support@** into your team's existing helpdesk or shared Gmail inbox.
* **Finance** – Route emails with "invoice" in a header or recipient address to the finance team's mailbox.
* **Procurement** – Route email from a specific vendor's domain (e.g., sender ends with **@vendor.com**) to procurement.
* **Compliance** – Send a copy of every inbound email to an archive or compliance mailbox.

{% hint style="info" %}
Auto-forwarding rules are currently available via API only.
{% endhint %}

#### Prerequisites

Before you start, make sure you have:

* An [inbound inbox](https://docs.mailtrap.io/inbound-email/receiving-emails).
* An [API token](https://docs.mailtrap.io/email-api-smtp/setup/api-tokens) with access to that inbox.&#x20;

### How it works

Inbound Auto-Forwarding rules let you route inbound email to the right people, while your app or AI agent keeps working with the full conversation thread via API and webhooks.&#x20;

Each rule consists of:

* **Conditions** – What an email must match to be forwarded.
* **Destinations** – The email addresses the matching emails are forwarded to.

You can match on the following:

| **match\_type** | **What it matches**                              | **Operators**                                                                      |
| --------------- | ------------------------------------------------ | ---------------------------------------------------------------------------------- |
| sender          | Who the email is from                            | `equal`, `not_equal`, `contains`, `starts_with`, `ends_with`                       |
| recipient       | The address the email was sent to (To or Cc)     | `equal`, `not_equal`, `contains`, `starts_with`, `ends_with`                       |
| header          | Any email header, by name (set with header\_key) | `equal`, `not_equal`, `contains`, `starts_with`, `ends_with`, `empty`, `not_empty` |

Forwarded emails are sent from your inbox address, so they pass DMARC on your domain. For a custom domain (catch-all) inbox, the forward is sent from the exact address the email was originally sent to.

The body and headers of the email are kept as they are. The original sender is stored in the `Original-From` and `X-Mailtrap-Original-From` headers, and the original Message-ID in the `Original-Message-ID` header.

### Step 1. Create a forwarding rule

* Get the ID of the inbox you want to forward from. You can find it with the[ List Inboxes API](https://docs.mailtrap.io/developers/inbound/inboxes/list-inboxes) endpoint.
* Define the rule's name, conditions, and destinations, and send a `POST` request.

For example, the following rule forwards emails from **@vendor.com** with "invoice" in the subject to the finance team:

```bash
curl -X POST https://mailtrap.io/api/inbound/inboxes/{inbox_id}/forward_rules \
  -H 'Authorization: Bearer YOUR_API_KEY' \
  -H 'Content-Type: application/json' \
  -d '{
    "name": "Invoices to finance dpt",
    "conditions": [
      { "match_type": "sender", "operator": "ends_with", "value": "@vendor.com" },
      { "match_type": "header", "header_key": "Subject", "operator": "contains", "value": "invoice" }
    ],
    "destinations": [
      { "email": "finance@yourcompany.com" }
    ]
  }'
```

{% hint style="info" %}
Make sure to replace `YOUR_API_KEY` with your actual Mailtrap API token and `{inbox_id}` with your inbox ID.
{% endhint %}

* Check the response. A successful request returns the created rule:

```bash
{
  "data": {
    "id": 7,
    "name": "Invoices to finance dpt",
    "created_at": "2026-11-02T07:26:58.127Z",
    "updated_at": "2026-11-02T07:26:58.127Z",
    "conditions": [
      { "match_type": "sender", "operator": "ends_with", "value": "@vendor.com", "header_key": null },
      { "match_type": "header", "operator": "contains", "value": "invoice", "header_key": "Subject" }
    ],
    "destinations": [
      { "email": "finance@yourcompany.com" }
    ]
  }
}
```

Make sure to save the `id` value (your rule ID) since you’ll need it to update or delete the rule.

* Send a test email that matches your conditions to the inbox address, and confirm it arrives at the destination.

{% hint style="info" %}
Each destination gets one delivery attempt. Failed forwards aren't retried.
{% endhint %}

### Step 2. Manage your Auto-Forwarding rules

* To **list** the rules:

```bash
curl -X GET https://mailtrap.io/api/inbound/inboxes/{inbox_id}/forward_rules \
  -H 'Authorization: Bearer YOUR_API_KEY'
```

* To **update** a rule:

```bash
curl -X PATCH https://mailtrap.io/api/inbound/inboxes/{inbox_id}/forward_rules/{id} \
  -H 'Authorization: Bearer YOUR_API_KEY' \
  -H 'Content-Type: application/json' \
  -d '{ "name": "Vendor invoices to finance" }'
```

* To **delete** a rule:

```bash
curl -X DELETE https://mailtrap.io/api/inbound/inboxes/{inbox_id}/forward_rules/{id} \
  -H 'Authorization: Bearer YOUR_API_KEY'
```

For full request and response details, see the[ Inbound API documentation](https://docs.mailtrap.io/developers/inbound/).

### Limitations

* Each inbox can have up to 5 rules, and each rule up to 5 conditions and 5 destinations.
* Conditions are combined with AND only. For "either/or" logic, create separate rules.
* Matching is plain text only and regular expressions aren't supported.
* Rules match on the sender, recipients, and headers, not on the email body.
* Rule names are required, can be at most 100 characters, and must be unique within the inbox.
* Emails that Mailtrap has already forwarded aren't forwarded again.
* A forwarded email is a new outbound send from your inbox address. Replying from the destination mailbox goes to the inbox address, unless the original email had a Reply-To header.
