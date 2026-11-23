# Heroku

Add the official Mailtrap add-on to your Heroku app to test emails in Email Sandbox.

<a href="https://devcenter.heroku.com/articles/mailtrap" class="button primary">Mailtrap add-on on Heroku Dev Center</a>

### Overview

The Mailtrap add-on gives your Heroku app access to [Email Sandbox](https://docs.mailtrap.io/getting-started/email-sandbox). Sandbox catches the emails your app sends from development, staging, and QA environments, so you can inspect and debug them before they reach real recipients.

#### Prerequisites

Before we start, you'll need:

* A Heroku app
* The [Heroku CLI](https://devcenter.heroku.com/articles/heroku-cli)

### Add the Mailtrap add-on

Add the add-on to your app from the Heroku CLI:

```bash
heroku addons:create mailtrap
```

The add-on adds a `MAILTRAP_API_TOKEN` config var to your app.

### Connect your app to Email Sandbox

1. Open the Mailtrap dashboard with `heroku addons:open mailtrap`, or select **Mailtrap** under **Add-ons** in the Heroku Dashboard.
2. Go to **Sandboxes**, open your sandbox, and copy the SMTP credentials from the **Integration** tab. You can also pick your language or framework under **Code Samples** and copy the ready-made configuration.
3. Add the credentials to your app's email settings. The host is `sandbox.smtp.mailtrap.io` and the recommended port is `2525`.

For Rails and Django examples, see the [Heroku Dev Center article](https://devcenter.heroku.com/articles/mailtrap).

### Local setup

To use the same config vars locally, add them to your `.env` file:

```bash
heroku config -s | grep MAILTRAP >> .env
```

Don't commit the `.env` file to source control.

### Remove the add-on

```bash
heroku addons:destroy mailtrap
```

For add-on and runtime issues, contact [Heroku Support](https://devcenter.heroku.com/articles/support-channels). For other questions, contact our support team at **support@mailtrap.io**.
