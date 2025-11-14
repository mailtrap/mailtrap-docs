---
description: >-
  Set up your sending domain in Mailtrap. Add DNS records, verify
  SPF/DKIM/DMARC, pass compliance, and start sending emails in minutes.
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

# Sending Domain Setup

<table data-view="cards"><thead><tr><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td>AWS Route 53</td><td><a href="aws-route-53.md">aws-route-53.md</a></td></tr><tr><td>Cloudflare</td><td><a href="cloudflare.md">cloudflare.md</a></td></tr><tr><td>Digital Ocean</td><td><a href="digitalocean.md">digitalocean.md</a></td></tr><tr><td>GoDaddy</td><td><a href="godaddy.md">godaddy.md</a></td></tr><tr><td>Google Cloud DNS</td><td><a href="google-cloud-dns.md">google-cloud-dns.md</a></td></tr><tr><td>Google Domains</td><td><a href="google-domains.md">google-domains.md</a></td></tr><tr><td>Namecheap</td><td><a href="namecheap.md">namecheap.md</a></td></tr></tbody></table>

### Setting up your domain  <a href="#setting-up-your-own-domain-ys86q" id="setting-up-your-own-domain-ys86q"></a>

{% hint style="info" %}
_In the example below, we’ll be using GoDaddy._
{% endhint %}

{% stepper %}
{% step %}
#### Add Domain  <a href="#step-1-add-domain-woixs" id="step-1-add-domain-woixs"></a>

* Navigate to Sending Domains in the left navigation panel.

<div align="left" data-full-width="false" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/pwnfi0PrV_iw_1wMFjqda0X1iwah7Q2Gb-4EBnErhKhQsk-4W2CM3eDaeV2kCjxWnjhEAOHkI9caXtT0Xm5-kdc-CFlD76FhnJ-lUOurpOd6S9u2qVJd7hieoIXCzujQtfT_-QmJoyfcXQouQm4eoaw" alt="" width="375"></div>

* Click Add Domain.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/WH64hwf9AJ23KGlhisXbwVBjNZ-PTnFXLO0LS0ooVhGNjwHs_kLYT5n9CKMHLlLWIUpcc8Jl6qSlA14BMWyonem5nclTltPb1cK5s-ukI_wu7YDz0C2I26rKiA1nzUM2L1bqmdPKFg4JcYe0G0RIDdc" alt="" width="375"></div>

* Type in the domain from which you want to send emails and click Add. Remember that you should be the domain owner with access to its DNS records/have someone with access to DNS records.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/73MNY012XVDgAJ_RO9lIqVX4c5S3pW_-Q47uc2gpmUyYe2SoldAB9fNZiMxXO1Ygq-BqwWpuWUtty482f4v5NT6pz730HdBVoBWo7062174lJgB-0MW35ba5f6MD-jzMK2tQCrFsFNIJHtLkRPGUsAg" alt=""></div>

* After this step, you’ll see the Domain Verification page.
{% endstep %}

{% step %}
#### Domain Verification   <a href="#step-2-domain-verification-04egm" id="step-2-domain-verification-04egm"></a>

At this stage, you need to verify the domain. You have two options:

* Send domain verification instructions to your admin or developer;
* Or verify the domain yourself if you have access to your domain’s DNS records (your domain provider account).

{% hint style="success" %}
To send instructions to your admin or developer, enter their email address and click Send Instructions.
{% endhint %}

<div align="left" data-with-frame="true"><img src="https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/673c5d4e772e5b7dd60d8548/file-a5cMdgPIul.png" alt=""></div>

To verify the domain yourself, follow these steps:

* Go to your domain provider and locate the domain you’ve added to Mailtrap.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/HHSh2cp5Q3EVMaN4XEyw1B4CCQJyRNWyks6FeCBPDBs1oW1VE3gs1LzcMApbZZ1lcTyVWfgBX7wSJldGQcp1FrV1_IcJzpQtoOwVQASDKm2gtEdAhhp5lEOPOHRDAbWAqdrf2snAcLhfcU_gP167p9c" alt="" width="563"></div>

* Open the DNS settings and click Add New Record.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/1LdTCB6Q6BurqNfwgwVJZxFjSvsuaA_73rQQHkjGPIANd8MwzRO_X_zaZKV2hYchfpbEOdUYseUIbmwSlMksd2vRSu10tP7HuchVx1EFkgX52rHUqdwy8ZSbY7-Il4v62eCIqZnI7NcBnbRB1PmwS-U" alt="" width="563"></div>

* Return to Mailtrap. On the Domain Verification page, you’ll see the DNS records you need to add to your domain provider. These are Domain Verification, DKIM, SPF, DMARC, and Domain Tracking. You’ll need the values under Type, Name, and Value. The namings of these records in Mailtrap are the same as in most domain providers but may differ slightly depending on the provider.

