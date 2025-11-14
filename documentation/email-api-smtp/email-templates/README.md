---
title: Email Templates
description: >-
  Create and send Mailtrap email templates with drag-and-drop builder or HTML
  editor, add Handlebars variables, and integrate via API or SMTP.
---

## Overview

Email Templates allow you to design, edit, and host HTML email templates, and reference them via API.

<figure><img src="../../.gitbook/assets/template-html-code-editor (1).png" alt="Template editor showing HTML code on left and email preview on right with welcome message"><figcaption><p>Email template editor with code and preview</p></figcaption></figure>

By storing the template on Mailtrap and calling it via API, you can easily change the template code without committing to your codebase.

Email Templates support Variables, and Mailtrap uses Handlebars as a template engine.

You can put \{{user\_name\}} into your template and pass "John" as the "user\_name" value via API.

For a complete guide on using Handlebars with email templates, see [Handlebars Guide](handlebars-guide.md).

{% embed url="https://mailtrap.io/blog/using-handlebars-with-mailtrap-email-templates-quick-guide-with-examples/" fullWidth="false" %}

## Creating a template

{% stepper %}
{% step %}
Navigate to the Templates menu

<figure><img src="../../.gitbook/assets/template-menu-nav (1).png" alt="Mailtrap sidebar with Templates menu item highlighted by red arrow"><figcaption><p>Templates navigation menu</p></figcaption></figure>
{% endstep %}

{% step %}
Click the Create New Template button.

<figure><img src="../../.gitbook/assets/template-list-create-button (1).png" alt="Templates list page with Create New Template button highlighted by red arrow"><figcaption><p>Create New Template button</p></figcaption></figure>
{% endstep %}

{% step %}
Click the drop-down menu to select one of your domains, enter the Template name, Subject, and Category, and click Continue.

<figure><img src="../../.gitbook/assets/template-details-form (1).png" alt="Template Details form with fields for domain selection, template name, subject, and category with Continue button highlighted"><figcaption><p>Template details form</p></figcaption></figure>
{% endstep %}

{% step %}
Choose the Drag & Drop Editor to build the template without coding, or select HTML Editor if you prefer to write/modify the code.

<figure><img src="../../.gitbook/assets/template-design-selection (1).png" alt="Template Design page with Drag &#x26; Drop Editor and HTML Editor options, showing template previews below"><figcaption><p>Template design selection</p></figcaption></figure>
{% endstep %}

{% step %}
Create/modify the design and click Finish.

<figure><img src="../../.gitbook/assets/template-drag-drop-editor (1).png" alt="Drag and Drop Editor showing email template preview on left and content blocks panel on right with Finish button"><figcaption><p>Drag and Drop Editor interface</p></figcaption></figure>

The main Templates menu features all your saved templates. To quickly access a saved template, just click on it within the main menu.

<figure><img src="../../.gitbook/assets/template-list-view (1).png" alt="Templates list showing multiple saved templates with names, types, categories, and last update dates"><figcaption><p>Saved templates list</p></figcaption></figure>
{% endstep %}
{% endstepper %}

## Managing templates

### List of templates and user permissions

Clicking on Templates in the side menu lists all the templates you can access.

<figure><img src="../../.gitbook/assets/template-final-list (1).png" alt="Templates page showing list of all available templates with names, types, categories, and update dates"><figcaption><p>List of all templates</p></figcaption></figure>

Access to templates is managed on a domain level. You need to have Admin access to a domain to manipulate the templates. In case you don't have Edit rights, you can't change the template. Each account can have up to 200 email templates.

{% hint style="warning" %}
You can delete a template. However, this action is irreversible, so be sure to change the sending/testing code after deletion. When the template is deleted, the UUID is also deleted, and Mailtrap won't be able to render it.
{% endhint %}

## Next steps

* [Editing and Customizing Templates](editing-and-customizing.md) - Learn how to customize templates with the Drag & Drop or Code Editor
* [Handlebars Guide](handlebars-guide.md) - Complete guide to using Handlebars syntax in templates
* [Integration](integration.md) - Integrate templates with Email API/SMTP
* [Debugging](debugging.md) - Test templates with Email Sandbox
