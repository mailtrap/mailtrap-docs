---
description: Learn how to integrate Mailtrap with Phoenix applications to send emails.
---

# Phoenix

This guide shows you how to integrate Mailtrap with Phoenix and send emails using the Email API.

Before we start, you'll need to:

* [Verify your sending domain](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/setup/sending-domain)
* [Create and save an API key](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/setup/api-tokens)

## Send emails using Phoenix and Mailtrap

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
To learn more about API integration, [click here](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/api-integration).
{% endhint %}
