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

<a href="https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/setup/sending-domain" class="button secondary">Sending Domain Setup</a> check it for more details on setting up your sending domain. Continue reading to learn how to add Mailtrap DNS records to GoDaddy.

{% hint style="info" %}
This guide assumes that your domain is either registered with GoDaddy and uses its nameservers or isn't registered with GoDaddy but uses its nameservers.
{% endhint %}

{% stepper %}
{% step %}
Go to GoDaddy and locate the domain you've added to Mailtrap.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/godaddy-domain-list.png" alt="" width="375"></div>
{% endstep %}

{% step %}
Open the DNS settings and click **Add New Record**.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/godaddy-dns-settings.png" alt="" width="563"></div>
{% endstep %}

{% step %}
On the Domain Verification page in Mailtrap, you'll see the DNS records you need to add to GoDaddy. These are **Domain Verification**, **DKIM**, **DMARC**, and **Domain Tracking**. You'll need the values under **Type**, **Name**, and **Value**. The naming of these records in Mailtrap is the same as in GoDaddy.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/google-cloud-dns-4.png" alt="" width="563"></div>

Make sure you check the type next to each record in Mailtrap and choose a relevant one in GoDaddy. There are **four CNAME type records** (Domain Verification, DKIM (2), and Custom Tracking Domain) and **one TXT type record** (DMARC).

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/google-cloud-dns-5.png" alt="DNS record types and categories in Mailtrap" width="563"><figcaption></figcaption></figure></div>

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/godaddy-dns-type-selector.png" alt="GoDaddy DNS record type selector dropdown" width="375"><figcaption></figcaption></figure></div>

{% hint style="info" %}
The SPF check for your mail is covered by the domain verification record. There is no need to add a separate SPF record on your sending domain.
{% endhint %}
{% endstep %}

{% step %}
Copy the **Name** and **Value** for each record one by one. You can do this by hovering and clicking each record.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/google-cloud-dns-6.png" alt="" width="563"></div>
{% endstep %}

{% step %}
Paste the values into GoDaddy DNS management page.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/godaddy-paste-dns-values.png" alt="Pasting DNS values into GoDaddy record form" width="563"></div>
{% endstep %}

{% step %}
Use the default value for TTL.

Click Save after adding each record in GoDaddy.
{% endstep %}

{% step %}
Repeat the process of copying and pasting for each record until you've added all the Mailtrap DNS records to GoDaddy.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/godaddy-all-dns-records-added.png" alt="" width="563"></div>
{% endstep %}

{% step %}
Some records may be verified immediately, while some may take more time. Mailtrap will check the DNS records automatically every hour, but you can force a check by clicking the Re-check DNS Records button.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/google-cloud-dns-11.png" alt="" width="563"></div>
{% endstep %}

{% step %}
If you add all the required DNS records correctly, the Status of DNS records will change from Missing to Verified, and the red dots will turn green.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/google-cloud-dns-12.png" alt="" width="563"></div>
{% endstep %}
{% endstepper %}

{% hint style="info" %}
If you have additional questions, consult the official [GoDaddy documentation](https://uk.godaddy.com/help/manage-dns-records-680) or contact us at [support@mailtrap.io](mailto:support@mailtrap.io).
{% endhint %}
