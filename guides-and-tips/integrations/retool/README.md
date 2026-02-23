# Retool

Mailtrap can be integrated with Retool, giving you flexible options for email sending and contact management. This integration allows you to send transactional and bulk emails, manage contacts, and maintain suppression lists — all within Retool's resource environment.

### Integration options

Mailtrap offers two main integration approaches with Retool:

### Retool + Mailtrap REST API

Use Mailtrap's REST API to send emails directly from your Retool application. This approach is ideal for simple setups and quick implementations.

**Key** **features**:

* Configure a single REST API resource with your Mailtrap API key
* Send transactional emails using the `/api/send` endpoint
* Reuse queries across multiple Retool apps

See the Retool and Mailtrap REST API integration guide for detailed setup instructions.

{% embed url="https://docs.mailtrap.io/guides/integrations/retool/retool" %}

### Retool + Mailtrap OpenAPI

Use Mailtrap's OpenAPI specifications to access the full range of Mailtrap features within Retool. This approach is ideal for advanced use cases requiring multiple endpoints.

**Key** **features**:

* Send transactional and bulk emails
* Sync contacts from external databases or CRMs
* Manage suppression lists for better deliverability
* Trigger Mailtrap Automation sequences based on contact updates

See the Retool and Mailtrap OpenAPI integration guide for detailed setup instructions.

{% embed url="https://docs.mailtrap.io/guides/integrations/retool/retool-openapi-integration" %}

### Which integrations should you choose?

**Choose Retool + REST API if you**:

* Need a quick setup for sending transactional emails
* Prefer a simple, single-resource configuration
* Only need basic email sending functionality

**Choose Retool + OpenAPI if you**:

* Want access to multiple Mailtrap endpoints (sending, contacts, suppressions)
* Need to send bulk/promotional emails alongside transactional emails
* Plan to sync contacts and trigger automation sequences
* Require suppression list management for deliverability optimization

### Getting started

Both integration guides above contain step-by-step instructions, screenshots, and code examples. Choose the option that best fits your use case and follow the corresponding guide.

