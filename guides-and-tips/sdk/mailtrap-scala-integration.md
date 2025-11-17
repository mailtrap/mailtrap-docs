---
title: Mailtrap Scala Integration
description: Learn how to integrate Mailtrap with Scala apps and projects for email sending using SMTP and RESTful API methods.
---

Mailtrap can be integrated with Scala apps and projects for email sending.

# Email API/SMTP for Scala

## SMTP integration

To integrate SMTP with your Scala app, navigate to the **Integrations** tab and copy-paste the credentials or ready-made code snippets.

Note that you'll have to use Play-Mailer configuration, as Scala doesn't have built-in support for SMTP sending.

<figure><img src="../.gitbook/assets/mailtrap-scala-integration-smtp.png" alt="Mailtrap SMTP integration interface showing credentials and Play-Mailer code snippet for Scala configuration"><figcaption><p>Mailtrap SMTP integration for Scala with Play-Mailer configuration</p></figcaption></figure>

Read more about SMTP integration {% content-ref url="../../documentation/email-api-smtp/integrations/smtp-integration.md" %}
[smtp-integration.md](../../documentation/email-api-smtp/integrations/smtp-integration.md)
{% endcontent-ref %}

## RESTful integration

To integrate Mailtrap using RESTful API, simply copy/paste the API endpoint and API Token into the configuration file of a Scala framework or library that supports HTTP requests.

For more details, refer to the [API documentation](https://api-docs.mailtrap.io/docs/mailtrap-api-docs/5tjdeg9545058-mailtrap-api).

<figure><img src="../.gitbook/assets/mailtrap-scala-integration-api.png" alt="Mailtrap API integration interface showing cURL code sample with endpoint and authentication token"><figcaption><p>Mailtrap RESTful API integration for Scala</p></figcaption></figure>

Read more about API integration {% content-ref url="../../documentation/email-api-smtp/integrations/api-integration.md" %}
[api-integration.md](../../documentation/email-api-smtp/integrations/api-integration.md)
{% endcontent-ref %}
