---
title: DigitalOcean DNS Setup
description: >-
  Verify your Mailtrap sending domain in Digital Ocean. Add DNS records for
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

# DigitalOcean

To add and verify a sending domain in Mailtrap, you need access to your domain's DNS records and your domain provider account.

<a href="https://app.gitbook.com/s/S3xyr7ba7aGO19rc8dSK/email-api-smtp/setup/sending-domain" class="button secondary">Sending Domain Setup</a> check it for more details on setting up your sending domain. Continue reading to learn how to add Mailtrap DNS records to DigitalOcean.

{% hint style="info" %}
This guide assumes that your domain is either registered and managed with DigitalOcean or registered elsewhere but points to DigitalOcean.
{% endhint %}

{% stepper %}
{% step %}
**Access Networking and select domain**

Choose Networking in the main menu of the control panel and click the domain you've added to Mailtrap.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/digitalocean-networking-menu.png" alt="DigitalOcean control panel Networking menu with domain selection" width="563"></div>

You'll see the Create new record heading.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/digitalocean-create-new-record.png" alt="DigitalOcean Create new record section" width="563"></div>
{% endstep %}

{% step %}
**View Mailtrap DNS records**

Return to Mailtrap. On the Domain Verification page, you'll see the DNS records you need to add to DigitalOcean. These are Domain Verification, DKIM, DMARC, and Domain Tracking. You'll need the values under Type, Name, and Value.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/namecheap-mailtrap-dns-records.png" alt="Mailtrap domain verification page showing required DNS records" width="563"></div>
{% endstep %}

{% step %}
**Select DNS record type**

Check the type next to each record in Mailtrap and choose a relevant one in DigitalOcean (CNAME or TXT). Mailtrap has four CNAME type records (Domain Verification, DKIM (2), and Custom Tracking Domain) and one TXT type record (DMARC).

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/namecheap-dns-types-categories.png" alt="DNS record types and categories in Mailtrap" width="563"><figcaption><p>DNS Types and Categories in Mailtrap</p></figcaption></figure></div>

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/digitalocean-record-type-selector.png" alt="DigitalOcean DNS record type selector dropdown" width="563"><figcaption><p>DNS record types in DigitalOcean</p></figcaption></figure></div>

{% hint style="info" %}
The SPF check for your mail is covered by the domain verification record. There is no need to add a separate SPF record on your sending domain.
{% endhint %}
{% endstep %}

{% step %}
**Copy DNS record values from Mailtrap**

Copy the Name and Value for each record one by one. You can do this by hovering and clicking each record.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/digitalocean-copy-dns-values.png" alt="Copying DNS record values from Mailtrap" width="563"></div>
{% endstep %}

{% step %}
**Paste values into DigitalOcean**

And paste them into DigitalOcean. Remember that DigitalOcean refers to the Name field as Hostname for all record types. For CNAME type records, it refers to the Value field as Is an Alias of.

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/digitalocean-txt-record-fields.png" alt="DigitalOcean TXT record input form showing Hostname and Value fields" width="563"><figcaption><p>Naming of TXT-type records in DigitalOcean</p></figcaption></figure></div>

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/digitalocean-cname-record-fields.png" alt="DigitalOcean CNAME record input form showing Hostname and Is an Alias of fields" width="563"><figcaption><p>Naming of CNAME-type records in DigitalOcean</p></figcaption></figure></div>
{% endstep %}

{% step %}
**Set TTL and create record**

Use the default value for TTL.

Click Create Record after adding each record in DigitalOcean.
{% endstep %}

{% step %}
**Add all DNS records**

Repeat the process of copying and pasting for each record until you've added all the Mailtrap DNS records to DigitalOcean.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/digitalocean-all-records-added.png" alt="DigitalOcean DNS records list showing all Mailtrap records added" width="375"></div>
{% endstep %}

{% step %}
**Verify DNS records in Mailtrap**

Then, return to Mailtrap. Some records may be verified immediately, while some may take more time. Mailtrap will check the DNS records automatically every hour, but you can force a check by clicking the Re-check DNS Records button.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/namecheap-recheck-dns-records.png" alt="Mailtrap Re-check DNS Records button" width="563"></div>
{% endstep %}

{% step %}
**Confirm verification status**

If you add all the required DNS records correctly, the Status of DNS records will change from Missing to Verified, and the red dots will turn green.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/digitalocean-dns-verified.png" alt="Mailtrap showing all DNS records verified with green status indicators" width="563"></div>
{% endstep %}
{% endstepper %}

{% hint style="info" %}
If you have additional questions, [consult DigitalOcean documentation](https://docs.digitalocean.com/products/networking/dns/how-to/manage-records/) or contact us at [support@mailtrap.io](mailto:support@mailtrap.io).
{% endhint %}
