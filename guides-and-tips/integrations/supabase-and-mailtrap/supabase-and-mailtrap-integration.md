---
title: <i class="fa-database">:database:</i> Supabase Integration with Mailtrap
description: >-
  Learn how to integrate Mailtrap SMTP with Supabase to bypass email rate limits
  and send production-ready emails with comprehensive analytics.
---

# Supabase Transactional Emails Integration

With Mailtrap SMTP, you can move beyond Supabase's limit of [2 emails per hour](https://supabase.com/docs/guides/auth/rate-limits) to a production-ready [email-sending solution](https://mailtrap.io/email-sending/) with comprehensive [analytics](https://mailtrap.io/actionable-analytics/).

In this guide, I'll show you how to obtain the Mailtrap SMTP credentials and update them in Supabase.

{% stepper %}
{% step %}
**Obtain your sending credentials**

If you haven't already, you'll need to verify your domain before we start. You can use our [step-by-step article](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/setup/sending-domain-setup) as a guide.

With a verified domain in place:

Go to **Sending Domains** and select your domain.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/supabase-and-mailtrap-integration-1.png" alt="Mailtrap Sending Domains interface showing verified domain with status indicator and Add Domain button" width="563"></div>

Click on **Integration**, select **Transactional Stream**, and click **Integrate**.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/supabase-and-mailtrap-integration-2.png" alt="" width="375"></div>

Under the **SMTP** tab, you can find your sending credentials, which include **Host**, **Port**, **Username**, and **Password**.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/supabase-and-mailtrap-integration-3.png" alt="" width="375"></div>
{% endstep %}

{% step %}
**Update the SMTP server in Supabase**

Open your Supabase [project dashboard](https://supabase.com/dashboard/projects) and select your project.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/supabase-and-mailtrap-integration-4.png" alt="" width="375"></div>

Click on **Authentication** → **SMTP settings**.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/supabase-and-mailtrap-integration-5.png" alt="" width="563"></div>

Click on **Emails** → **SMTP Settings** and enable the **Enable Custom SMTP** toggle. Update **Host**, **Port**, **Username**, and **Password** with your Mailtrap credentials, then click **Save changes**.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/supabase-and-mailtrap-integration-6.png" alt="" width="563"></div>
{% endstep %}

{% step %}
**Create a new account in your app**

Open your app/project and try to create an account.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/supabase-and-mailtrap-integration-7.png" alt="" width="563"></div>

Alternatively, you can simulate new user registration by clicking **Add user** in Supabase.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/supabase-and-mailtrap-integration-8.png" alt="Supabase authentication users table displaying newly created user with email authentication method" width="563"></div>
{% endstep %}

{% step %}
**Monitor your email performance**

Once you send emails from your Supabase project, they should arrive in both your recipient's inbox and your **Mailtrap Email Logs**. There, you can see useful information such as delivery time, opens/clicks, email HTML source, [spam analysis](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-sandbox/deliverability-tests), and more.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/supabase-and-mailtrap-integration-9.png" alt="Mailtrap email details page showing confirmation email delivery status with complete metadata" width="563"></div>

You can read more about **Mailtrap Email Logs** in our [dedicated article](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/statistics/email-logs).

Additionally, you'll be able to see all important stats regarding your sent emails, such as opens, clicks, bounces, and more.

For more information on **Mailtrap Analytics**, [click here](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/statistics/stats-dashboard).
{% endstep %}
{% endstepper %}
