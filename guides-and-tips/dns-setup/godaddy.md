---
title: GoDaddy DNS Setup
description: >-
  Verify your Mailtrap sending domain in GoDaddy. Add DNS records for DKIM/DMARC
  verification, pass compliance, and start sending emails.
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

# GoDaddy

To add and verify a sending domain in Mailtrap, you need access to your domain's DNS records and your domain provider account.

<a href="./" class="button secondary">Sending Domain Setup</a> check it for more details on setting up your sending domain. Continue reading to learn how to add Mailtrap DNS records to GoDaddy.

{% hint style="info" %}
This guide assumes that your domain is either registered with GoDaddy and uses its nameservers or isn't registered with GoDaddy but uses its nameservers.
{% endhint %}

{% stepper %}
{% step %}
**Locate your domain**

Go to GoDaddy and locate the domain you've added to Mailtrap.

<div align="left" data-with-frame="true"><img src="../../documentation/.gitbook/assets/godaddy-domain-list (1).png" alt="GoDaddy domain list with Manage button" width="375"></div>
{% endstep %}

{% step %}
**Open DNS settings**

Open the DNS settings and click Add New Record.

<div align="left" data-with-frame="true"><img src="../../documentation/.gitbook/assets/godaddy-add-new-record (1).png" alt="GoDaddy DNS settings page with Add New Record button" width="563"></div>
{% endstep %}

{% step %}
**View Mailtrap DNS records**

Return to Mailtrap. On the Domain Verification page, you'll see the DNS records you need to add to GoDaddy. These are Domain Verification, DKIM, DMARC, and Domain Tracking. You'll need the values under Type, Name, and Value. The namings of these records in Mailtrap are the same as in GoDaddy.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/google-cloud-dns-4 (1).png" alt="Mailtrap domain verification page showing required DNS records" width="563"></div>

Make sure you check the type next to each record in Mailtrap and choose a relevant one in GoDaddy. There are four CNAME type records (Domain Verification, DKIM (2), and Custom Tracking Domain) and one TXT type record (DMARC).

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/google-cloud-dns-5 (1).png" alt="DNS record types and categories in Mailtrap" width="563"><figcaption><p>DNS Types and Categories in Mailtrap</p></figcaption></figure></div>

<div align="left" data-with-frame="true"><figure><img src="../../documentation/.gitbook/assets/godaddy-dns-record-types (1).png" alt="GoDaddy DNS record type selector dropdown" width="375"><figcaption><p>DNS record types in GoDaddy</p></figcaption></figure></div>

{% hint style="info" %}
The SPF check for your mail is covered by the domain verification record. There is no need to add a separate SPF record on your sending domain.
{% endhint %}
{% endstep %}

{% step %}
**Copy DNS record values from Mailtrap**

Copy the Name and Value for each record one by one. You can do this by hovering and clicking each record.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/google-cloud-dns-6 (1).png" alt="Copying DNS record values from Mailtrap" width="563"></div>
{% endstep %}

{% step %}
**Paste values into GoDaddy**

And paste them into GoDaddy.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/godaddy-paste-dns-values.png" alt="Pasting DNS values into GoDaddy record form" width="563"></div>
{% endstep %}

{% step %}
**Set TTL and save**

Use the default value for TTL.

Click Save after adding each record in GoDaddy.
{% endstep %}

{% step %}
**Add all DNS records**

Repeat the process of copying and pasting for each record until you've added all the Mailtrap DNS records to GoDaddy.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/godaddy-all-dns-records-added.png" alt="GoDaddy DNS records list showing all Mailtrap records added" width="563"></div>
{% endstep %}

{% step %}
**Verify DNS records in Mailtrap**

Then, return to Mailtrap. Some records may be verified immediately, while some may take more time. Mailtrap will check the DNS records automatically every hour, but you can force a check by clicking the Re-check DNS Records button.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/google-cloud-dns-11 (1).png" alt="Mailtrap Re-check DNS Records button" width="563"></div>
{% endstep %}

{% step %}
**Confirm verification status**

If you add all the required DNS records correctly, the Status of DNS records will change from Missing to Verified, and the red dots will turn green.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/google-cloud-dns-12 (1).png" alt="Mailtrap showing all DNS records verified with green status indicators" width="563"></div>
{% endstep %}
{% endstepper %}

{% hint style="info" %}
If you have additional questions, [consult GoDaddy documentation](https://uk.godaddy.com/help/manage-dns-records-680) or contact us at [support@mailtrap.io](mailto:support@mailtrap.io).
{% endhint %}
