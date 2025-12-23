---
description: >-
  Upload, store, and organize your contacts in email lists to send targeted
  campaigns.
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

# Contacts Management

Mailtrap Contacts allows you to upload and store your contacts on the Mailtrap platform and organize them in different email lists to send targeted campaigns.

## Key Features

* Import contacts via CSV, API, or third-party integrations
* Organize contacts into targeted lists and segments
* Manage custom fields for personalization
* Track subscription status and engagement

## Getting Started

<table data-view="cards" data-full-width="false"><thead><tr><th></th><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td><strong>Overview</strong></td><td>Filter, search, edit, and perform bulk actions on your contact database.</td><td><a href="overview.md">overview.md</a></td></tr><tr><td><strong>Custom Fields</strong></td><td>Define custom variables like name, date of birth, or location to personalize your campaigns.</td><td><a href="custom-fields.md">custom-fields.md</a></td></tr><tr><td><strong>Import Contacts</strong></td><td>Bulk contacts import from spreadsheets, sync via API, or use our integrations.</td><td><a href="import-contacts.md">import-contacts.md</a></td></tr><tr><td><strong>Lists</strong></td><td>Static groups of contacts that help you organize your audience for targeted email campaigns</td><td><a href="lists.md">lists.md</a></td></tr><tr><td><strong>Segments</strong></td><td>Dynamic groups of contacts that automatically update based on criteria you define</td><td><a href="segments.md">segments.md</a></td></tr></tbody></table>

## Contact management workflow

{% stepper %}
{% step %}
**Define custom fields**

Set up custom fields to store additional contact information for personalization.
{% endstep %}

{% step %}
**Import your contacts**

Upload contacts via CSV, API integration, or third-party tools like Zapier.
{% endstep %}

{% step %}
**Organize into lists**

Group contacts into relevant lists based on your marketing strategy.
{% endstep %}

{% step %}
**Create segments**

Build dynamic segments that automatically update based on contact properties.
{% endstep %}

{% step %}
**Launch campaigns**

Use your organized contacts to send targeted email marketing campaigns.
{% endstep %}
{% endstepper %}

## Import methods

{% tabs %}
{% tab title="CSV Import" %}
**Bulk upload from spreadsheets**

Perfect for migrating existing contact lists or periodic bulk updates.

* Download our CSV template
* Map fields to custom variables
* Import thousands of contacts at once
{% endtab %}

{% tab title="API Integration" %}
**Real-time syncing from your application**

Keep contacts synchronized with your application database.

* RESTful API endpoints
* Webhook support
* Automatic updates
{% endtab %}

{% tab title="Third-party Integrations" %}
**Connect your favorite tools**

Seamlessly integrate with your existing workflow.

* Zapier automation
* Make.com scenarios
* n8n workflows
{% endtab %}
{% endtabs %}

## Important considerations

{% hint style="warning" %}
**Consent requirements:**

You must have explicit consent from recipients before adding them to marketing campaigns. Mailtrap requires confirmation of consent during the import process.
{% endhint %}

{% hint style="info" %}
**Subscription management:**

Once a contact unsubscribes, they cannot be manually resubscribed. They must sign up for your list again to receive marketing emails.
{% endhint %}
