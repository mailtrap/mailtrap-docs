---
description: >-
  Learn how to integrate Mailtrap with your Elixir applications using SDK, SMTP,
  or RESTful API for email sending
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

# Elixir

<a href="https://github.com/mailtrap/mailtrap-elixir" class="button primary">Mailtrap Elixir SDK on GitHub</a>

## Overview

Mailtrap can be integrated with Elixir apps and projects for email sending.

## Email API/SMTP for Elixir

### SDK integration

The [Mailtrap Elixir SDK](https://github.com/mailtrap/mailtrap-elixir) brings functional programming elegance to email sending with full support for Elixir's concurrent and fault-tolerant features. The SDK supports:

* Transactional email sending
* Sandbox testing
* Account management
* OTP-compliant design
* Pattern matching for responses
* Pipe-friendly API

{% hint style="info" %}
Check the repo for Bamboo adaptor examples.
{% endhint %}

### Installation

Add the SDK to your `mix.exs` dependencies:

{% code title="mix.exs" %}
```elixir
def deps do
  [
    {:mailtrap, "~> 1.0"}
  ]
end
```
{% endcode %}

Then run:

{% code title="Terminal" %}
```bash
mix deps.get
```
{% endcode %}

### Minimal Example

Here's a minimal example to send your first email:

{% code title="send_email.exs" %}
```elixir
client = Mailtrap.Sending.client("PASTE TOKEN HERE")
email = (%Mailtrap.Email{}
  |> Mailtrap.Email.put_from({"From name", "from@example.com"})
  |> Mailtrap.Email.put_to({"Recepient", "recepient@example.com"})
  |> Mailtrap.Email.put_subject("Hi there")
  |> Mailtrap.Email.put_text("General Kenobi"))
Mailtrap.Sending.send(client, email)
```
{% endcode %}

{% hint style="info" %}
Get your API token from your Mailtrap account under **Settings → API Tokens**.
{% endhint %}

### SMTP integration

To integrate SMTP with your Elixir app, navigate to the Integrations tab and copy-paste the credentials.

{% hint style="info" %}
SMTP integration is compatible with any Elixir framework or library that sends emails via SMTP.
{% endhint %}

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/mailtrap-elixir-integration-smtp-credentials.png" alt="" width="563"></div>

Read more about SMTP integration [here](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/setup/smtp-integration).

### RESTful API integration

To integrate Mailtrap using RESTful API, simply copy/paste the API endpoint and API Token into the configuration file of the Elixir framework or library that supports HTTP requests. For more details, refer to the [API documentation](https://api-docs.mailtrap.io/docs/mailtrap-api-docs/5tjdeg9545058-mailtrap-api).

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/mailtrap-elixir-integration-api-credentials.png" alt="" width="563"></div>

Read more about API integration in the [here](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/setup/api-integration).
