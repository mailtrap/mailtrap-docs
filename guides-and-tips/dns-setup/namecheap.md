---
title: Namecheap DNS Setup
description: >-
  Verify your Mailtrap sending domain in Namecheap. Add DNS records for
  DKIM/DMARC verification, pass compliance, and start sending emails.
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

To add and verify a sending domain in Mailtrap, you need access to your domain's DNS records and your domain provider account.

<a href="./" class="button secondary">Sending Domain Setup</a> check it for more details on setting up your sending domain. Continue reading to learn how to add Mailtrap DNS records to Namecheap.

{% hint style="info" %}
This guide assumes that your domain is either registered with Namecheap and uses its nameservers or isn't registered with Namecheap but uses its nameservers.
{% endhint %}

{% stepper %}
{% step %}
## Locate and manage domain

Go to Namecheap, locate the domain you've added to Mailtrap on the dashboard, and click Manage.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/namecheap-domain-dashboard.png" alt="Namecheap dashboard showing domain list with Manage button" width="563"></div>
{% endstep %}

{% step %}
## Navigate to Advanced DNS

Navigate to the Advanced DNS tab.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/namecheap-advanced-dns-tab.png" alt="Namecheap Advanced DNS tab in domain settings" width="563"></div>
{% endstep %}

{% step %}
## Add new record

Click Add New Record.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/namecheap-add-new-record-button.png" alt="Namecheap Add New Record button" width="563"></div>
{% endstep %}

{% step %}
## View Mailtrap DNS records

Return to Mailtrap. On the Domain Verification page, you'll see the DNS records you need to add to Namecheap. These are Domain Verification, DKIM, DMARC, and Domain Tracking. You'll need the values under Type, Name, and Value.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/namecheap-mailtrap-dns-records.png" alt="Mailtrap domain verification page showing required DNS records" width="563"></div>

Make sure you check the type next to each record in Mailtrap and choose a relevant one in Namecheap. There are four CNAME type records (Domain Verification, DKIM (2), and Custom Tracking Domain) and one TXT type record (DMARC).

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/namecheap-dns-types-categories.png" alt="DNS record types and categories in Mailtrap" width="563"><figcaption><p>DNS Types and Categories in Mailtrap </p></figcaption></figure></div>

{% hint style="info" %}
The SPF check for your mail is covered by the domain verification record. There is no need to add a separate SPF record on your sending domain.
{% endhint %}
{% endstep %}

{% step %}
## Copy DNS record values from Mailtrap

Copy the Name and Value for each record one by one. You can do this by hovering and clicking each record.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/namecheap-copy-record-values.png" alt="Copying DNS record values from Mailtrap" width="563"></div>
{% endstep %}

{% step %}
## Paste values into Namecheap

And paste them into Namecheap. Remember that Namecheap refers to the Name field as Host.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/namecheap-paste-host-value.png" alt="Namecheap DNS record form showing Host and Value fields" width="563"></div>
{% endstep %}

{% step %}
## Set TTL

Use the default value for TTL.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/namecheap-ttl-default.png" alt="Namecheap TTL field with default value" width="375"></div>
{% endstep %}

{% step %}
## Add all DNS records

Repeat the process of copying, pasting, and clicking Add New Record for each record until you've added all the Mailtrap DNS records to Namecheap. Click Save All Changes.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/namecheap-save-all-changes.png" alt="Namecheap Save All Changes button" width="375"></div>
{% endstep %}

{% step %}
## Verify DNS records in Mailtrap

Then, return to Mailtrap. Some records may be verified immediately, while some may take more time. Mailtrap will check the DNS records automatically every hour, but you can force a check by clicking the Re-check DNS Records button.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/namecheap-recheck-dns-records.png" alt="Mailtrap Re-check DNS Records button" width="563"></div>
{% endstep %}

{% step %}
## Confirm verification status

If you add all the required DNS records correctly, the Status of DNS records will change from Missing to Verified, and the red dots will turn green.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/namecheap-verified-dns-status.png" alt="Mailtrap showing all DNS records verified with green status indicators" width="563"></div>
{% endstep %}
{% endstepper %}

{% hint style="info" %}
If you have additional questions, [consult Namecheap documentation](https://www.namecheap.com/support/knowledgebase/article.aspx/434/2237/how-do-i-set-up-host-records-for-a-domain/) or contact us at [support@mailtrap.io](mailto:support@mailtrap.io).
{% endhint %}
