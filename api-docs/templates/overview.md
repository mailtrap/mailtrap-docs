---
title: Email Templates Overview
description: Create and manage reusable email templates for consistent branding
---

# Overview

Email Templates allow you to create reusable email designs with dynamic content. Maintain consistent branding, reduce errors, and speed up email creation with centralized template management.

## Create a Template

Create templates using the Mailtrap UI or via API.

For step-by-step instructions on creating templates in the Mailtrap interface, see [Email Templates](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-marketing/email-templates).

## Save Template via API

Store your template using the API:

{% tabs %}
{% tab title="cURL" %}
```bash
curl -X POST "https://mailtrap.io/api/accounts/{account_id}/email_templates" \
  -H "Api-Token: YOUR_API_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "email_template": {
      "name": "Welcome Email",
      "subject": "Welcome to {{company_name}}, {{user_name}}!",
      "category": "Onboarding",
      "body_html": "<html><body><h1>Welcome {{user_name}}!</h1></body></html>",
      "body_text": "Welcome {{user_name}}!"
    }
  }'
```
{% endtab %}

{% tab title="Node.js" %}
```javascript
const response = await fetch('https://mailtrap.io/api/accounts/{account_id}/email_templates', {
  method: 'POST',
  headers: {
    'Api-Token': 'YOUR_API_TOKEN',
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({
    email_template: {
      name: 'Welcome Email',
      subject: 'Welcome to {{company_name}}, {{user_name}}!',
      category: 'Onboarding',
      body_html: '<html><body><h1>Welcome {{user_name}}!</h1></body></html>',
      body_text: 'Welcome {{user_name}}!'
    }
  })
});

const template = await response.json();
// Returns: { uuid: 'abc-123-def', name: 'Welcome Email', ... }
```
{% endtab %}

{% tab title="PHP" %}
```php
$curl = curl_init();

curl_setopt_array($curl, [
    CURLOPT_URL => "https://mailtrap.io/api/accounts/{account_id}/email_templates",
    CURLOPT_RETURNTRANSFER => true,
    CURLOPT_POST => true,
    CURLOPT_HTTPHEADER => [
        "Api-Token: YOUR_API_TOKEN",
        "Content-Type: application/json"
    ],
    CURLOPT_POSTFIELDS => json_encode([
        "email_template" => [
            "name" => "Welcome Email",
            "subject" => "Welcome to {{company_name}}, {{user_name}}!",
            "category" => "Onboarding",
            "body_html" => "<html><body><h1>Welcome {{user_name}}!</h1></body></html>",
            "body_text" => "Welcome {{user_name}}!"
        ]
    ])
]);

$response = curl_exec($curl);
curl_close($curl);
```
{% endtab %}

{% tab title="Python" %}
```python
import requests

response = requests.post(
    "https://mailtrap.io/api/accounts/{account_id}/email_templates",
    headers={
        "Api-Token": "YOUR_API_TOKEN",
        "Content-Type": "application/json"
    },
    json={
        "email_template": {
            "name": "Welcome Email",
            "subject": "Welcome to {{company_name}}, {{user_name}}!",
            "category": "Onboarding",
            "body_html": "<html><body><h1>Welcome {{user_name}}!</h1></body></html>",
            "body_text": "Welcome {{user_name}}!"
        }
    }
)

template = response.json()
```
{% endtab %}

{% tab title="Ruby" %}
```ruby
require 'net/http'
require 'json'
require 'uri'

uri = URI("https://mailtrap.io/api/accounts/{account_id}/email_templates")
http = Net::HTTP.new(uri.host, uri.port)
http.use_ssl = true

request = Net::HTTP::Post.new(uri)
request["Api-Token"] = "YOUR_API_TOKEN"
request["Content-Type"] = "application/json"
request.body = {
  email_template: {
    name: "Welcome Email",
    subject: "Welcome to {{company_name}}, {{user_name}}!",
    category: "Onboarding",
    body_html: "<html><body><h1>Welcome {{user_name}}!</h1></body></html>",
    body_text: "Welcome {{user_name}}!"
  }
}.to_json

response = http.request(request)
```
{% endtab %}

{% tab title=".NET" %}
```csharp
using System.Net.Http;
using System.Text;
using System.Text.Json;

var client = new HttpClient();
client.DefaultRequestHeaders.Add("Api-Token", "YOUR_API_TOKEN");

var content = new StringContent(
    JsonSerializer.Serialize(new {
        email_template = new {
            name = "Welcome Email",
            subject = "Welcome to {{company_name}}, {{user_name}}!",
            category = "Onboarding",
            body_html = "<html><body><h1>Welcome {{user_name}}!</h1></body></html>",
            body_text = "Welcome {{user_name}}!"
        }
    }),
    Encoding.UTF8,
    "application/json"
);

var response = await client.PostAsync(
    "https://mailtrap.io/api/accounts/{account_id}/email_templates",
    content
);
```
{% endtab %}