<div align="left" data-with-frame="true"><img src="https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/673c5da7442d517d60d26c5f/file-kl0nGsYGqW.png" alt="" width="563"></div>

* Make sure you check the type next to each record in Mailtrap and choose a relevant one in your domain provider. There are four CNAME type records (Domain Verification, DKIM (2), and Custom Tracking Domain) and two TXT type records (SPF and DMARC). Read [this article](https://help.mailtrap.io/article/79-dns-records) for detailed information on each DNS record.

<div align="left" data-with-frame="true"><figure><img src="https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/673c5dbd772e5b7dd60d854b/file-NxGu99kleR.png" alt="DNS Types and Categories in Mailtrap" width="563"><figcaption><p>DNS Types and Categories in Mailtrap</p></figcaption></figure></div>

<div align="left" data-with-frame="true"><figure><img src="https://lh7-us.googleusercontent.com/l3vQpGEx7u2Cr35_ekYw8k9NzZskYM_X6Ax4ce1VrR7Zhs1e4EySbQTeUVbIQLGJiSFUDzcnTqscQa9065MWGJyjUngoU3LdX8yrJjiAv9UTZoLEIDxV5_NlcgG_NhMY3GcwVqY40yawR0XOYLIdafs" alt="" width="563"><figcaption><p>DNS record types in GoDaddy </p></figcaption></figure></div>

{% hint style="info" %}
_Note that you should have only one SPF record. So, if you already have one for your domain, update its value to include Mailtrap._
{% endhint %}

* Copy the Name and Value for each record one by one. You can do this by hovering and clicking each record.

<div align="left" data-with-frame="true"><img src="https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/673c5df7253ee02cb10711ad/file-o5XTkj8phs.png" alt="" width="563"></div>

* Paste them into your domain provider.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/JZRl_aMMfhdj2qddwJU20Cmz_Ge8Ygw1vKckO2sClRJ07oZrolZinutwmA787OlxUZmoGD7GOdPvC_EBuzvS0jrCoDs8SEUrR6PxzsQZ4BN5_DapPC6kto9EmzDdhG3n2IrcsPDbsmxUMSVMaM27MXQ" alt="" width="563"></div>

* Click Save after adding each record in your domain provider.
* Repeat the process of copying and pasting for each record until you’ve added all the Mailtrap DNS records to your domain provider.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/5HdxUfrrjClIVHKBMc_NwFwNoeQMEq2Eo2281J5fBjzfgQjBY8LvzqzuzoH8N9ymPFRINoLIov_bzSNGtNTZws1On6S2u5tQkYkXRjpzfZI41yum4okAXERkjQFL6bI2hWVSxV3ioYQoGK9cxVh-Hm8" alt="" width="563"></div>

* Then, return to Mailtrap. Some records may be verified immediately, while some may take more time. Mailtrap will check the DNS records automatically every hour, but you can force a check by clicking the Re-check DNS Records button.

<div align="left" data-with-frame="true"><img src="https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/673c5edf1f08a9604200325b/file-IhJ2jEg6pC.png" alt=""></div>

* If you add all the required DNS records correctly, the Status of DNS records will change from Missing to Verified, and the red dots will turn green.

<div align="left" data-with-frame="true"><img src="https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/673c6307268fb643f63a5b37/file-GMKtJImPDV.png" alt="" width="563"></div>

* Once the DNS records are verified, you’ll be taken to the next step - Compliance Check. 

**Several notes:**

* Some domain providers don't allow setting ‘@’ for SPF records. In this case, please use your own domain name "example.com" instead of '@'.
* Some domain providers require a postfix format of the DKIM record. If that’s the case, replace `rwmt1._domainkey` with `rwmt1._domainkey.yourdomain.com` . Repeat the process for `rwmt2._domainkey` , changing the name to `rwmt2._domainkey.yourdomain.com` .
* If you’re asked to set TTL, use the default value as indicated under the TTL field on the Domain Verification page in Mailtrap.
{% endstep %}

{% step %}
#### Company / Personal Information

After adding your DNS records, click on “Fill in Compliance Form” to complete a short form where you’ll be asked to provide either business or personal information.

Please keep in mind that it’s crucial to provide correct information corresponding to your company registration details. It is crucial in order to comply with international regulations. Those information may also be automatically added to an email footer of promotional emails sent from your domain.

{% hint style="success" %}
_Tip: If you’ve provided this information before, you won’t be asked to fill it in again._
{% endhint %}

<div align="center" data-with-frame="true"><figure><img src="../../.gitbook/assets/image.png" alt="" width="355"><figcaption></figcaption></figure></div>

You can switch between personal and business information only once, meaning that you cannot change it after the form is submitted.

<div align="left" data-with-frame="true"><figure><img src="../../.gitbook/assets/image (1).png" alt="" width="307"><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
#### Compliance Check <a href="#step-3-compliance-check-v3fbr" id="step-3-compliance-check-v3fbr"></a>

Compliance Check is a process of checking every new domain added to Mailtrap.

Once all the DNS records are successfully verified, your domain will undergo an automatic review. This usually takes a couple of minutes. If your domain is verified at this stage, you’ll see the Verified badge next to your domain and below Compliance Check, and you’ll be able to start sending the emails. You’ll also receive an email informing you that your domain is ready for sending emails.

Some domains may be selected for additional checks. If so, we’ll ask you to fill out a simple Compliance Form and answer a few questions about your business, sending goals, etc. You’ll see a notification under Compliance Check and a link to the form.

<div data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/3xDxFQRfiMe2_5WydJi8GZujVTSRG3vHxgby5nYhvc5wtJfSF9HiQfNuh8pbXOAhKNyh9_-8MAxowibVsmfl4IJzUN6xPjxWlfldYWRWOb4Oitcfz5dYM8x44Jhtoko2j4jG8YOCJALaGoUv1V4zJRw" alt="" width="563"></div>

We’ll email you if we need additional information from you. If all the checks are successful at this stage, your domain will be verified.

In some cases, your domain may be selected for manual verification. This is the final check before your domain is verified. The length of the manual verification depends on how fast you reply to our emails. If successful, you’ll see Verified status. If not, you’ll see a Rejected badge next to your domain and a message under Compliance Check. In case of any questions about the reasons for rejection, please contact our support team at [support@mailtrap.io](mailto:support@mailtrap.io).

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/image (2).png" alt="" width="563"><figcaption></figcaption></figure></div>
{% endstep %}
{% endstepper %}

### (Optional) Tracking Settings <a href="#optional-tracking-settings-ffi49" id="optional-tracking-settings-ffi49"></a>

An optional step is to change the tracking settings. By default, Mailtrap tracks email opens for each email sent. You can also enable click tracking.

{% hint style="info" %}
_Click tracking and custom domain for clicks tracking are available only for paid accounts._
{% endhint %}

<div data-with-frame="true"><img src="https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/673c6593442d517d60d26c65/file-vHR7EJAfx8.png" alt=""></div>

With tracking enabled, you will find the open and click rates in the Analytics reports. [Read this article](../statistics/) for a detailed breakdown of Statistics.

1. Navigate to the Tracking Settings tab.

<div align="left" data-with-frame="true"><img src="https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/673c65d3268fb643f63a5b3c/file-pwnq75lN1S.png" alt="" width="563"></div>

2. Toggle the switch next to Track Opened Emails to enable or disable tracking opens. Mailtrap tracks email opens via an invisible pixel. It’s added to each message sent from your account. When an email is opened, a pixel is loaded, and an ‘open’ event is recorded. Each of these events will be visible in [Email Logs](../statistics/email-logs.md).

{% hint style="info" %}
_Some mailbox providers, browsers, and extensions block invisible pixels. Users can also choose not to display images, or a solution they use to retrieve emails may not support images by default. In each of these cases, an ‘open’ event won’t be recorded even if an email is opened._
{% endhint %}

<div align="left" data-with-frame="true"><img src="https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/673c6611772e5b7dd60d8559/file-tvKTW9kyVQ.png" alt="" width="563"></div>

3. If you're a paid user, toggle the switch next to Track Clicks to enable or disable tracking clicks. If you enable click tracking, the toggle for Custom Domain for Clicks Tracking will be switched on automatically. That way, all links will be redirected through your domain (mt-link.yourdomain.com). And if you verified all the records correctly in Step 2, Domain Tracking will also be verified and ready to use.

<div align="left" data-with-frame="true"><img src="https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/673c66321f08a96042003264/file-vfPKzvZwVC.png" alt="" width="563"></div>

### Unsubscribe Settings <a href="#unsubscribe-settings-ekyqh" id="unsubscribe-settings-ekyqh"></a>

You can also configure unsubscribe settings.

Unsubscribe links are mandatory for bulk emails as per privacy laws. If your emails don’t include an unsubscribe link, Mailtrap will add an Unsubscribe Footer automatically. This is what it will look like:

<div align="left" data-with-frame="true"><img src="https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/673c6657772e5b7dd60d855a/file-h4zAxojjdh.png" alt="" width="563"></div>

To add an unsubscribe link anywhere in your template, include this tag in your HTML template: `<a href="__unsubscribe_url__">unsubscribe</a>` . Mailtrap will render a clickable link in your email.

Unsubscribe Footer and Links are optional for transactional emails and are switched off by default.

However, if you want to, you can still add an Unsubscribe Footer to your transactional emails by toggling the switch On under Unsubscribe Footer for Transactional emails or adding an HTML tag mentioned above.

<div data-with-frame="true"><img src="https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/673c6686268fb643f63a5b3d/file-rwwC9AJ3wi.png" alt=""></div>

If you’d like, you can mix both approaches - automatically add a footer to emails sent from one domain and do it manually (when applicable) for emails sent from another domain.

If an end-user uses an unsubscribe link, Mailtrap will reject any future emails sent to this address from this particular domain. You can quickly find all such emails in the Email Logs by filtering by a “reject” event.

You will still be able to email them using other domains or subdomains added to your Mailtrap account.

For that reason, it’s worth having different domains or subdomains for different types of emails. This way, users can, for example, unsubscribe from your bulk or marketing messages while still receiving vital transactional messages.

### (Optional) Webhooks <a href="#optional-webhooks-4hmes" id="optional-webhooks-4hmes"></a>

Lastly, you can set up webhooks to receive event information almost real-time.

<div align="left" data-with-frame="true"><img src="https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/679a619ec72d0b603e83468f/file-nao4bkR40r.png" alt="" width="563"></div>

Click the Add New Webhook button, choose the Sending Stream, paste the webhook URL (your endpoint) into the designated field, select the events you want to listen to, and then test the setup.

<div align="left" data-with-frame="true"><img src="https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/679a63312c51514a3dd8a240/file-J489GncXKV.png" alt="" width="563"></div>

Mailtrap also allows you to batch up to 500 events within a webhook; that is - group all events under one object, and thus save on computing power.

To read more about webhooks setup, events structure, and batching, [check this article](https://help.mailtrap.io/article/102-webhooks).

### Useful tips <a href="#sending-domains-j_1ht" id="sending-domains-j_1ht"></a>

After completing the setup process, you can always return to the Sending Domains tab to add any additional domains or subdomains. If you, for example, misspelled a domain, you’ll need to delete it and re-add it with the correct spelling.

{% hint style="info" %}
_You can’t create any additional demo domains, but you can delete the existing one if needed._
{% endhint %}

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/Y_nH9YF60dJmeRh-BlyReoA7spk7_ll7ICEP5DYVHY74ImUobDFI8cnLSmP-QZBpO3_hHSXJG1VVOH5x-vq4s3-tg9Fq-feRp884RF8XUOtVuiAYrLQ3Yig6cZBx44behNkMnnQIjDAsZ_Qx2X5Hp-k" alt="" width="563"></div>

Remember that the domain with the Demo badge can be used to send emails only to the email address you registered with.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/www7l5PULBizvKM1SASk9vvcgSUmWLv8QGVZIYDBeoEXiMShWVZ2w9cPpu3a2G0SiGHlWcKjs1BAabtVQpYcgbGOHgljnePMYBNvHGc6Nu-Sh1WJs8BWVr78D8Tot3ZSjFjfgQF0OJzcqCTg6djVBeU" alt="" width="375"></div>

You can send emails to your recipients only from domains that have Verified status. If the status is Pending or Rejected, you won’t be able to send emails.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/yF7CMu9oSErVTH2ufQuvFG83bPZWqF_ToXbyyqFh9KlxaNK3beYp0x86gvHFOdkpy8__K53wEQskTJ7D55aWusWExVJxTf7AUJx3ku2XwLGmSgeoCgQrqWPo4i9lEeEk2lhQvoYJ7xj2QI7TdiLj68M" alt="" width="375"></div>

From the Sending Domains menu, you can also delete the domains, subdomains, or the demo domain you no longer use. Just press the bin icon next to the domain. This will remove the domain from the list, and you won’t be able to send any further emails until you add and verify it again.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/JIy5_JitKlFwtRMbCCm9ieErt5xQknRyOLo163VHKy9Mx1oeYcHm0oSITRuF2OoWawwLy7S0E1-hA0Ac_njDIbQhEsX_sVZ4aZ4o9wzZDupXRyq328vxX8aKZ0z-stqZ3VAJyfIKyYbEUvVVCYFmTOw" alt="" width="563"></div>

Note that removing a domain won’t remove it from your Mailtrap account completely. It will still appear, for example, in analytics, and will be displayed with the (deleted) suffix, just like in the example below:

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/zYl0PXWMs8JTwi0NMxZLzU5SsEkuS4wD6saHEU7QvciCNevKB8XLnb2iIpT0WzyJL6mlsFITdyul85ePq_1S0tWIw9Qsh1_97U7RzWri99h4fGL5gopQmLEipIftoPeEsgKO6JnqVk-JAI9ONmTqrZE" alt="" width="375"></div>

We do this to preserve your historical stats that would otherwise be lost.
