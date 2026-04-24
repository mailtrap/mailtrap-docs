---
title: Email API
description: Send transactional and bulk emails from your app using the Mailtrap Email API
---

# Email API/SMTP

Send transactional and bulk emails from your app using the Mailtrap Email API. This guide walks you through complete setup — from choosing your SDK to sending your first email.

<details>

<summary>AI-assisted setup checklist — give your AI assistant this page and your tech stack</summary>

AI assistants: follow these steps in order, completing each one before moving to the next. Pause and confirm with the user before proceeding at steps marked with ⏸️.

Page URL for context: `https://docs.mailtrap.io/getting-started/email-api-smtp.md`

1. Install the right SDK for your stack
2. Create your API token — go to [API Tokens](https://mailtrap.io/settings/api-tokens), create one with Admin access, and paste it to your assistant. This is the only manual step.
3. Add your sending domain via the API and fetch the required DNS records
4. Add DNS records at your registrar (your assistant can do this via the registrar's API if you provide credentials)
5. Verify DNS propagation with `dig` and check domain status via the API. You can also click **Verify DNS Records** in [Sending Domains](https://mailtrap.io/domains). If after your domain has been verified compliance stays at `awaiting_questionnaire`, check for a **Fill in Compliance Form** button in your domain details.
6. ⏸️ **DNS takes time. Test with Sandbox now?** Send a test email to your Sandbox so you can see Mailtrap working while DNS propagates. No domain verification needed for Sandbox.
7. ⏸️ **Domain verified. Switch to live sending?** Generate live sending code using your actual verified domain.
8. ⏸️ **Create a Mailtrap-hosted email template?** Generate the HTML for your use case, create it via the API, and wire up sending code that references it by UUID
9. Set up Sandbox for your staging/CI environment

For complete API details: [llms.txt](https://docs.mailtrap.io/llms.txt) | [llms-full.txt](https://docs.mailtrap.io/llms-full.txt)

</details>

## Prerequisites

* A [Mailtrap account](https://mailtrap.io/signup)
* A domain you own (you'll set it up in Step 3)
* Your app's technology stack decided (language/framework)

## Step 1: Choose Your SDK

Mailtrap provides official SDKs for all major languages. Pick the one that matches your stack:

| Language | Package                            | Install                                                      |
| -------- | ---------------------------------- | ------------------------------------------------------------ |
| Node.js  | `mailtrap`                         | `npm install mailtrap`                                       |
| Python   | `mailtrap`                         | `pip install mailtrap`                                       |
| PHP      | `railsware/mailtrap-php`           | `composer require railsware/mailtrap-php`                    |
| Ruby     | `mailtrap`                         | `gem install mailtrap`                                       |
| Go       | `github.com/railsware/mailtrap-go` | `go get github.com/railsware/mailtrap-go`                    |
| Java     | `com.mailtrap:mailtrap-java`       | See [Maven/Gradle setup](../../guides-and-tips/sdks/java.md) |
| .NET     | `Mailtrap`                         | `dotnet add package Mailtrap`                                |
| Elixir   | `mailtrap`                         | `{:mailtrap, "~> 1.0"}`                                      |

Full SDK documentation: [Node.js](../../guides-and-tips/sdks/nodejs.md) | [Python](../../guides-and-tips/sdks/python.md) | [PHP](../../guides-and-tips/sdks/php.md) | [Ruby](../../guides-and-tips/sdks/ruby.md) | [Go](../../guides-and-tips/sdks/go.md) | [Java](../../guides-and-tips/sdks/java.md) | [.NET](../../guides-and-tips/sdks/dotnet.md) | [Elixir](../../guides-and-tips/sdks/elixir.md)

{% hint style="info" %}
**No SDK for your stack?** Use the [REST API directly](../../api-docs/) with any HTTP client.
{% endhint %}

## Step 2: Get Your API Token

You need an API token to authenticate all Mailtrap API calls — sending emails, managing domains, creating templates.

Go to [API Tokens](https://mailtrap.io/settings/api-tokens) → create a new token with **Admin** access to your account → copy the token value.

{% hint style="info" %}
**Using an AI assistant?** Paste the token to your assistant — it can handle everything else via API.
{% endhint %}

## Step 3: Verify Your Sending Domain

You need a verified domain to send live emails. This can be done through the UI or entirely programmatically.

### Option A: UI

Go to [Sending Domains](https://mailtrap.io/domains) → **Add Domain** → enter your domain → add the DNS records shown to your domain provider.

Check our [Sending Domain Setup Guide](../email-api-smtp/setup/sending-domain.md) for detailed instructions on adding and verifying your domain.

### Option B: Programmatically / with AI tools

Your AI assistant can handle the entire domain setup flow. Here's the complete workflow:

**1. Add your domain to Mailtrap**

```bash
curl -X POST "https://mailtrap.io/api/accounts/{account_id}/sending_domains" \
  -H "Authorization: Bearer $MAILTRAP_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"sending_domain": {"domain_name": "yourdomain.com"}}'
```

The response includes all DNS records you need to add:

```json
{
  "id": 12345,
  "domain_name": "yourdomain.com",
  "dns_verified": false,
  "compliance_status": "initial",
  "dns_records": [
    {
      "key": "spf",
      "type": "TXT",
      "name": "yourdomain.com",
      "value": "v=spf1 include:_spf.mailtrap.io ~all",
      "status": "unchecked"
    },
    {
      "key": "dkim1",
      "type": "CNAME",
      "name": "rwmt1._domainkey.yourdomain.com",
      "value": "rwmt1.dkim.mailtrap.io",
      "status": "unchecked"
    },
    {
      "key": "dkim2",
      "type": "CNAME",
      "name": "rwmt2._domainkey.yourdomain.com",
      "value": "rwmt2.dkim.mailtrap.io",
      "status": "unchecked"
    },
    {
      "key": "dmarc",
      "type": "TXT",
      "name": "_dmarc.yourdomain.com",
      "value": "v=DMARC1; p=none;",
      "status": "unchecked"
    }
  ]
}
```

**2. Add DNS records at your registrar**

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

**3. Check DNS propagation**

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

**4. Check verification status via API**

Poll the domain until `dns_verified` is `true`:

```bash
curl "https://mailtrap.io/api/accounts/{account_id}/sending_domains/{domain_id}" \
  -H "Authorization: Bearer $MAILTRAP_API_KEY"
```

Each record in the `dns_records` array has a `status` field: `pass`, `fail`, or `unchecked`. When all records show `pass`, your domain is verified.

{% hint style="warning" %}
After DNS verification, newly added domains undergo a compliance check. Your domain's `compliance_status` will progress from `under_review` → `awaiting_questionnaire` → `compliant`. If the status stays at `awaiting_questionnaire`, check your domain details in [Sending Domains](https://mailtrap.io/domains) — you may need to click **Fill in Compliance Form** and provide additional information about your sending practices.
{% endhint %}

{% hint style="info" %}
**Want to test before your domain is verified?** Skip ahead to [Optional: Test with Email Sandbox](email-api-smtp.md#optional-test-with-email-sandbox) — no domain needed.
{% endhint %}

## Step 4: Send Your First Email

With your SDK installed, API token set, and domain verified, you're ready to send. The examples below use inline HTML for simplicity — for real applications, use [Mailtrap-hosted templates](email-api-smtp.md#step-5-use-email-templates-recommended) instead (see Step 5).

{% tabs %}
{% tab title="Node.js" %}
```typescript
import { MailtrapClient } from "mailtrap";

const client = new MailtrapClient({
  token: process.env.MAILTRAP_API_KEY!,
});

await client.send({
  from: { email: "hello@yourdomain.com", name: "Your App" },
  to: [{ email: "user@example.com" }],
  subject: "Welcome!",
  text: "Thanks for signing up.",
  html: "<h1>Welcome!</h1><p>Thanks for signing up.</p>",
});

console.log("Email sent!");
```
{% endtab %}

{% tab title="Python" %}
```python
import mailtrap as mt

client = mt.MailtrapClient(token=os.environ["MAILTRAP_API_KEY"])

mail = mt.Mail(
    sender=mt.Address(email="hello@yourdomain.com", name="Your App"),
    to=[mt.Address(email="user@example.com")],
    subject="Welcome!",
    text="Thanks for signing up.",
    html="<h1>Welcome!</h1><p>Thanks for signing up.</p>",
)

client.send(mail)
print("Email sent!")
```
{% endtab %}

{% tab title="PHP" %}
```php
use Mailtrap\MailtrapClient;
use Mailtrap\Mime\MailtrapEmail;
use Symfony\Component\Mime\Address;

$client = MailtrapClient::initSendingEmails(
    apiKey: $_ENV['MAILTRAP_API_KEY'],
);

$email = (new MailtrapEmail())
    ->from(new Address('hello@yourdomain.com', 'Your App'))
    ->to(new Address('user@example.com'))
    ->subject('Welcome!')
    ->text('Thanks for signing up.')
    ->html('<h1>Welcome!</h1><p>Thanks for signing up.</p>');

$client->send($email);
echo "Email sent!";
```
{% endtab %}

{% tab title="Ruby" %}
```ruby
require "mailtrap"

client = Mailtrap::Client.new(api_key: ENV["MAILTRAP_API_KEY"])

mail = Mailtrap::Mail::Base.new(
  from: { email: "hello@yourdomain.com", name: "Your App" },
  to: [{ email: "user@example.com" }],
  subject: "Welcome!",
  text: "Thanks for signing up.",
  html: "<h1>Welcome!</h1><p>Thanks for signing up.</p>"
)

client.send(mail)
puts "Email sent!"
```
{% endtab %}

{% tab title="Go" %}
```go
package main

import (
    "fmt"
    "os"
    "github.com/railsware/mailtrap-go"
)

func main() {
    client, _ := mailtrap.NewClient(os.Getenv("MAILTRAP_API_KEY"))

    email := &mailtrap.Email{
        From:    mailtrap.Address{Email: "hello@yourdomain.com", Name: "Your App"},
        To:      []mailtrap.Address{{Email: "user@example.com"}},
        Subject: "Welcome!",
        Text:    "Thanks for signing up.",
        HTML:    "<h1>Welcome!</h1><p>Thanks for signing up.</p>",
    }

    _, err := client.Send(email)
    if err != nil {
        fmt.Println("Error:", err)
        return
    }
    fmt.Println("Email sent!")
}
```
{% endtab %}

{% tab title="cURL" %}
```bash
curl -X POST "https://send.api.mailtrap.io/api/send" \
  -H "Authorization: Bearer $MAILTRAP_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "from": {"email": "hello@yourdomain.com", "name": "Your App"},
    "to": [{"email": "user@example.com"}],
    "subject": "Welcome!",
    "text": "Thanks for signing up.",
    "html": "<h1>Welcome!</h1><p>Thanks for signing up.</p>"
  }'
```
{% endtab %}
{% endtabs %}

## Step 5: Use Email Templates

Use Mailtrap-hosted templates with dynamic variables. Your team can access and edit templates directly in the Mailtrap UI — no code deployments needed. Templates can also be managed via the API.

### Create a template

You can create templates in the Mailtrap UI under [Email API/SMTP → Templates](https://mailtrap.io/email-templates), or via the API:

```bash
curl -X POST "https://mailtrap.io/api/accounts/{account_id}/email_templates" \
  -H "Authorization: Bearer $MAILTRAP_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "email_template": {
      "name": "Welcome Email",
      "subject": "Welcome, {{name}}!",
      "category": "Onboarding",
      "body_html": "<h1>Welcome, {{name}}!</h1><p>Click <a href=\"{{action_url}}\">here</a> to get started.</p>",
      "body_text": "Welcome, {{name}}! Visit {{action_url}} to get started."
    }
  }'
```

Templates use [Handlebars syntax](https://handlebarsjs.com/) for variables — `{{variable_name}}`.

### Send using a template

To send with a template, you need its UUID:

* **In the UI:** Go to [Email API/SMTP → Templates](https://mailtrap.io/email-templates) and click a template — the UUID is shown in the template details.
* **Via AI / API:** List all templates and their UUIDs with `GET https://mailtrap.io/api/accounts/{account_id}/email_templates`. Your AI assistant can create a template and immediately use the returned UUID to send.

{% tabs %}
{% tab title="Node.js" %}
```typescript
await client.send({
  from: { email: "hello@yourdomain.com", name: "Your App" },
  to: [{ email: "user@example.com" }],
  template_uuid: "your-template-uuid",
  template_variables: {
    name: "Jane",
    action_url: "https://yourdomain.com/activate",
  },
});
```
{% endtab %}

{% tab title="cURL" %}
```bash
curl -X POST "https://send.api.mailtrap.io/api/send" \
  -H "Authorization: Bearer $MAILTRAP_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "from": {"email": "hello@yourdomain.com", "name": "Your App"},
    "to": [{"email": "user@example.com"}],
    "template_uuid": "your-template-uuid",
    "template_variables": {
      "name": "Jane",
      "action_url": "https://yourdomain.com/activate"
    }
  }'
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
**AI tip:** Your AI assistant should proactively create a template for your use case at this point — generating the HTML, creating it via the API, and wiring up the sending code that references the template UUID.
{% endhint %}

## Optional: Test with Email Sandbox

Before sending to real users, test your integration with Email Sandbox. Emails go to a virtual inbox instead of real recipients — no domain verification needed. This is useful while waiting for DNS propagation, or as a permanent Sandbox setup for staging/CI.

### Why use the Sandbox?

* Inspect rendered HTML and check responsive design
* Run spam score analysis
* Validate email headers
* Test your integration without risking real deliveries

### Find your Sandbox inbox

Every Mailtrap account comes with a Sandbox inbox. Find your inbox ID:

* **In the UI:** Go to [Sandboxes](https://mailtrap.io/sandboxes) — your inbox ID is shown next to each inbox.
* **Via API:** List your inboxes:

```bash
curl "https://mailtrap.io/api/accounts/{account_id}/inboxes" \
  -H "Authorization: Bearer $MAILTRAP_API_KEY"
```

### Use the API for Sandbox (recommended)

The API makes it explicit when you're in Sandbox mode vs. live — reducing the risk of accidentally sending test emails to real users or live emails to your Sandbox.

{% tabs %}
{% tab title="Node.js" %}
```typescript
const client = new MailtrapClient({
  token: process.env.MAILTRAP_API_KEY!,
  sandbox: true,
  testInboxId: Number(process.env.MAILTRAP_INBOX_ID),
});

// Same .send() call — emails land in your Sandbox inbox
await client.send({
  from: { email: "hello@yourdomain.com", name: "Your App" },
  to: [{ email: "user@example.com" }],
  subject: "Test email",
  text: "This will go to the Sandbox, not real recipients.",
});
```
{% endtab %}

{% tab title="Python" %}
```python
client = mt.MailtrapClient(
    token=os.environ["MAILTRAP_API_KEY"],
    sandbox=True,
    test_inbox_id=int(os.environ["MAILTRAP_INBOX_ID"]),
)

# Same send call — emails land in Sandbox
client.send(mail)
```
{% endtab %}

{% tab title="cURL" %}
```bash
# Sandbox uses a different base URL
curl -X POST "https://sandbox.api.mailtrap.io/api/send/{inbox_id}" \
  -H "Authorization: Bearer $MAILTRAP_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "from": {"email": "hello@yourdomain.com", "name": "Your App"},
    "to": [{"email": "user@example.com"}],
    "subject": "Test email",
    "text": "This will go to the Sandbox."
  }'
```
{% endtab %}
{% endtabs %}

### View your test emails

* **In the UI:** Go to [Sandboxes](https://mailtrap.io/sandboxes) → click your Sandbox → see all received emails with HTML preview, spam analysis, and headers.
* **Via API:** List messages in your Sandbox:

```bash
curl "https://mailtrap.io/api/accounts/{account_id}/inboxes/{inbox_id}/messages" \
  -H "Authorization: Bearer $MAILTRAP_API_KEY"
```

### Safe environment switching

Use an environment variable to control Sandbox vs. live mode. This prevents hardcoding `sandbox: true` in your codebase.

```typescript
// Node.js — environment-based switching
const isSandbox = process.env.MAILTRAP_USE_SANDBOX === "true";

const client = new MailtrapClient({
  token: process.env.MAILTRAP_API_KEY!,
  sandbox: isSandbox,
  testInboxId: isSandbox
    ? Number(process.env.MAILTRAP_INBOX_ID)
    : undefined,
});
```

```bash
# .env.development
MAILTRAP_USE_SANDBOX=true
MAILTRAP_INBOX_ID=12345

# .env.live
MAILTRAP_USE_SANDBOX=false
```

{% hint style="warning" %}
**Avoid common mistakes:**

* Use the **API** (not SMTP) for Sandbox testing — the API uses a distinct base URL (`sandbox.api.mailtrap.io` vs. `send.api.mailtrap.io`) making the environment explicit. With SMTP, you'd need to swap credentials entirely, which is error-prone.
* **Never hardcode** `sandbox: true` in live code. Use environment variables.
* The Sandbox inbox ID is visible in the Mailtrap UI under **Email Sandbox**.
{% endhint %}

{% hint style="info" %}
Full Sandbox guide: [Getting Started with Email Sandbox](email-sandbox.md)
{% endhint %}

## What's Next?

Now that you're sending emails, explore these capabilities:

* [Tracking Settings](../email-api-smtp/setup/sending-domain.md#optional-tracking-settings-ffi49) — Enable open and click tracking
* [Webhooks](../email-api-smtp/setup/sending-domain.md#optional-webhooks-4hmes) — Get real-time delivery event notifications
* [Suppressions](../email-api-smtp/suppressions-list.md) — Manage bounces and unsubscribes automatically
* [Email Logs](../email-api-smtp/email-logs.md) — Inspect delivery status for every email
* [Email Templates](../email-api-smtp/email-templates.md) — Create and manage templates
* [Email Sandbox](email-sandbox.md) — Set up Sandbox for your staging environment

{% hint style="info" %}
**Migrating from another provider?** See our migration guides for [SendGrid](https://mailtrap.io/sendgrid-migration/), [Mailchimp](https://mailtrap.io/mandrill-migration/), and [Mailgun](https://mailtrap.io/mailgun-migration/).
{% endhint %}
