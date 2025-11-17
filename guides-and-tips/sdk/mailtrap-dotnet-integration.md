---
title: <i class="fa-windows">:windows:</i> Mailtrap .NET integration
description: >-
  Learn how to integrate Mailtrap with .NET apps and projects for email sending
  using SDK, SMTP, or RESTful API.
icon: windows
---

# .NET Integration

<a href="https://github.com/mailtrap/mailtrap-dotnet" class="button primary">Mailtrap .NET SDK on GitHub</a>

## .NET Integration

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
* Compatible with .NET 6+, .NET Core, and .NET Framework

### Installation

Install the SDK using NuGet Package Manager:

{% code title=".NET CLI" %}
```bash
dotnet add package Mailtrap
```
{% endcode %}

Or using Package Manager Console:

{% code title="Package Manager" %}
```powershell
Install-Package Mailtrap
```
{% endcode %}

### Minimal Example

Here's a minimal example to send your first email:

{% code title="Program.cs" %}
```csharp
using Mailtrap;
using Mailtrap.Models;

var client = new MailtrapClient("your-api-token");

var email = new Mail
{
    From = new Address("hello@example.com", "Mailtrap Test"),
    To = new List<Address> { new Address("recipient@example.com") },
    Subject = "Hello from Mailtrap!",
    Text = "Welcome to Mailtrap Email Sending!",
    Html = "<p>Welcome to <strong>Mailtrap</strong> Email Sending!</p>"
};

try
{
    var response = await client.SendAsync(email);
    Console.WriteLine($"Email sent successfully: {response.MessageId}");
}
catch (Exception ex)
{
    Console.WriteLine($"Error sending email: {ex.Message}");
}
```
{% endcode %}

{% hint style="info" %}
Get your API token from the Mailtrap dashboard under **Settings → API Tokens**.
{% endhint %}

#### SMTP integration

To integrate SMTP with your .NET app, navigate to the Integrations tab, choose C#, and copy-paste the credentials or ready-made code snippets.

{% hint style="info" %}
SMTP integration is compatible with any .NET programming language or library that sends emails via SMTP.
{% endhint %}

![Mailtrap SMTP integration settings showing credentials and C# code sample for sending emails using System.Net.Mail library](<../.gitbook/assets/mailtrap-csharp-smtp-integration (1).png>)

Read more about SMTP integration [here](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/smtp-integration).

#### RESTful API integration

To integrate Mailtrap using RESTful API, use the configuration available among **Code samples** under the API section.

API integration can be used with any .NET programming language or library that supports HTTP requests. For more details, refer to the [API documentation](https://api-docs.mailtrap.io/docs/mailtrap-api-docs/5tjdeg9545058-mailtrap-api).

![Mailtrap API integration showing code sample for sending emails via RESTful API using C# and HttpClient with API token authentication](<../.gitbook/assets/mailtrap-csharp-api-integration (1).png>)

Read more about API integration [here](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/api-integration).
