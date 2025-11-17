---
title: Mailtrap Phoenix Integration
description: Learn how to integrate Mailtrap with Phoenix applications to send emails.
---

Before we start, you'll need to:

- [Verify your sending domain](https://help.mailtrap.io/article/69-sending-domain-setup)
- [Create and save an API key](https://help.mailtrap.io/article/103-api-tokens)

# Overview

To integrate Mailtrap and send emails via Phoenix, simply copy/paste the following script into your configuration:

{% code title="Phoenix configuration" %}
```elixir
# config/config.exs
config :sample, Sample.Mailer,
  adapter: Swoosh.Adapters.Mailtrap,
  api_key: "my-api-key"

# lib/sample/mailer.ex
defmodule Sample.Mailer do
  use Swoosh.Mailer, otp_app: :sample
end
```
{% endcode %}

Once you copy the script, make sure to insert your Mailtrap API token instead of the `my-api-key` value.

{% hint style="info" %}
To learn more about API integration, [click here](https://help.mailtrap.io/article/121-mailtrap-email-sending-api-integration).
{% endhint %}