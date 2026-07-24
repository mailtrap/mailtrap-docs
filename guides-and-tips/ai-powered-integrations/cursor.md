---
title: <i class="fa-code">:code:</i> Cursor and Mailtrap Integration
description: >-
  Integrate Mailtrap with the Cursor code editor to send transactional and
  promotional emails directly from your AI-powered development environment.
---

# Cursor

[Cursor](https://cursor.com/) is an AI coding platform that understands your entire codebase and lets you write, edit, and refactor code across multiple files with natural language commands.

In this guide, you’ll learn how to:

* [Integrate Mailtrap with your Cursor project](cursor.md#integrate-mailtrap-with-your-cursor-project) – Prompt the Cursor AI to connect to the Mailtrap Email API and start sending emails within minutes.
* [Add Mailtrap MCP to Cursor](cursor.md#add-mailtrap-mcp-to-cursor) – Connect and get data from your account, as opposed to UI and calling API directly.
* [Install Mailtrap Skills in Cursor](cursor.md#install-mailtrap-skills-in-cursor) – Give your Cursor AI agent context on everything Mailtrap related.

_Click on any of the links above to jump ahead to the detailed step-by-step section._

**Note**: Mailtrap offers a free, 4000 email/month Email API and SMTP plan.

### Integrate Mailtrap with your Cursor project

#### Step 1. Get your API token

You need an API token to authenticate all Mailtrap API calls — sending emails, managing domains, creating templates.

Go to [API Tokens](https://mailtrap.io/settings/api-tokens) → create a new token with **Admin** access to your account → copy the token value.

<figure><img src="../.gitbook/assets/Screenshot 2026-05-07 at 10.04.46 (1).png" alt=""><figcaption></figcaption></figure>

#### Step 2. Verify your domain

Before you start sending emails with Mailtrap, you first need to verify your domain. The process takes \~15 minutes, and you can do it manually, by following our [step-by-step guide](https://docs.mailtrap.io/email-api-smtp/setup/sending-domain) or programmatically, by prompting the Cursor AI assistant.

* Add your domain to Mailtrap

```bash
curl -X POST "https://mailtrap.io/api/accounts/{account_id}/sending_domains" \
  -H "Authorization: Bearer $MAILTRAP_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"sending_domain": {"domain_name": "yourdomain.com"}}'
```

The response will include all DNS records you need to add.

* Add DNS records at your registrar

Most domain registrars have APIs your AI assistant can use to add these records automatically. Provide your registrar's API credentials and let it handle the rest.

{% tabs %}
{% tab title="Cloudflare" %}
```bash
# Add DKIM CNAME record
curl -X POST "https://api.cloudflare.com/client/v4/zones/{zone_id}/dns_records" \
  -H "Authorization: Bearer $CLOUDFLARE_API_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "type": "CNAME",
    "name": "rwmt1._domainkey.yourdomain.com",
    "content": "rwmt1.dkim.mailtrap.io",
    "ttl": 3600,
    "proxied": false
  }'

# Add SPF TXT record
curl -X POST "https://api.cloudflare.com/client/v4/zones/{zone_id}/dns_records" \
  -H "Authorization: Bearer $CLOUDFLARE_API_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "type": "TXT",
    "name": "yourdomain.com",
    "content": "v=spf1 include:_spf.mailtrap.io ~all",
    "ttl": 3600
  }'

# Add DMARC TXT record
curl -X POST "https://api.cloudflare.com/client/v4/zones/{zone_id}/dns_records" \
  -H "Authorization: Bearer $CLOUDFLARE_API_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "type": "TXT",
    "name": "_dmarc.yourdomain.com",
    "content": "v=DMARC1; p=none;",
    "ttl": 3600
  }'
```
{% endtab %}

{% tab title="AWS Route 53" %}
```bash
aws route53 change-resource-record-sets \
  --hosted-zone-id $HOSTED_ZONE_ID \
  --change-batch '{
    "Changes": [
      {
        "Action": "UPSERT",
        "ResourceRecordSet": {
          "Name": "rwmt1._domainkey.yourdomain.com",
          "Type": "CNAME",
          "TTL": 3600,
          "ResourceRecords": [{"Value": "rwmt1.dkim.mailtrap.io"}]
        }
      },
      {
        "Action": "UPSERT",
        "ResourceRecordSet": {
          "Name": "rwmt2._domainkey.yourdomain.com",
          "Type": "CNAME",
          "TTL": 3600,
          "ResourceRecords": [{"Value": "rwmt2.dkim.mailtrap.io"}]
        }
      },
      {
        "Action": "UPSERT",
        "ResourceRecordSet": {
          "Name": "yourdomain.com",
          "Type": "TXT",
          "TTL": 3600,
          "ResourceRecords": [{"Value": "\"v=spf1 include:_spf.mailtrap.io ~all\""}]
        }
      },
      {
        "Action": "UPSERT",
        "ResourceRecordSet": {
          "Name": "_dmarc.yourdomain.com",
          "Type": "TXT",
          "TTL": 3600,
          "ResourceRecords": [{"Value": "\"v=DMARC1; p=none;\""}]
        }
      }
    ]
  }'
```
{% endtab %}

{% tab title="GoDaddy" %}
```bash
# Add DKIM CNAME record
curl -X PATCH "https://api.godaddy.com/v1/domains/yourdomain.com/records" \
  -H "Authorization: sso-key $GODADDY_API_KEY:$GODADDY_API_SECRET" \
  -H "Content-Type: application/json" \
  -d '[
    {
      "type": "CNAME",
      "name": "rwmt1._domainkey",
      "data": "rwmt1.dkim.mailtrap.io",
      "ttl": 3600
    }
  ]'
```
{% endtab %}
{% endtabs %}

* Check DNS propagation

Use `dig` to verify records have propagated before triggering verification in Mailtrap:

```bash
# Check DKIM CNAME records
dig CNAME rwmt1._domainkey.yourdomain.com +short
# Expected: rwmt1.dkim.mailtrap.io.

dig CNAME rwmt2._domainkey.yourdomain.com +short
# Expected: rwmt2.dkim.mailtrap.io.

# Check SPF TXT record
dig TXT yourdomain.com +short | grep mailtrap
# Expected: "v=spf1 include:_spf.mailtrap.io ~all"

# Check DMARC TXT record
dig TXT _dmarc.yourdomain.com +short
# Expected: "v=DMARC1; p=none;"
```

{% hint style="info" %}
DNS propagation usually takes minutes but can take up to 48 hours. If `dig` returns the expected values, records are ready. You can also click **Verify DNS Records** on your domain in [Sending Domains](https://mailtrap.io/domains) to trigger a check from Mailtrap's side.
{% endhint %}

* Check verification status via API

Poll the domain until `dns_verified` is `true`:

```bash
curl "https://mailtrap.io/api/accounts/{account_id}/sending_domains/{domain_id}" \
  -H "Authorization: Bearer $MAILTRAP_API_KEY"
```

Each record in the `dns_records` array has a `status` field: `pass`, `fail`, or `unchecked`. When all records show `pass`, your domain is verified.

{% hint style="info" %}
After DNS verification, newly added domains undergo a compliance check. Your domain's `compliance_status` will progress from `under_review` → `awaiting_questionnaire` → `compliant`. If the status stays at `awaiting_questionnaire`, check your domain details in [Sending Domains](https://mailtrap.io/domains) — you may need to click **Fill in Compliance Form** and provide additional information about your sending practices.
{% endhint %}

#### Step 3. Prompt the Cursor AI assistant

You can prompt Cursor to integrate Mailtrap into your project, have AI install the right SDK (if available), and help to write the actual sending code with a prompt like this one:

> Integrate Mailtrap into my project, so that it can send emails through the Mailtrap email API. For this, use my Mailtrap API token and sending address. Make sure to safely store my credentials in an .env file

**Important**: Don't forget to add your actual Mailtrap API token and the sending email address to the prompt.

Cursor AI will then go through the Mailtrap documentation, integrate the email API, and safely store your credentials in a **.env** file. Then, you can proceed to test the configuration. For instance, here’s our contact form email in our Gmail inbox we used as our `to` address:

<figure><img src="../.gitbook/assets/cursor new.png" alt=""><figcaption></figcaption></figure>

And here is the same email in the [Mailtrap Email Logs](https://docs.mailtrap.io/email-api-smtp/analytics/logs):

<figure><img src="../.gitbook/assets/cursor new.png" alt=""><figcaption></figcaption></figure>

### Add Mailtrap MCP to Cursor

**Note**: Before you start, make sure to install the [latest Node.js version](https://nodejs.org/en) since [Mailtrap MCP](https://www.npmjs.com/package/mcp-mailtrap) is implemented as a Node.js command line utility.

To add Mailtrap MCP to Cursor, simply [click here](https://cursor.com/en-US/install-mcp?name=mailtrap\&config=eyJlbnYiOnsiTUFJTFRSQVBfQVBJX1RPS0VOIjoieW91cl9tYWlsdHJhcF9hcGlfdG9rZW4iLCJERUZBVUxUX0ZST01fRU1BSUwiOiJ5b3VyX3NlbmRlckBleGFtcGxlLmNvbSIsIk1BSUxUUkFQX0FDQ09VTlRfSUQiOiJ5b3VyX2FjY291bnRfaWQiLCJNQUlMVFJBUF9URVNUX0lOQk9YX0lEIjoieW91cl90ZXN0X2luYm94X2lkIn0sImNvbW1hbmQiOiJucHggLXkgbWNwLW1haWx0cmFwIn0%3D) or press the quick install button on the official Mailtrap MCP page:

<figure><img src="../.gitbook/assets/cursor install.png" alt=""><figcaption></figcaption></figure>

You will then be taken to the following Cursor settings page, where you will have to insert your Mailtrap credentials:

<figure><img src="../.gitbook/assets/cursor cred.png" alt=""><figcaption></figcaption></figure>

* `MAILTRAP_API_TOKEN` – Required for all functionality, used to authenticate API requests, which you can copy/paste from the credentials tab.
* `DEFAULT_FROM_EMAIL` – Required for email sending. Make sure the email’s domain matches your own domain from the **Sending Domains** tab in Mailtrap.

You can find these credentials in your Mailtrap account by navigating to **Sending Domains** → **Integration** → **API**.

* `MAILTRAP_ACCOUNT_ID` – This is required for template management purposes. You can find the account ID under **Settings** → **Account Settings**.
* `MAILTRAP_TEST_INBOX_ID` – If you need sandbox email functionality, you can find this ID in your Sandbox.

Once you insert your Mailtrap credentials, make sure to hit the **Install** button, and you should see Mailtrap MCP installed, along with a list of available tools it comes with. Currently, Mailtrap MCP supports:

* **Sending**: send live emails
* **Sandbox**: list and preview test inbox messages
* **Email logs**: filter delivery history by sender, recipient, status, or event; view a specific log with optional raw body
* **Stats**: get delivery, bounce, open, click, and spam rates over a date range, broken down by domain, category, ESP, or date
* **Templates**: list, create, update, delete email templates
* **Sending domains**: list, create, delete domains, plus get verification status and DNS setup instructions

### Install Mailtrap Skills in Cursor

With [Mailtrap Skills](https://github.com/mailtrap/mailtrap-skills), your Cursor AI agent can get correct Mailtrap endpoints, auth patterns, and stream choices without you having to leave the editor. To install them, simply copy symlink the skill folders into the skills directory your agent reads. For example:

* **Cursor (project)**: `.cursor/skills/` in your repo, e.g. `ln -s /path/to/mailtrap-skills/skills/* .cursor/skills/`
* **Cursor (user)**: `~/.cursor/skills/` for global availability

**Note**: Mailtrap Skills are not a substitute for [docs.mailtrap.io](http://docs.mailtrap.io) or the [developer API documentation](https://docs.mailtrap.io/developers).
