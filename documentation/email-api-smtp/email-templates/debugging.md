---
title: Template Debugging
description: Learn how to test and debug your email templates using Mailtrap Email Sandbox.
icon: bug
---

# Debugging with Sandbox

### Overview

Before sending your email templates to production, it's important to test them in a safe environment. Mailtrap Email Sandbox allows you to test your templates, preview how they render, and verify that all variables are working correctly.

### Debugging steps

{% stepper %}
{% step %}
Navigate to Templates in the menu on the left.

<div align="left" data-with-frame="true"><figure><img src="../../.gitbook/assets/template-menu-nav.png" alt="Mailtrap sidebar with Templates menu item highlighted by red arrow" width="375"><figcaption><p>Navigate to Templates</p></figcaption></figure></div>
{% endstep %}

{% step %}
Click the template you want to call using the API.

<div align="left" data-with-frame="true"><figure><img src="../../.gitbook/assets/template-list-view.png" alt="Templates list showing Newsletter template highlighted by red arrow" width="563"><figcaption><p>Select template to debug</p></figcaption></figure></div>
{% endstep %}

{% step %}
Open the Integration tab.

<div align="left" data-with-frame="true"><figure><img src="../../.gitbook/assets/template-integration-tab.png" alt="Template page showing Details and Integration tabs with Integration tab highlighted by red arrow" width="563"><figcaption><p>Open Integration tab</p></figcaption></figure></div>
{% endstep %}

{% step %}
Toggle the switch to Email Testing.

<div align="left" data-with-frame="true"><figure><img src="../../.gitbook/assets/template-email-testing-toggle.png" alt="Integration page with Email Testing toggle highlighted by red arrow" width="375"><figcaption><p>Toggle to Email Testing</p></figcaption></figure></div>
{% endstep %}

{% step %}
And click Integrate.

<div align="left" data-with-frame="true"><figure><img src="../../.gitbook/assets/template-testing-inbox-integrate.png" alt="Testing Inbox card with Integrate button highlighted by red arrow" width="375"><figcaption><p>Click Integrate for Testing Inbox</p></figcaption></figure></div>
{% endstep %}

{% step %}
Select the desired sandbox from the dropdown menu to reveal its credentials. Copy the Host, API Token, Template UUID, and Sandbox ID.

Alternatively, you can also use one of the pre-made Code Samples.

<div align="left" data-with-frame="true"><figure><img src="../../.gitbook/assets/template-sandbox-credentials.png" alt="Sandbox integration showing API credentials and code samples with sandbox dropdown" width="563"><figcaption><p>Sandbox credentials and code samples</p></figcaption></figure></div>
{% endstep %}

{% step %}
Paste the code into your project and customize it if needed. Then, run the code to send an email to the selected Email Testing sandbox.
{% endstep %}

{% step %}
Finally, check the sandbox you specified in the script.

<div align="left" data-with-frame="true"><figure><img src="../../.gitbook/assets/template-test-email-received.png" alt="Email Testing sandbox showing received test email with template content" width="563"><figcaption><p>Test email received in sandbox</p></figcaption></figure></div>

The Tech Info tab contains the link to the template you tested and lists all the variables used in the template.

<div align="left" data-with-frame="true"><figure><img src="../../.gitbook/assets/template-tech-info-variables.png" alt="Tech Info tab showing template link and variables used in the email" width="563"><figcaption><p>Tech Info tab with template details</p></figcaption></figure></div>

For more details, [open the API docs](https://api-docs.mailtrap.io/docs/mailtrap-api-docs/5tjdeg9545058-mailtrap-api) and go to [Sandbox API](https://api-docs.mailtrap.io/docs/mailtrap-api-docs/a2041e813d169-email-testing-api) → Test Emails → Send email (including templates). Under Body, click the dropdown menu, and choose `EmailFromTemplate`.
{% endstep %}
{% endstepper %}
