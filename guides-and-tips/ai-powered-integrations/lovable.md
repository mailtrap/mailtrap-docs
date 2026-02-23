---
title: <i class="fa-heart">:heart:</i> Lovable and Mailtrap Integration
description: >-
  Step-by-step guide on how to integrate Mailtrap with your Lovable application
  to send transactional emails and manage contacts.
---

# Lovable

[Lovable](https://lovable.dev/) is a platform that lets you build apps and websites by chatting with AI. In this article, you’ll learn how to connect it to Mailtrap and add email-sending functionality to your projects.

**Before we start**:

* Add and [verify your email sending domain](https://help.mailtrap.io/article/69-sending-domain-setup) since Mailtrap allows you to send emails only from a verified domain.
* Create a Supabase account and a project, and [integrate it with Mailtrap](https://docs.mailtrap.io/guides/integrations/supabase/transactional-emails). The process takes \~5 minutes and lets you safely store your Mailtrap credentials.

### Step 1. Add your Mailtrap credentials

According to Lovable’s [security best practices](https://docs.lovable.dev/tips-tricks/security-best-practices#do-not-store-secrets-in-frontend-code), you shouldn’t store secrets in frontend code since it’s visible to users and can be compromised. Instead, ask Lovable to securely add your Mailtrap credentials with a prompt like this one:

> Add the Mailtrap email API token and Mailtrap From Email securely without exposing it in the frontend code

Lovable will then offer to enable [Lovable Cloud](https://docs.lovable.dev/integrations/cloud), where you can securely store your credentials without worrying about ever exposing them. To continue, click **Allow**.

<figure><img src="../.gitbook/assets/Lovable cloud.png" alt="" width="375"><figcaption></figcaption></figure>

Next, add the following two secrets:

* `MAILTRAP_API_TOKEN` – This is the [Mailtrap API token](https://docs.mailtrap.io/email-api-smtp/setup/api-tokens), which you can create at any time from your account.&#x20;
* `MAILTRAP_FROM_EMAIL` – This is the email address with the verified Mailtrap sending domain you’ve added after creating an account.

<figure><img src="../.gitbook/assets/lovable creds.png" alt="" width="375"><figcaption></figcaption></figure>

Finally, prompt Lovable to use Mailtrap email API to send emails from your project, just like so:

> From now on, please use Mailtrap email API to send emails from my project

The AI will go through [Mailtrap API documentation](https://docs.mailtrap.io/developers) and create a backend function for sending emails via Mailtrap.

### Step 2. Start sending emails

Once you connect your Lovable project to Mailtrap, you can start sending emails. If you followed everything thus far, you should receive the email in your inbox in a few seconds.

Here it is in a Gmail inbox I used as my `to` address:

<figure><img src="../.gitbook/assets/lovable email to.png" alt=""><figcaption></figcaption></figure>

And here it is in the [Mailtrap Email Logs](https://docs.mailtrap.io/email-api-smtp/analytics/logs):

<figure><img src="../.gitbook/assets/lovable email logs.png" alt=""><figcaption></figcaption></figure>

### Next steps

Your Lovable application now has full email sending and contact management capabilities through Mailtrap integration. You can extend this setup by adding more sophisticated email [templates](https://docs.mailtrap.io/email-marketing/campaigns/email-templates), managing [contacts](https://mailtrap.io/mailtrap-contacts/), and creating [automated email workflows](https://docs.mailtrap.io/email-marketing/automations).
