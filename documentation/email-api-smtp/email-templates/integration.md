---
title: Template Integration - Email API/SMTP
description: >-
  Learn how to integrate Mailtrap email templates with Email API/SMTP using
  Transactional or Bulk streams.
---

# Integration

### Overview

Once you've created and customized your email template, you can integrate it with your application using the Email API or SMTP. This guide shows you how to get the necessary credentials and code samples to send emails using your templates.

### Integration steps

{% stepper %}
{% step %}
Navigate to Templates in the menu on the left.

<figure><img src="../../.gitbook/assets/template-menu-nav (1).png" alt="Mailtrap sidebar menu with Templates menu item highlighted by red arrow"><figcaption><p>Templates in navigation menu</p></figcaption></figure>
{% endstep %}

{% step %}
Click the template you want to call using the API.

<figure><img src="../../.gitbook/assets/template-list-view (1).png" alt="Templates list showing Newsletter template highlighted by red arrow"><figcaption><p>Select template from list</p></figcaption></figure>
{% endstep %}

{% step %}
Open the Integration tab.

<figure><img src="../../.gitbook/assets/template-integration-tab (1).png" alt="Template page showing Details and Integration tabs with Integration tab highlighted by red arrow"><figcaption><p>Open Integration tab</p></figcaption></figure>
{% endstep %}

{% step %}
With Email API/SMTP toggled on, click Integrate under Transactional Stream or Bulk Stream.

<figure><img src="../../.gitbook/assets/template-stream-options.png" alt="Integration page showing Transactional Stream and Bulk Stream options with Integrate buttons highlighted by red arrows"><figcaption><p>Choose stream type and click Integrate</p></figcaption></figure>
{% endstep %}

{% step %}
Copy the necessary credentials such as Host, API Token, and Template UUID.

<figure><img src="../../.gitbook/assets/marketing-templates-transactional (1).png" alt="Transactional Stream API credentials box showing Host, API Token, and Template UUID"><figcaption><p>Transactional Stream API credentials</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/marketing-templates-bulk (1).png" alt="Bulk Stream API credentials box showing Host, API Token, and Template UUID"><figcaption><p>Bulk Stream API credentials</p></figcaption></figure>
{% endstep %}

{% step %}
Alternatively, under Code Samples, choose the desired language and copy the sample configuration already containing the necessary credentials. Mailtrap's official SDKs ([Node.js](https://github.com/railsware/mailtrap-nodejs), [Python](https://github.com/railsware/mailtrap-python), [PHP](https://github.com/railsware/mailtrap-php), and [Ruby](https://github.com/railsware/mailtrap-ruby)) also support the templates feature.
{% endstep %}

{% step %}
Paste the code into your project and customize it if needed. Then, run the code to send an email to the email address you indicated in your script.

For more details, [open the API docs](https://api-docs.mailtrap.io/docs/mailtrap-api-docs/5tjdeg9545058-mailtrap-api) and go to Email Sending API → Emails → Send email (including template) for transactional stream and Bulk Sending API → Emails → Send email (including template) for bulk stream. Under Body, click the dropdown menu, and choose `EmailFromTemplate`.
{% endstep %}
{% endstepper %}

### Next steps

* [Debugging](debugging.md) - Test your template integration with Email Sandbox
* [Handlebars Guide](handlebars-guide.md) - Learn about using variables and dynamic content in templates
