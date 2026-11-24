---
description: >-
  Comprehensive guide to integrate Mailtrap with Vercel for live email sending,
  sandbox testing, and inbound email.
cover: ../../.gitbook/assets/vercel-cover.png
coverY: 0
---

# Vercel

You can integrate Mailtrap with Vercel in two ways, through:

* Environment variables added to your project
* Vercel Connect, which supplies Mailtrap credentials at runtime

Both let your Vercel apps send emails through Mailtrap, test them in Email Sandbox, receive inbound email, and use the Mailtrap API.

### Integration options

Mailtrap offers two main integration approaches with Vercel:

#### **Native Vercel integration (environment variables)**

Install the Mailtrap integration from Mailtrap’s Integrations page to automatically add Mailtrap credentials to your Vercel project as environment variables. This approach is ideal for apps that read their configuration from environment variables and switch between testing and production sending.

**Key features**:

* Mailtrap credentials are added to your project automatically, with no manual copying
* Separate variables for the Development, Preview, and Production environments
* Switch between Email Sandbox and live sending per environment
* An API token generated at the domain level during setup

See the native Vercel integration guide for detailed setup instructions.

{% content-ref url="integration.md" %}
[integration.md](integration.md)
{% endcontent-ref %}

#### **Vercel Connect (runtime credentials)**

Create a Mailtrap connector in Vercel, and your apps and AI agents request Mailtrap credentials at runtime instead of storing an API key in environment variables. This approach is ideal for AI-built apps and agents that should never see the API key.

**Key features**:

* The Mailtrap API key never appears in your app’s code or environment variables
* Credentials are requested at runtime through the Vercel Connect SDK
* One shared API key on the connector, which you can update or rotate in one place
* Works with the Email API, Email Sandbox, and the Inbound Email API

See the Vercel Connect guide for detailed setup instructions.

{% content-ref url="connect.md" %}
[connect.md](connect.md)
{% endcontent-ref %}

#### Which integration should you choose?

**Choose the native integration if you**:

* Want the quickest setup with no code changes to how your app reads credentials
* Already use environment variables for your app’s configuration
* Want separate testing and production settings for each Vercel environment
* Only need to send emails, in testing or production

**Choose Vercel Connect if you**:

* Don’t want the API key stored in environment variables
* Are building an AI agent that sends or reads emails without the model seeing the API key
* Built your app with v0 or the AI SDK
* Need the Inbound Email API, for example to give an agent its own email address
* Want to rotate the API key in one place without redeploying

#### Getting started

Both integration guides above contain step-by-step instructions, screenshots, and code examples. Choose the option that best fits your use case and follow the corresponding guide.
