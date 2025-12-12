---
title: Feedback Loops
description: >-
  Learn how Mailtrap integrates with popular Feedback Loops (FBLs) to track spam
  complaints from major mailbox providers including Outlook, Yahoo, and more.
icon: message
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

# Feedback Loops

Mailtrap is integrated with the majority of popular Feedback Loops (FBLs) to gather information about spam complaints.

{% hint style="info" %}
Remember that Gmail doesn’t provide spam complaint information per message.
{% endhint %}

Still, Mailtrap adds `Feedback-ID` to all emails sent to Gmail. If you specify Email Categories, we add it to the header as a part of the category. Yet, it’s up to Gmail to show that info in your Google Postmaster. Read more about the feedback header [here](https://support.google.com/a/answer/6254652?hl=en).

Our Deliverability Team can review aggregated data for Spam Rates for Gmail recipients daily if you provide us with view rights for Google Postmaster. This service is available for our paid customers. Please contact our support team for the details.

<a href="mailto:support@mailtrap.io" class="button secondary">Contact Support</a>

<details>

<summary>The list of FBLs Mailtrap is integrated with:</summary>

* Microsoft Outlook
* Yahoo! Mail
* Bluetie
* Comcast
* Fastmail
* gandi.net
* Liberty Global (Chello, UPC, and UnityMedia)
* Locaweb
* Mail.ru
* OpenSRS/Hostedmail (Tucows)
* Rackspace
* Seznam
* SFR
* SilverSky
* Swisscom
* Synacor
* Telecom Italia
* Telenet
* Telenor
* Telstra
* Terra
* UOL
* Virgilio
* Virgin Media
* Yandex
* Ziggo

</details>

While using our services, Mailtrap may get alerts from these FBLs if your recipients submit spam complaints. You'll see them in your [Stats](statistics/stats-dashboard.md) and may receive them via [Webhooks](setup/sending-domain.md#optional-webhooks-4hmes).

We also support the `CFBL-Address` header as per [RFC 9477](https://www.rfc-editor.org/rfc/rfc9477.html). However, it’s still experimental, and not all mailbox providers support it.
