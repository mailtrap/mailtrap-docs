---
cover: ../.gitbook/assets/post-smtp-cover.png
coverY: 0
---

# Post SMTP

Integrate Mailtrap with your WordPress site using the Post SMTP plugin to send and test emails through the Mailtrap API or SMTP.

### Overview

Post SMTP is a WordPress plugin that sends your site's emails through an email provider instead of the default WordPress mail function. You can connect it to Mailtrap in two ways:

* **Mailtrap API integration**: Post SMTP's built-in Mailtrap mailer sends through the Mailtrap Email API with your API token.
* **SMTP integration**: Post SMTP's Other SMTP mailer with your Mailtrap SMTP credentials.

#### Prerequisites

Before we start, you'll need to:

* [Verify your sending domain](https://docs.mailtrap.io/general/sending-domain)
* [Create and save an API token](https://docs.mailtrap.io/general/api-tokens)
* Install and activate [Post SMTP](https://wordpress.org/plugins/post-smtp/) on your WordPress site

{% hint style="info" %}
Post SMTP requires WordPress 5.6 or later and PHP 7.1 or later.
{% endhint %}

### Email Live Sending with Post SMTP

#### Mailtrap API integration

The Mailtrap mailer is available in Post SMTP 3.7.0 and later. It sends through the Transactional Stream over HTTPS, so it works even if your hosting provider blocks SMTP ports.

1. In your WordPress dashboard, go to **Post SMTP** and click **Setup the wizard**. If Post SMTP is already configured, click **Relaunch the wizard**.
2. Choose **Mailtrap** and click **Continue**.
3. Fill in the sender details:
   * **From Email**: an address on your verified sending domain, for example `hello@yourdomain.com`.
   * **From Name**: the sender name your recipients see.
   * Turn on **Force From Email** and **Force From Name** so other plugins and themes can't change them.
4. Paste your API token into the **API Token** field and click **Save and Continue**.
5. Enter a **Recipient Email Address**, click **Send Test Email**, and then click **Finish**.

The test email appears in your [Email Logs](https://docs.mailtrap.io/email-live-sending/analytics/logs) as soon as it's sent. Post SMTP also keeps its own log under **Post SMTP** → **Email Log**.

{% hint style="info" %}
The Mailtrap mailer supports only the Transactional Stream. To send through the Bulk Stream or to Email Sandbox, use SMTP integration.
{% endhint %}

#### SMTP integration

You can also send with Post SMTP's Other SMTP mailer. To get your credentials:

1. Go to the [Sending Setup](https://mailtrap.io/api-smtp/sending-setup) page under **Live Sending** and choose your domain.
2. Select the Transactional or Bulk Stream.
3. Toggle the switch to **SMTP** and copy the credentials.

Then set up Post SMTP:

1. Go to **Post SMTP** and start the setup wizard.
2. Choose **Other SMTP** and click **Continue**.
3. Fill in **From Email** and **From Name** with an address on your verified sending domain.
4. Enter your SMTP credentials and click **Save and Continue**:

| Field     | Value                   |
| --------- | ----------------------- |
| Host Name | `live.smtp.mailtrap.io` |
| Port      | `587`                   |
| Username  | `api`                   |
| Password  | Your API token          |

5. Send a test email and click **Finish**.

For the Bulk Stream, use `bulk.smtp.mailtrap.io` with the Bulk Stream credentials. Mailtrap SMTP supports ports 587 (recommended), 2525, 25, and 465. Post SMTP sets the encryption from the port: SSL for port 465 and STARTTLS for the others.

To change these settings later, go to **Post SMTP** → **Settings** → **Connections**. Read more in the [SMTP integration guide](https://docs.mailtrap.io/email-live-sending/setup/smtp-integration).

### Email Sandbox with Post SMTP

[Email Sandbox](https://docs.mailtrap.io/getting-started/email-sandbox) catches every email your WordPress site sends, so you can inspect it without reaching real recipients. You don't need a verified domain to use it.

The Mailtrap mailer doesn't support Email Sandbox, so use the Other SMTP mailer:

1. In Mailtrap, go to **Sandboxes**, open your sandbox, and copy the credentials from the **Integration** tab.
2. In WordPress, go to **Post SMTP**, start the setup wizard, choose **Other SMTP**, and click **Continue**.
3. Fill in **From Email** and **From Name**.
4. Enter your Sandbox credentials and click **Save and Continue**:

| Field     | Value                      |
| --------- | -------------------------- |
| Host Name | `sandbox.smtp.mailtrap.io` |
| Port      | `2525`                     |
| Username  | Your sandbox username      |
| Password  | Your sandbox password      |

5. Send a test email and click **Finish**. The email appears in your sandbox.

Each sandbox has its own username and password. Read more in the [Sandbox SMTP integration guide](https://docs.mailtrap.io/email-sandbox/setup/sandbox-smtp-integration).

#### Switch from Sandbox to live sending

When you're ready to send to real recipients, relaunch the setup wizard and choose one of these:

* **Mailtrap**: the Mailtrap mailer with your API token.
* **Other SMTP**: your Email Live Sending SMTP credentials instead of the Sandbox credentials.

Use Sandbox on your development and staging sites, and live sending on your production site.

#### Troubleshooting

* **"Sending from domain is not allowed" error**

The sender address doesn't use a verified sending domain. Make sure **From Email** uses your verified domain, and turn on **Force From Email** so other plugins can't change it. See [Domain not allowed](https://docs.mailtrap.io/email-live-sending/troubleshooting/sending-from-domain-not-allowed) for more fixes.

* **401 Unauthorized error**

The API token is wrong, expired, or has no access to your sending domain. New tokens expire after 365 days by default. See [Unauthorized (401) error](https://docs.mailtrap.io/email-live-sending/troubleshooting/unauthorized-401-error) for more fixes.

* **SMTP connection fails**

Your hosting provider may block the SMTP port. Try port 2525, or switch to the Mailtrap mailer, which sends over HTTPS instead of SMTP.

* **Emails appear in the Post SMTP log but aren't sent**

Check **Delivery Mode** under **Post SMTP** → **Settings** → **Advanced**. It must be set to **Log Email and Send**.

If you need help with your Post SMTP integration, contact our support team at **support@mailtrap.io**.
