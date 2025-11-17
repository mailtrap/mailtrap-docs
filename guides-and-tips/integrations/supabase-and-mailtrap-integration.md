---
title: Supabase Integration with Mailtrap
description: Learn how to integrate Mailtrap SMTP with Supabase to bypass email rate limits and send production-ready emails with comprehensive analytics.
---

With Mailtrap SMTP, you can move beyond Supabase's limit of [2 emails per hour](https://supabase.com/docs/guides/auth/rate-limits) to a production-ready [email-sending solution](https://mailtrap.io/email-sending/) with comprehensive [analytics](https://mailtrap.io/actionable-analytics/).

In this guide, I'll show you how to obtain the Mailtrap SMTP credentials and update them in Supabase.

# Overview

<i class="fa-database">:database:</i>

## Step 1: Obtain your sending credentials

If you haven't already, you'll need to verify your domain before we start. You can use our [step-by-step article](https://help.mailtrap.io/article/69-sending-domain-setup) as a guide.

With a verified domain in place:

- Go to **Sending Domains** and select your domain.

![Mailtrap Sending Domains interface showing verified domain with status indicator and Add Domain button](../.gitbook/assets/supabase-and-mailtrap-integration-1.png)

- Click on **Integration**, select **Transactional Stream**, and click **Integrate**.

![Mailtrap domain integration settings page displaying Transactional Stream and Bulk Stream options](../.gitbook/assets/supabase-and-mailtrap-integration-2.png)

- Under the **SMTP** tab, you can find your sending credentials, which include **Host**, **Port**, **Username**, and **Password**.

![Mailtrap SMTP credentials panel showing host address, port number, username, password, and authentication methods](../.gitbook/assets/supabase-and-mailtrap-integration-3.png)

## Step 2: Update the SMTP server in Supabase

- Open your Supabase [project dashboard](https://supabase.com/dashboard/projects) and select your project.

![Supabase projects dashboard displaying organization name and project card with navigation arrow](../.gitbook/assets/supabase-and-mailtrap-integration-4.png)

- Click on **Authentication** → **SMTP settings**.

![Supabase project settings page showing left sidebar with Configuration section and Authentication option highlighted](../.gitbook/assets/supabase-and-mailtrap-integration-5.png)

- Click on **Emails** → **SMTP Settings** and enable the **Enable Custom SMTP** toggle.
- Update **Host**, **Port**, **Username**, and **Password** with your Mailtrap credentials, then click **Save changes**.

![Supabase custom SMTP configuration form with Mailtrap credentials filled in all required fields](../.gitbook/assets/supabase-and-mailtrap-integration-6.png)

## Step 3: Create a new account in your app

- Open your app/project and try to create an account.

![Developer debug panel showing account creation form with email address field and password fields](../.gitbook/assets/supabase-and-mailtrap-integration-7.png)

- Alternatively, you can simulate new user registration by clicking **Add user** in Supabase.

![Supabase authentication users table displaying newly created user with email authentication method](../.gitbook/assets/supabase-and-mailtrap-integration-8.png)

## Step 4: Monitor your email performance

Once you send emails from your Supabase project, they should arrive in both your recipient's inbox and your **Mailtrap Email Logs**. There, you can see useful information such as delivery time, opens/clicks, email HTML source, [spam analysis](https://help.mailtrap.io/article/43-deliverability-tests), and more.

![Mailtrap email details page showing confirmation email delivery status with complete metadata](../.gitbook/assets/supabase-and-mailtrap-integration-9.png)

You can read more about **Mailtrap Email Logs** in our [dedicated article](https://help.mailtrap.io/article/71-email-logs).

Additionally, you'll be able to see all important stats regarding your sent emails, such as opens, clicks, bounces, and more.

![Mailtrap analytics dashboard showing email delivery statistics and performance metrics by mailbox provider](../.gitbook/assets/supabase-and-mailtrap-integration-10.png)

For more information on **Mailtrap Analytics**, [click here](https://help.mailtrap.io/article/88-statistics).