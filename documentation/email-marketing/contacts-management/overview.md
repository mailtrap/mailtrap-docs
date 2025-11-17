---
title: Contacts Management Overview
description: >-
  Upload, store, and organize your contacts in email lists to send targeted
  campaigns
icon: user-magnifying-glass
---

# Contacts Management

Mailtrap Contacts allows you to upload and store your contacts on the Mailtrap platform and organize them in different email lists to send targeted campaigns.

## Key Features

{% hint style="success" %}
**Comprehensive Contact Management**

* Import contacts via CSV, API, or third-party integrations
* Organize contacts into targeted lists and segments
* Manage custom fields for personalization
* Track subscription status and engagement
{% endhint %}

## Getting Started

{% columns %}
{% column %}
<i class="fa-solid">:solid:</i>**Custom Fields**

Define custom variables like name, date of birth, or location to personalize your campaigns.

[Learn about Fields →](fields.md)
{% endcolumn %}

{% column %}
<i class="fa-solid">:solid:</i>**Import Contacts**

Bulk import contacts from spreadsheets, sync via API, or use our integrations.

[Upload Contacts →](uploading-contacts.md)
{% endcolumn %}
{% endcolumns %}

{% columns %}
{% column %}
<i class="fa-solid">:solid:</i>**Manage Contacts**

Filter, search, edit, and perform bulk actions on your contact database.

[Manage Contacts →](managing-contacts.md)
{% endcolumn %}

{% column %}
<i class="fa-solid">:solid:</i>**Lists & Segments**

Create dynamic segments for targeted messaging based on contact fields or contacts engagement.

[Lists →](lists.md) | [Segments →](segments.md)
{% endcolumn %}
{% endcolumns %}

## Contact Management Workflow

{% stepper %}
{% step %}
#### Define Custom Fields

Set up custom fields to store additional contact information for personalization.
{% endstep %}

{% step %}
#### Import Your Contacts

Upload contacts via CSV, API integration, or third-party tools like Zapier.
{% endstep %}

{% step %}
#### Organize into Lists

Group contacts into relevant lists based on your marketing strategy.
{% endstep %}

{% step %}
#### Create Segments

Build dynamic segments that automatically update based on contact properties.
{% endstep %}

{% step %}
#### Launch Campaigns

Use your organized contacts to send targeted email marketing campaigns.
{% endstep %}
{% endstepper %}

## Import Methods

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

## Important Considerations

{% hint style="warning" %}
**Consent Requirements** You must have explicit consent from recipients before adding them to marketing campaigns. Mailtrap requires confirmation of consent during the import process.
{% endhint %}

{% hint style="info" %}
**Subscription Management** Once a contact unsubscribes, they cannot be manually resubscribed. They must sign up for your list again to receive marketing emails.
{% endhint %}
