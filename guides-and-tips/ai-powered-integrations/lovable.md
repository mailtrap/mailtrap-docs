---
title: <i class="fa-heart">:heart:</i> Lovable and Mailtrap Integration
description: >-
  Step-by-step guide on how to integrate Mailtrap with your Lovable application
  to send transactional emails and manage contacts.
layout:
  width: default
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
---

# Lovable

Mailtrap is an email-sending solution for developer and product teams. Focused on fast delivery and high inboxing rates for transactional and promo emails. Provides highly customizable API and 24/7 tech support.

## Overview

This integration guide demonstrates how to integrate Mailtrap with your Lovable application to enable email sending and contact management capabilities.

### Integration features

This integration is built to:

* Send emails such as transactional messages (e.g., order confirmations, notifications, etc).
* Manage contacts and push user information to Contacts so you can later send campaigns to them or use Automations.

### Important notes

* Your prompts must be adjusted to your needs.
* These prompts are created based on our experience in August 2025 with Lovable and GPT-5.
* Results may vary as Lovable and LLM models constantly evolve.

### Before we start

* Create Lovable, Mailtrap, and Supabase accounts.
  * Lovable to create contact forms and generate your logic.
  * Supabase to securely store API keys.
  * Mailtrap to send emails and manage contacts.
* Add and [verify your email sending domain](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/setup/sending-domain) since Mailtrap allows you to send emails only from a verified domain.
* Make sure your [API Token](https://mailtrap.io/api-tokens) has admin access level to that domain and contacts.
* Create [Custom fields](https://mailtrap.io/contacts/fields) in Mailtrap in advance if your form has more inputs and you want to save their content in Mailtrap. You might also need a List ID.
* Provide your Account ID as it's required for creating a contact in Mailtrap. You can find it [here](https://mailtrap.io/account-management).

### Send emails using Mailtrap Email API/SMTP

To send emails from your project, you can use a prompt like this:

* Email should be sent via Mailtrap.io, as I have an account there.
* My Mailtrap verified domain is demoatmailtrap.com
* I want to send emails from hello@demoatmailtrap.com
* Save my Mailtrap API key in `MAILTRAP_API_KEY` secret.
* Include and use Mailtrap NodeJS SDK [https://www.npmjs.com/package/mailtrap](https://www.npmjs.com/package/mailtrap) to send emails. Use the latest available version of the npm package. Its documentation:
  * Readme: [https://github.com/railsware/mailtrap-nodejs/blob/main/README.md](https://github.com/railsware/mailtrap-nodejs/blob/main/README.md)
  * Examples for implementation: [https://github.com/railsware/mailtrap-nodejs/tree/main/examples](https://github.com/railsware/mailtrap-nodejs/tree/main/examples)
  * How to send an email example: [https://github.com/railsware/mailtrap-nodejs/blob/main/examples/sending/everything.ts](https://github.com/railsware/mailtrap-nodejs/blob/main/examples/sending/everything.ts)

### Add your leads and users to Mailtrap Contacts

As you add contacts to Mailtrap, you can send Campaigns to them, manage them, create segments, and use them in Automations (e.g., welcome sequences, thank you messages, etc.).

* Create Custom fields in advance in Mailtrap.
* (Optional) List ID can be found in the URL of your List:
  * Go to your List by clicking on it.
  * You'll see all contacts in the list, and the URL will be similar to: `https://mailtrap.io/contacts?filters=%5B%7B%22name%22:%22list_id%22,%22operator%22:%22equal%22,%22value%22:%5B23%5D%7D%5D`
  * Put your URL in [https://www.urldecoder.org/](https://www.urldecoder.org/) and click Decode
  * You'll see a URL like: `https://mailtrap.io/contacts?filters=[{"name":"list_id","operator":"equal","value":[23]}]`
  * Your list ID is 23.
  * Note: You can also use the [Mailtrap List API](https://api-docs.mailtrap.io/docs/mailtrap-api-docs/1029f3edc83a2-get-all-contact-lists) to retrieve this information.

Then, feel free to use the following prompt:

* Pass all my new users/form submissions to Mailtrap contacts.
* Use the latest version of Mailtrap NodeJS SDK ([https://www.npmjs.com/package/mailtrap](https://www.npmjs.com/package/mailtrap), [https://github.com/railsware/mailtrap-nodejs/blob/main/README.md](https://github.com/railsware/mailtrap-nodejs/blob/main/README.md)) to add contacts. Here is an example: [https://github.com/railsware/mailtrap-nodejs/blob/main/examples/contacts/everything.ts](https://github.com/railsware/mailtrap-nodejs/blob/main/examples/contacts/everything.ts)
* My `MAILTRAP_ACCOUNT_ID` env variable.
* Use the same Token I use for the production mode of Mailtrap, as it can also create Contacts.
* Pass the name from my form to `name` field in Mailtrap. Add users to `MAILTRAP_LIST_ID`.
* Create `contacts` table in Supabase with such columns as:
  * `id`: UUID, primary key
  * `name`: text
  * `email`: text
  * `message`: text
  * `created_at`: timestamp
  * `mailtrap_contact_id`: text
* Apply Supabase Row-Level Security (RLS) to restrict access to only authenticated users.
* Save form contacts info from submissions in DB and use Mailtrap NodeJS SDK to create a contact in Mailtrap.
* Save Mailtrap contact\_id (Mailtrap provides it with a response) to `mailtrap_contact_id` column in `contacts` table.

## Integration example: form submissions, email notifications, and contact management

In this example, we'll use Lovable to create a demo landing page with a form to capture leads, get notifications about form submissions to your email, and add leads' info to Mailtrap Contacts so you can send them updates later.

#### Important information

* This guide is only a reference and was created to showcase Mailtrap.
* The guide is based on our own experience with Lovable. Results may vary for you.
* Do not store sensitive information in code; use Secrets instead.

{% hint style="info" %}
**Pro tip**: To avoid Supabase's hourly limits on email sending, adjust your Supabase project's SMTP settings with Mailtrap.
{% endhint %}

{% stepper %}
{% step %}
**Connect to Supabase**

Lovable uses Supabase (built-in integration) to manage authentication, database, and backend.

To connect your Lovable project to your Supabase account, click on the Supabase icon in the upper-right corner of a new project. This will open the following window, where you need to enter a project name, password, and choose the region closest to your recipients.

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/image (1).png" alt="" width="375"><figcaption></figcaption></figure></div>

After clicking on **Create new project**, Lovable will confirm that you have successfully connected your app to Supabase.

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/image (1) (1).png" alt="" width="375"><figcaption></figcaption></figure></div>

{% hint style="success" %}
For more information on integrating Supabase, follow the [official Lovable guide](https://docs.lovable.dev/integrations/supabase).
{% endhint %}
{% endstep %}

{% step %}
**Create a landing page**

The landing form we'll create will have the following functionality: each form submission will create a contact in Mailtrap, and you'll get an email notification about each submission.

We'll use a prompt like this:

Simply copy/paste the prompt in Lovable and hit enter.

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/image (2).png" alt="" width="179"><figcaption></figcaption></figure></div>

Lovable will prepare an implementation plan and show it to you. As you verify it, you can proceed with its implementation.

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/image (5).png" alt="" width="176"><figcaption></figcaption></figure></div>

Next, you need to add your credentials:

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/image (6).png" alt="" width="375"><figcaption></figcaption></figure></div>

Lastly, apply proposed changes so the database table can be created:

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/image (7).png" alt="" width="375"><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
**Send emails via form**

We got a landing page with a form, so let's test it.

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/image (8).png" alt="" width="563"><figcaption></figcaption></figure></div>

Upon submitting the form, you should see the following message, but keep in mind that it's OK if it doesn't work perfectly from the start.

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/image (9).png" alt="" width="375"><figcaption></figcaption></figure></div>

In case you do encounter any issues, check the Edge Functions log errors, pass it to Lovable, and ask it to fix them.

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/image (13).png" alt="" width="563"><figcaption></figcaption></figure></div>

After a few iterations of fixes by passing logs from the Edge Function and examples of Mailtrap NodeJS SDK, you should see the contact in your Mailtrap Contacts.

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/image (12).png" alt="" width="563"><figcaption></figcaption></figure></div>

And here it is in the Gmail inbox, which was set in `MAILTRAP_MY_EMAIL`.

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/image (11).png" alt="" width="563"><figcaption></figcaption></figure></div>

And here it is in the [Mailtrap Email Logs](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/analytics/logs).

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/image (10).png" alt="" width="563"><figcaption></figcaption></figure></div>

Note: Your Secrets in Supabase will look like:

{% code title="Supabase Secrets" %}
```
MAILTRAP_ACCOUNT_ID=1318706
MAILTRAP_API_KEY={{your-mailtrap-api-key}}
MAILTRAP_MY_EMAIL=myemails@example.com
MAILTRAP_FROM_EMAIL=form-submissions@demoatmailtrap.com
```
{% endcode %}
{% endstep %}
{% endstepper %}

## Next steps

Your Lovable application now has full email sending and contact management capabilities through Mailtrap integration. You can extend this setup by adding more sophisticated email templates, implementing contact segmentation, and creating automated email workflows.