{% tab title="Java" %}
```java
import java.net.http.*;
import java.net.URI;

HttpClient client = HttpClient.newHttpClient();

String json = """
    {
      "email_template": {
        "name": "Welcome Email",
        "subject": "Welcome to {{company_name}}, {{user_name}}!",
        "category": "Onboarding",
        "body_html": "<html><body><h1>Welcome {{user_name}}!</h1></body></html>",
        "body_text": "Welcome {{user_name}}!"
      }
    }
    """;

HttpRequest request = HttpRequest.newBuilder()
    .uri(URI.create("https://mailtrap.io/api/accounts/{account_id}/email_templates"))
    .header("Api-Token", "YOUR_API_TOKEN")
    .header("Content-Type", "application/json")
    .POST(HttpRequest.BodyPublishers.ofString(json))
    .build();

HttpResponse<String> response = client.send(request, HttpResponse.BodyHandlers.ofString());
```
{% endtab %}
{% endtabs %}

## Send Email Using Template

Use the template UUID to send personalized emails:

{% tabs %}
{% tab title="cURL" %}
```bash
curl -X POST "https://send.api.mailtrap.io/api/send" \
  -H "Authorization: Bearer YOUR_API_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "from": {"email": "noreply@example.com"},
    "to": [{"email": "user@example.com"}],
    "template_uuid": "abc-123-def",
    "template_variables": {
      "user_name": "John Doe",
      "company_name": "Acme Corp"
    }
  }'
```
{% endtab %}

{% tab title="Node.js" %}
```javascript
import { MailtrapClient } from "mailtrap";

const client = new MailtrapClient({
  token: process.env.MAILTRAP_API_KEY
});

await client.send({
  from: { email: "noreply@example.com" },
  to: [{ email: "user@example.com" }],
  template_uuid: "abc-123-def",
  template_variables: {
    user_name: "John Doe",
    company_name: "Acme Corp"
  }
});
```
{% endtab %}

{% tab title="PHP" %}
```php
use Mailtrap\MailtrapClient;
use Mailtrap\Mime\MailtrapEmail;
use Symfony\Component\Mime\Address;

$mailtrap = MailtrapClient::initSendingEmails(
    apiKey: $_ENV['MAILTRAP_API_KEY']
);

$email = (new MailtrapEmail())
    ->from(new Address('noreply@example.com'))
    ->to(new Address('user@example.com'))
    ->templateUuid('abc-123-def')
    ->templateVariables([
        'user_name' => 'John Doe',
        'company_name' => 'Acme Corp'
    ]);

$mailtrap->send($email);
```
{% endtab %}

{% tab title="Python" %}
```python
import mailtrap as mt

client = mt.MailtrapClient(token="YOUR_API_KEY")

client.send(mt.Mail(
    sender=mt.Address(email="noreply@example.com"),
    to=[mt.Address(email="user@example.com")],
    template_uuid="abc-123-def",
    template_variables={
        "user_name": "John Doe",
        "company_name": "Acme Corp"
    }
))
```
{% endtab %}

{% tab title="Ruby" %}
```ruby
require 'mailtrap'

client = Mailtrap::Client.new(api_key: 'YOUR_API_KEY')

mail = Mailtrap::Mail.from_template(
  from: { email: 'noreply@example.com' },
  to: [{ email: 'user@example.com' }],
  template_uuid: 'abc-123-def',
  template_variables: {
    user_name: 'John Doe',
    company_name: 'Acme Corp'
  }
)

client.send(mail)
```
{% endtab %}

{% tab title=".NET" %}
```csharp
using Mailtrap;

var client = new MailtrapClient("YOUR_API_KEY");

await client.SendAsync(new MailtrapMessage
{
    From = new MailtrapAddress { Email = "noreply@example.com" },
    To = new[] { new MailtrapAddress { Email = "user@example.com" } },
    TemplateUuid = "abc-123-def",
    TemplateVariables = new Dictionary<string, object>
    {
        { "user_name", "John Doe" },
        { "company_name", "Acme Corp" }
    }
});
```
{% endtab %}

{% tab title="Java" %}
```java
import io.mailtrap.api.MailtrapClient;
import io.mailtrap.model.*;

MailtrapClient client = new MailtrapClient("YOUR_API_KEY");

Email email = Email.builder()
    .from(new Address("noreply@example.com"))
    .to(List.of(new Address("user@example.com")))
    .templateUuid("abc-123-def")
    .templateVariables(Map.of(
        "user_name", "John Doe",
        "company_name", "Acme Corp"
    ))
    .build();

client.send(email);
```
{% endtab %}
{% endtabs %}

## Template Variables

Templates support Handlebars syntax for dynamic content including variables, conditionals, and loops.

For complete syntax reference and examples, see [Handlebars Guide](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/email-templates/handlebars-guide).

## Testing Templates

You can test your templates using Email Sandbox before sending to production.

For detailed instructions on template debugging, see:
- [Email Sandbox API Overview](../sandbox/overview.md)
- [Debugging with Sandbox](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/email-templates/debugging)
