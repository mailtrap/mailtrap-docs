---
description: >-
  Learn how to integrate Mailtrap SMTP with Supabase to bypass email rate limits
  and send production-ready emails with comprehensive analytics.
---

# Supabase Transactional Emails Integration

With Mailtrap SMTP, you can move beyond Supabase's limit of [2 emails per hour](https://supabase.com/docs/guides/auth/rate-limits) to a production-ready [email-sending solution](https://mailtrap.io/email-sending/) with comprehensive [analytics](https://mailtrap.io/actionable-analytics/).

Mailtrap’s native integration with Supabase streamlines your workflow by automatically populating your Supabase project with Mailtrap’s SMTP credentials. You can access this setup via the Integrations page in Mailtrap or through the [Supabase Marketplace](https://supabase.com/docs/guides/integrations/supabase-marketplace).

{% hint style="info" %}
Currently, this integration supports Sending Domains (API/SMTP) only and does not include Email Sandbox configuration. If you would like to see Sandbox support in the future, please [leave a feature request here](https://feedback.mailtrap.io/).
{% endhint %}

#### Prerequisites:

* **Admin rights** for your Mailtrap account.
* A [**verified sending domain**](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/setup/sending-domain) set up within Mailtrap.
* An existing **Supabase account** with an active project.

#### Use cases:

* **Supabase Auth**: Managing email confirmations, magic links, and password resets.
* **Database Events**: Triggering transactional emails based on database changes.
* **User Interaction**: Powering contact forms or "Send Message" features.

{% hint style="info" %}
Sending automated emails via Supabase Edge Functions is not covered by this integration. Please refer to our [dedicated guide for Edge Functions](https://mailtrap.io/blog/supabase-send-email/#Configure-Supabase-Edge-Functions-and-Database-Webhooks).
{% endhint %}

### Step-by-step integration guide

{% stepper %}
{% step %}
**Initiate the integration**

* Log in to your Mailtrap account.
* Navigate to the [**Integrations** page](https://mailtrap.io/integrations) from the sidebar.
* Scroll to the **AI & Development** section (or search for "Supabase") and locate the **Supabase** card.
* Click the **Integrate** button.

<figure><img src="../../.gitbook/assets/Screenshot 2025-12-18 at 12.49.46.png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
**Authorize access**

* On the setup screen, click **Connect Supabase**.

<figure><img src="../../.gitbook/assets/Screenshot 2025-12-18 at 12.50.24.png" alt=""><figcaption></figcaption></figure>

* Review the permissions for the access of your Supabase organizations and projects, and click **Authorize Mailtrap**.

<figure><img src="../../.gitbook/assets/Screenshot 2025-12-18 at 13.08.34.png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
**Write** and **Read** access is required to update configurations. Moreover, you can revoke the authorization at any time.
{% endhint %}
{% endstep %}

{% step %}
**Select your project**

Once authorized, Mailtrap will load your available Supabase projects. Then, all you need to do is:

* Click the **Select a Supabase project** dropdown menu
* Choose the specific project you wish to integrate (e.g., Test Integration).

<figure><img src="../../.gitbook/assets/Screenshot 2025-12-18 at 13.12.29.png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
**Create an API Token**

* In the **Create an API token** section, use the dropdown menu to select the Mailtrap Domain you want to use for sending emails.
* Click **Create Token**.

<figure><img src="../../.gitbook/assets/Screenshot 2025-12-18 at 13.15.57.png" alt=""><figcaption></figcaption></figure>


{% endstep %}

{% step %}
**Configure sender details**

Define who the emails will appear to be coming from.

* Sender name: The name you want displayed in the recipient's inbox (e.g., Julia or Support Team).
* Sender email: The local part of the email address (e.g., enter noreply to create noreply@your-domain.com).
* Mailtrap will generate a preview of the SMTP settings (Host, Port, Username, etc.).
* Click Configure SMTP to finish the process.

You will see a confirmation message stating: "_Successfully configured Supabase SMTP_."

<figure><img src="../../.gitbook/assets/Screenshot 2025-12-18 at 13.18.09.png" alt=""><figcaption></figcaption></figure>
{% endstep %}
{% endstepper %}

### Manual integration

You can also integrate Mailtrap SMTP with Supabase manually.&#x20;

{% stepper %}
{% step %}
**Obtain your sending credentials**

* Go to **Sending Domains** and select your domain.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/supabase-and-mailtrap-integration-1.png" alt="" width="563"></div>

* Click on **Integration**, select **Transactional Stream**, and click **Integrate**.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/supabase-and-mailtrap-integration-2.png" alt="" width="375"></div>

* Under the **SMTP** tab, you can find your sending credentials, which include **Host**, **Port**, **Username**, and **Password**.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/supabase-and-mailtrap-integration-3.png" alt="" width="375"></div>
{% endstep %}

{% step %}
**Update the SMTP server in Supabase**

* Open your Supabase [project dashboard](https://supabase.com/dashboard/projects) and select your project.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/supabase-and-mailtrap-integration-4.png" alt="" width="375"></div>

* Click on **Authentication** → **SMTP settings**.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/supabase-and-mailtrap-integration-5.png" alt="" width="563"></div>

* Click on **Emails** → **SMTP Settings** and enable the **Enable Custom SMTP** toggle. Update **Host**, **Port**, **Username**, and **Password** with your Mailtrap credentials, then click **Save changes**.
* Update the **Sender details** and **SMTP provider settings** like in the screenshot below, and hit **Save changes**.

<figure><img src="../../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

### **Monitor your email performance**

Once you send emails from your Supabase project, they should arrive in both your recipient's inbox and your **Mailtrap Email Logs**. There, you can see useful information such as delivery time, opens/clicks, email HTML source, [spam analysis](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-sandbox/deliverability-tests), and more.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/supabase-and-mailtrap-integration-9.png" alt="" width="563"></div>

You can read more about **Mailtrap Email Logs** in our [dedicated article](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/analytics/logs).

Additionally, you'll be able to see all important stats regarding your sent emails, such as opens, clicks, bounces, and more.

For more information on **Mailtrap Analytics**, [click here](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/analytics/dashboard).
{% endstep %}
{% endstepper %}
