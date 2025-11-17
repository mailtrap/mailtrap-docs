---
title: <i class="fa-gem">:gem:</i> Mailtrap Sinatra Integration
description: Learn how to integrate Mailtrap with Sinatra applications to send emails using the Email API.
---

# Overview

This guide shows you how to integrate Mailtrap with Sinatra and send emails using the Email API.

Before we start, you'll need to:

- [Verify your sending domain](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/setup/sending-domain-setup)
- [Create and save an API key](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/account-and-organization/api-tokens)

## Send emails using Sinatra and Mailtrap

To integrate Mailtrap and send emails via Sinatra, copy the following script into your configuration:

{% code title="app.rb" language="ruby" %}
```ruby
require "sinatra"
require "mailtrap"

set :port, 5000
set :bind, "0.0.0.0"

get "/" do
  content_type :json

  mail = Mailtrap::Mail.from_content(
    from: { name: 'Mailtrap Test', email: 'YOUR-EMAIL-HERE' },
    to: [{ email: 'RECIPIENT-EMAIL-HERE' }],
    subject: 'Hello World',
    html: '<strong>it works!</strong>',
  )

  client = Mailtrap::Client.new(api_key: 'YOUR-MAILTRAP-API-KEY-HERE')
  response = client.send(mail)

  response.to_hash.to_json
end
```
{% endcode %}

Once you copy the script, make sure to:

- Insert your Mailtrap API token in the `api_key:` field
- Enter your email address in the `from:` field
- Enter your recipient's email address in the `to:` field

{% hint style="info" %}
To learn more about API integration, see [Mailtrap Email Sending API Integration](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/api-integration).
{% endhint %}