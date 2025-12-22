---
description: >-
  Learn how to integrate Mailtrap with .NET apps and projects for email sending
  using SDK, SMTP, or RESTful API.
---

# .NET

<a href="https://github.com/mailtrap/mailtrap-dotnet" class="button primary">Mailtrap .NET SDK on GitHub</a>

### Overview

Mailtrap can be integrated with .NET apps and projects for email sending.

### Email API/SMTP for .NET

#### SDK integration

The [Mailtrap .NET SDK](https://github.com/mailtrap/mailtrap-dotnet) is a modern, async-first library for sending transactional and bulk emails from .NET applications. The SDK supports:

* Transactional email sending
* Batch email sending
* Template management
* Contact management
* Sandbox testing
* Account management
* Async/await pattern support
* .NET 6+, .NET Core, and .NET Framework

### Installation

Install the SDK using NuGet Package Manager:

{% code title=".NET CLI" %}
```bash
dotnet nuget add source https://nuget.pkg.github.com/mailtrap/index.json --name github-mailtrap --username GITHUB_USERNAME --password GITHUB_PAT --store-password-in-clear-text
dotnet add package Mailtrap -v 3.0.0 -s github-mailtrap

```
{% endcode %}

### Minimal Example

Here's a minimal example to send your first email:

{% code title="Program.cs" %}
```csharp
using Mailtrap;
using Mailtrap.Emails.Models;
using Mailtrap.Emails.Requests;

using var mailtrapClientFactory = new MailtrapClientFactory("YOUR_API_KEY");
var client = mailtrapClientFactory.CreateClient();

var mail = new SendEmailRequest
{
      From = new EmailAddress("sender@yourdomain.com"),
      To = new[] { new EmailAddress("recipient@example.com") },
      Subject = "Hello from Mailtrap",
      TextBody = "Welcome to Mailtrap Email API!"
};

await client.Email().Send(mail);
```
{% endcode %}

{% hint style="info" %}
Get your API token from your Mailtrap account under **Settings → API Tokens**.
{% endhint %}

#### SMTP integration

To integrate SMTP with your .NET app, navigate to the Integrations tab, choose C#, and copy-paste the credentials or ready-made code snippets.

{% hint style="info" %}
SMTP integration is compatible with any .NET programming language or library that sends emails via SMTP.
{% endhint %}

<div data-with-frame="true"><img src="../.gitbook/assets/mailtrap-csharp-smtp-integration.png" alt=""></div>

Read more about SMTP integration [here](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/setup/smtp-integration).

#### RESTful API integration

To integrate Mailtrap using RESTful API, use the configuration available among **Code samples** under the API section.

API integration can be used with any .NET programming language or library that supports HTTP requests. For more details, refer to the [API documentation](https://api-docs.mailtrap.io/docs/mailtrap-api-docs/5tjdeg9545058-mailtrap-api).

<div data-with-frame="true"><img src="../.gitbook/assets/mailtrap-csharp-api-integration.png" alt=""></div>

Read more about API integration [here](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/setup/api-integration).
