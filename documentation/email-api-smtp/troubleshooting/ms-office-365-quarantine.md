---
title: MS Office 365 Threat Management
description: >-
  How to resolve your emails sent from Mailtrap Email API/SMTP being sent to
  Office 365 quarantine.
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

# Office 365 Quarantine

Sometimes transactional messages from Mailtrap (such as email confirmations, invitations to join a sandbox, invoices, etc.) can be sent to Threat Management >> Quarantine by MS Office 365.

### Solution

If you have faced this issue, follow these steps to resolve it:

{% stepper %}
{% step %}
**Access Office 365 Quarantine**

Go to [https://protection.office.com/#/quarantine](https://protection.office.com/#/quarantine).
{% endstep %}

{% step %}
**Select Mailtrap Emails**

Select the emails sent from Mailtrap that are in quarantine.
{% endstep %}

{% step %}
**Release Messages**

Click the **Release messages** button.
{% endstep %}

{% step %}
**Add to Allow List**

Check the **"Add sender to your organization's allow list"** checkbox.

This will prevent future emails from Mailtrap from being quarantined.
{% endstep %}
{% endstepper %}

### Alternative: OAuth Integration

When signing up for Mailtrap, you have the option to use Office 365 account authorization (OAuth) for smooth integration. In this case, email confirmation won't be required and you can avoid quarantine issues altogether.

### Related Articles

* [Getting Started with Email API/SMTP](../setup/sending-domain.md)
* [Email API/SMTP FAQs](../faqs.md)
