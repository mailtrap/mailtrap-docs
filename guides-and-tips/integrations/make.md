---
description: >-
  Automate email workflows by connecting Mailtrap to thousands of applications
  using Make.com (formerly Integromat) without writing any code.
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

# Make.com

<a href="https://www.make.com/en/integrations/mailtrap" class="button primary">View on Make.com Marketplace</a>

## Overview

Using the Mailtrap integration with Make.com, you can automate email sending and contact management by connecting Mailtrap to thousands of other applications without any coding. This guide shows you how to set up the integration, create scenarios, and manage your automations.

## About Make.com

Make.com (formerly Integromat) is a powerful visual automation platform that allows you to design, build, and automate workflows between apps and services. With Mailtrap integration, you can:

* Send transactional emails automatically
* Manage contacts and lists
* Trigger emails based on events from other apps
* Sync data between Mailtrap and your tools

## Getting Started with Make.com

### Prerequisites

Before you start, you'll need:

* A [Make.com account](https://www.make.com/en/register)
* A [Mailtrap account](https://mailtrap.io/register/signup)
* [Verified sending domain](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/setup/sending-domain) in Mailtrap
* [Mailtrap API token](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/setup/api-tokens)

### Connecting Mailtrap to Make.com

{% stepper %}
{% step %}
**Create a New Scenario**

Log in to your Make.com account and create a new scenario.

Click the **+** button to add a new module and search for "Mailtrap".
{% endstep %}

{% step %}
**Add a Mailtrap Module**

Select the Mailtrap app and choose the action you want to perform:

* **Send Email** - Send transactional emails
* **Create Contact** - Add new contacts to your list
* **Update Contact** - Modify existing contact information
* **Add to List** - Add contacts to specific lists
* **Remove from List** - Remove contacts from lists
{% endstep %}

{% step %}
**Configure the Connection**

When prompted, add your Mailtrap connection:

1. Enter a connection name
2. Paste your Mailtrap API token
3. Click **Save**

Your Mailtrap account is now connected to Make.com.
{% endstep %}

{% step %}
**Configure the Module**

Set up the module parameters:

* Select your sending domain
* Configure email recipients
* Add subject and content
* Set any additional parameters

Map data from previous modules or enter static values as needed.
{% endstep %}

{% step %}
**Test and Activate**

Test your scenario to ensure it works correctly, then activate it to run automatically based on your triggers.
{% endstep %}
{% endstepper %}

## Common Use Cases

### Scenario 1: Send Welcome Email from Form Submission

**Trigger**: New form submission (e.g., Google Forms, Typeform) **Action**: Send welcome email via Mailtrap

This scenario automatically sends a personalized welcome email when someone submits a form.

### Scenario 2: Add Newsletter Subscribers to Contacts

**Trigger**: New subscriber in mailing list tool **Action**: Create contact in Mailtrap

Automatically sync new subscribers from your form or landing page to Mailtrap contacts.

### Scenario 3: Send Order Confirmation Emails

**Trigger**: New order in e-commerce platform (Shopify, WooCommerce) **Action**: Send transaction confirmation email via Mailtrap

Send professional order confirmations automatically when customers make a purchase.

### Scenario 4: Sync CRM Contacts to Mailtrap

**Trigger**: New contact in CRM (HubSpot, Salesforce) **Action**: Create contact in Mailtrap and add to list

Keep your Mailtrap contacts in sync with your CRM system.

## Available Actions

Mailtrap offers the following actions in Make.com:

* **Send Email** - Send transactional emails from verified domains
* **Create Contact** - Add new contacts with custom fields
* **Update Contact** - Modify contact information and custom fields
* **Delete Contact** - Remove contacts from your account
* **Add Contact to List** - Add contacts to specific lists
* **Remove Contact from List** - Remove contacts from lists
* **Make an API Call** - Use custom API endpoints for advanced scenarios

## Best Practices

{% hint style="success" %}
**Tips for Success**

1. **Test Before Production**: Always test scenarios with sample data first
2. **Error Handling**: Add error handlers to manage failed operations
3. **Rate Limits**: Be mindful of API rate limits for high-volume scenarios
4. **Data Mapping**: Use Make.com's data mapping tools for dynamic content
5. **Monitoring**: Regularly check scenario execution history
{% endhint %}

## Troubleshooting

### Connection Issues

If you can't connect Mailtrap to Make.com:

* Verify your API token is correct and has proper permissions
* Check that your token hasn't expired
* Ensure you're using the Admin API token

### Emails Not Sending

If emails aren't being sent:

* Verify your sending domain is verified in Mailtrap
* Check that the "from" email matches your verified domain
* Review scenario execution history for error messages
* Ensure you have sufficient sending credits

### Contact Sync Issues

If contacts aren't syncing properly:

* Verify email addresses are valid format
* Check that custom fields exist in Mailtrap
* Ensure list IDs are correct
* Review field mapping in Make.com

## Getting Help

Need assistance with your Make.com integration?

* **Make.com Documentation**: [Make.com Help Center](https://www.make.com/en/help)
* **Mailtrap API Docs**: [API Reference](https://api-docs.mailtrap.io/)
* **Mailtrap Support**: [support@mailtrap.io](mailto:support@mailtrap.io)

## Next Steps

After setting up your Make.com integration:

1. Explore more complex scenarios with multiple steps
2. Combine Mailtrap with other apps for powerful workflows
3. Set up monitoring and alerts for your scenarios
4. Review [Mailtrap Email Templates](https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/email-templates) for better email design
