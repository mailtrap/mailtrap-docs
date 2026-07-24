# BuildAI

[BuildAI.Space](https://www.buildai.space/) is a no-code platform for building AI-powered apps and Digital Employees.

This article shows you how to connect Mailtrap’s email API to your BuildAI AI-powered apps using BuildAI’s Custom Integration feature. The same integration can also be used inside AI-powered apps and workflows. No code required

**Note**: Mailtrap offers a free, 4000 email/month Email API and SMTP plan.

#### Prerequisties

* A BuildAI account with access to the Custom Integration feature
* A Mailtrap account with a verified sending domain - the email address in the `from` field must match a domain you own and have verified in Mailtrap.

#### Step 1. Get your Mailtrap API token

Mailtrap authenticates API requests using tokens. You’ll add this token to your BuildAI integration so every email send is authorized by your account.

* Log in to [Mailtrap](https://mailtrap.io).
* Go to **API Tokens** under **Settings**.
* Click **Add Token**, give it a name (e.g. `BuildAI Integration`), and set the scope to **Admin**.

<figure><img src="../.gitbook/assets/Screenshot 2026-07-15 at 18.40.02.png" alt=""><figcaption></figcaption></figure>

* Save and copy the token, you’ll enter it in Step 3.

{% hint style="info" %}
Your token is a password. Anyone who has it can send email from your account. Don’t share it, paste it into a public form field, or commit it to a repository. In Step 3 we’ll cover how to store it securely inside BuildAI.
{% endhint %}

#### Step 2. Confirm your sending domain

Before testing the integration, make sure the `from` address you’ll use is on a domain verified in Mailtrap. Sending from an unverified domain will fail.

* In Mailtrap, navigate to **Sending Domains**.
* Confirm the domain you’ll send from shows a **Verified** status.

<figure><img src="../.gitbook/assets/buildai 2.png" alt=""><figcaption></figcaption></figure>

* Note the sender address you’ll use (e.g. `hello@yourdomain.com`) - you’ll enter it in the API body in Step 4.

If your domain isn’t verified yet, follow [Mailtrap’s domain verification guide](https://docs.mailtrap.io/getting-started/email-api-smtp) before continuing.

#### Step 3. Open Custom Integrations in your BuildAI app

* Log in to [BuildAI](https://buildai.space) and open the app you want to add email to.
* Find the **Integrations** section; it’s in top right.
* Select **Custom Integration** under **Connect to any API**.

<figure><img src="../.gitbook/assets/buildai 3.png" alt=""><figcaption></figcaption></figure>

* Click to create a new custom integration.

#### Step 4. Configure the API connection

Fill in the Custom Integration form in plain language, you’ll later be asked to safely add credentials:

<figure><img src="../.gitbook/assets/buildai 4.png" alt="" width="375"><figcaption></figcaption></figure>

To help you complete the process, here are the defaults:

* Mailtrap - an email delivery platform
* Send a welcome email when my users fill out a form (or add your specific use case)
* (select answers verbatim) I have an API key
* (select answers verbatim) I have some API documentation
* Documentation can be found at: (use link)> [Mailtrap API docs](https://docs.mailtrap.io/developers?_gl=1*3ei5qp*_gcl_au*NzA4MzIzODUyLjE3NzkxODMwMDA.)&#x20;

Once done, hit ‘**Create App with**…’ button to proceed.

**Important note**: If you have an existing project or app, you’d like to use, make sure to specify the app name and email integration logic under ‘Specifically, I want to:’

#### Step 5. Store your API token securely

In the BuildAI chat flow, select **Set** S**ecrets**.

<div align="center"><figure><img src="../.gitbook/assets/buildai 5.png" alt="" width="375"><figcaption></figcaption></figure></div>

Add the **Mailtrap API Key** you previously generated and the **Mailtrap Sender Email**:

<figure><img src="../.gitbook/assets/buildai 6.png" alt="" width="375"><figcaption></figcaption></figure>

Hit **Save Secrets** to confirm, and your token is now stored in one place. If you ever rotate the token in Mailtrap, you update it once in BuildAI’s variable store and every integration that references it stays current.

#### Step 6. Inspect the integration and secrets

Once BuildAI completes Mailtrap integration, it asks you to navigate to **Settings** → **Secrets** to confirm your Secrets are where they’re supposed to be. Take this step before moving forward to ensure nothing’s broken.

<figure><img src="../.gitbook/assets/buildai 7.png" alt=""><figcaption></figcaption></figure>

Click **Save Secrets**, and move on to the next step.&#x20;

#### Step 7. Test the integration

Before publishing, confirm the full flow works end to end.

* Use BuildAI’s **Test** or **Preview** mode to run the app.
* Submit the form with a real email address you can check.

<figure><img src="../.gitbook/assets/buildai 8.png" alt=""><figcaption></figcaption></figure>

* In Mailtrap, open **Email Logs** and verify the message was delivered - check the recipient, sender, and subject line.

<figure><img src="../.gitbook/assets/buildai 9.png" alt=""><figcaption></figcaption></figure>

If the request fails, check the API response code in BuildAI’s integration logs. Common fixes:

* **401 Unauthorized** - token is wrong or missing the `Bearer` prefix in the Authorization header
* **422 Unprocessable Entity** - a required field is missing or malformed in the JSON body (check for missing quotes or commas)
* **Sender domain error** - the `from.email` address is on a domain that isn’t verified in Mailtrap

**Troubleshooting tips**:

* When you encounter bugs, use BuildAI’s button Resolve with AI. Note that it may take a couple of runs before the system figures out the fixes (particularly with 500 errors).&#x20;
* When you use Connect to Any API feature, you might need to add the Secrets a few times; even if you followed all the steps and saved the secrets. This depends on your app logic and the trigger flow (handled but BuildAI itself). But after a bit of back and forth, the system figures out how to securely call .env variables.&#x20;

#### Use cases

* Send a welcome email to every lead who fills out a BuildAI lead capture form
* Trigger a booking confirmation email from an AI Employee action when an appointment is accepted
* Notify your internal team when a new user registers in your BuildAI app
* Fire a follow-up email when a prospect completes a multi-step form or onboarding flow

#### Supported functionality

* Send transactional emails triggered by any BuildAI workflow action
* Personalize email content with dynamic data from BuildAI form fields and variables
* Send HTML and plain-text email bodies from a single integration call
* Send using a Mailtrap template by referencing a `template_uuid` in the body payload
* Track delivery status, open rates, and click rates in Mailtrap’s email logs
* Use [Email Sandbox](https://mailtrap.io/email-sandbox/) to test sends during app development without delivering to real recipients
