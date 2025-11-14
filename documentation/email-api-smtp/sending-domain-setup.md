---
title: Sending Domain Setup
description: >-
  Set up your sending domain in Mailtrap. Add DNS records, verify
  SPF/DKIM/DMARC, pass compliance, and start sending emails in minutes.
---

<table data-view="cards"><thead><tr><th></th><th data-type="content-ref"></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td>AWS Route 53</td><td><a href="https://app.gitbook.com/s/gkNigAKiqQtQub1GOdjY/dns-setup/aws-route-53">AWS Route 53</a></td><td><a href="../../guides-and-tips/dns-setup/aws-route-53.md">aws-route-53.md</a></td></tr><tr><td>Cloudflare</td><td></td><td><a href="../../guides-and-tips/dns-setup/cloudflare.md">cloudflare.md</a></td></tr><tr><td>Digital Ocean</td><td></td><td><a href="../../guides-and-tips/dns-setup/digitalocean.md">digitalocean.md</a></td></tr><tr><td>GoDaddy</td><td></td><td><a href="../../guides-and-tips/dns-setup/godaddy.md">godaddy.md</a></td></tr><tr><td>Google Cloud DNS</td><td></td><td><a href="../../guides-and-tips/dns-setup/google-cloud-dns.md">google-cloud-dns.md</a></td></tr><tr><td>Google Domains</td><td></td><td><a href="../../guides-and-tips/dns-setup/google-domains.md">google-domains.md</a></td></tr><tr><td>Namecheap</td><td></td><td><a href="../../guides-and-tips/dns-setup/namecheap.md">namecheap.md</a></td></tr></tbody></table>

### Setting up your domain <a href="#setting-up-your-own-domain-ys86q" id="setting-up-your-own-domain-ys86q"></a>

{% hint style="info" %}
In the example below, we'll be using GoDaddy.
{% endhint %}

{% stepper %}
{% step %}
**Add Domain**

* Navigate to Sending Domains in the left navigation panel.

<figure><img src="../.gitbook/assets/sending-domains-navigation-menu.png" alt="Sending Domains navigation menu in Mailtrap"><figcaption><p>Sending Domains navigation menu</p></figcaption></figure>

* Click Add Domain.

<figure><img src="../.gitbook/assets/sending-domains-add-domain-button.png" alt="Add Domain button in Sending Domains page"><figcaption><p>Add Domain button</p></figcaption></figure>

* Type in the domain from which you want to send emails and click Add. Remember that you should be the domain owner with access to its DNS records/have someone with access to DNS records.

<figure><img src="../.gitbook/assets/bulk-add-domain-name (1).png" alt="Add Domain Name form with domain input field"><figcaption><p>Add Domain Name form</p></figcaption></figure>

* After this step, you’ll see the Domain Verification page.
{% endstep %}

{% step %}
**Domain Verification**

At this stage, you need to verify the domain. You have two options:

* Send domain verification instructions to your admin or developer;
* Or verify the domain yourself if you have access to your domain’s DNS records (your domain provider account).

{% hint style="success" %}
To send instructions to your admin or developer, enter their email address and click Send Instructions.
{% endhint %}

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/sending-domains-email-to-admin.png" alt="Send domain verification instructions form with email address field and Send Instructions button"></div>

To verify the domain yourself, follow these steps:

* Go to your domain provider and locate the domain you've added to Mailtrap.

<figure><img src="../.gitbook/assets/godaddy-domain-list.png" alt="GoDaddy domain list showing mailtrap.club domain"><figcaption><p>GoDaddy domain list</p></figcaption></figure>

* Open the DNS settings and click Add New Record.

<figure><img src="../../guides-and-tips/.gitbook/assets/godaddy-add-new-record (1).png" alt="GoDaddy DNS Management with Add New Record button"><figcaption><p>GoDaddy DNS Management - Add New Record</p></figcaption></figure>

* Return to Mailtrap. On the Domain Verification page, you'll see the DNS records you need to add to your domain provider. These are Domain Verification, DKIM, SPF, DMARC, and Domain Tracking. You'll need the values under Type, Name, and Value. The namings of these records in Mailtrap are the same as in most domain providers but may differ slightly depending on the provider.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/sending-domains-dns-records-list.png" alt="DNS records list showing Domain Verification, DKIM, SPF, DMARC and Domain Tracking records with Type, Name and Value columns" width="563"></div>

* Make sure you check the type next to each record in Mailtrap and choose a relevant one in your domain provider. There are four CNAME type records (Domain Verification, DKIM (2), and Custom Tracking Domain) and two TXT type records (SPF and DMARC).

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/sending-domains-dns-types-categories.png" alt="DNS Types and Categories in Mailtrap showing CNAME and TXT record types" width="563"><figcaption><p>DNS Types and Categories in Mailtrap</p></figcaption></figure></div>

<figure><img src="../../guides-and-tips/.gitbook/assets/godaddy-dns-record-types (1).png" alt="DNS record type dropdown in GoDaddy showing CNAME selected"><figcaption><p>DNS record types in GoDaddy</p></figcaption></figure>

{% hint style="info" %}
Note that you should have only one SPF record. So, if you already have one for your domain, update its value to include Mailtrap.
{% endhint %}

* Copy the Name and Value for each record one by one. You can do this by hovering and clicking each record.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/sending-domains-copy-button.png" alt="DNS record with copy button highlighted showing how to copy Name and Value" width="563"></div>

* Paste them into your domain provider.

<figure><img src="../.gitbook/assets/godaddy-dns-new-record-form.png" alt="GoDaddy DNS new record form with CNAME type, name, and value fields"><figcaption><p>GoDaddy DNS new record form</p></figcaption></figure>

* Click Save after adding each record in your domain provider.
* Repeat the process of copying and pasting for each record until you've added all the Mailtrap DNS records to your domain provider.

<figure><img src="../.gitbook/assets/godaddy-dns-all-records-added.png" alt="GoDaddy DNS records table showing all Mailtrap DNS records added"><figcaption><p>All Mailtrap DNS records added in GoDaddy</p></figcaption></figure>

* Then, return to Mailtrap. Some records may be verified immediately, while some may take more time. Mailtrap will check the DNS records automatically every hour, but you can force a check by clicking the Re-check DNS Records button.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/sending-domains-dns-records-to-add.png" alt="Domain verification page showing DNS records with Missing status and Re-check DNS Records button"></div>

* If you add all the required DNS records correctly, the Status of DNS records will change from Missing to Verified, and the red dots will turn green.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/sending-domains-godaddy-domain-list.png" alt="DNS records showing Verified status with green checkmarks" width="563"></div>

* Once the DNS records are verified, you’ll be taken to the next step - Compliance Check.

**Several notes:**

* Some domain providers don't allow setting ‘@’ for SPF records. In this case, please use your own domain name "example.com" instead of '@'.
* Some domain providers require a postfix format of the DKIM record. If that’s the case, replace `rwmt1._domainkey` with `rwmt1._domainkey.yourdomain.com` . Repeat the process for `rwmt2._domainkey` , changing the name to `rwmt2._domainkey.yourdomain.com` .
* If you’re asked to set TTL, use the default value as indicated under the TTL field on the Domain Verification page in Mailtrap.
{% endstep %}

{% step %}
**Company / Personal Information**

After adding your DNS records, click on “Fill in Compliance Form” to complete a short form where you’ll be asked to provide either business or personal information.

Please keep in mind that it’s crucial to provide correct information corresponding to your company registration details. It is crucial in order to comply with international regulations. Those information may also be automatically added to an email footer of promotional emails sent from your domain.

{% hint style="success" %}
Tip: If you've provided this information before, you won't be asked to fill it in again.
{% endhint %}

<div align="center" data-with-frame="true"><figure><img src="../.gitbook/assets/image.png" alt="" width="355"><figcaption></figcaption></figure></div>

You can switch between personal and business information only once, meaning that you cannot change it after the form is submitted.

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/image (1).png" alt="" width="307"><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
**Compliance Check**

Compliance Check is a process of checking every new domain added to Mailtrap.

Once all the DNS records are successfully verified, your domain will undergo an automatic review. This usually takes a couple of minutes. If your domain is verified at this stage, you’ll see the Verified badge next to your domain and below Compliance Check, and you’ll be able to start sending the emails. You’ll also receive an email informing you that your domain is ready for sending emails.

Some domains may be selected for additional checks. If so, we’ll ask you to fill out a simple Compliance Form and answer a few questions about your business, sending goals, etc. You’ll see a notification under Compliance Check and a link to the form.

<figure><img src="../.gitbook/assets/sending-domains-compliance-pending.png" alt="Compliance check pending status with Fill In Compliance Form button"><figcaption><p>Compliance check pending status</p></figcaption></figure>

We’ll email you if we need additional information from you. If all the checks are successful at this stage, your domain will be verified.

In some cases, your domain may be selected for manual verification. This is the final check before your domain is verified. The length of the manual verification depends on how fast you reply to our emails. If successful, you'll see Verified status. If not, you'll see a Rejected badge next to your domain and a message under Compliance Check. In case of any questions about the reasons for rejection, please contact our support team at [support@mailtrap.io](mailto:support@mailtrap.io).

<div data-with-frame="true"><figure><img src="../.gitbook/assets/image (2).png" alt="" width="563"><figcaption></figcaption></figure></div>
{% endstep %}
{% endstepper %}

### (Optional) Tracking Settings <a href="#optional-tracking-settings-ffi49" id="optional-tracking-settings-ffi49"></a>

An optional step is to change the tracking settings. By default, Mailtrap tracks email opens for each email sent. You can also enable click tracking.

{% hint style="info" %}
Click tracking and custom domain for clicks tracking are available only for paid accounts.
{% endhint %}

<div data-with-frame="true"><img src="../.gitbook/assets/sending-domains-godaddy-dns-settings.png" alt="Tracking Settings overview showing Track Opened Emails and Track Clicks toggles"></div>

With tracking enabled, you will find the open and click rates in the Analytics reports. [Read this article](../statistics/) for a detailed breakdown of Statistics.

1. Navigate to the Tracking Settings tab.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/sending-domains-godaddy-record-type-dropdown.png" alt="Tracking Settings tab with Track Opened Emails toggle" width="563"></div>

2. Toggle the switch next to Track Opened Emails to enable or disable tracking opens. Mailtrap tracks email opens via an invisible pixel. It’s added to each message sent from your account. When an email is opened, a pixel is loaded, and an ‘open’ event is recorded. Each of these events will be visible in [Email Logs](../statistics/email-logs.md).

{% hint style="info" %}
Some mailbox providers, browsers, and extensions block invisible pixels. Users can also choose not to display images, or a solution they use to retrieve emails may not support images by default. In each of these cases, an 'open' event won't be recorded even if an email is opened.
{% endhint %}

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/sending-domains-godaddy-add-txt-record.png" alt="Track Opened Emails toggle enabled in Tracking Settings" width="563"></div>

3. If you're a paid user, toggle the switch next to Track Clicks to enable or disable tracking clicks. If you enable click tracking, the toggle for Custom Domain for Clicks Tracking will be switched on automatically. That way, all links will be redirected through your domain (mt-link.yourdomain.com). And if you verified all the records correctly in Step 2, Domain Tracking will also be verified and ready to use.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/sending-domains-godaddy-add-cname-record.png" alt="Track Clicks and Custom Domain for Clicks Tracking toggles enabled" width="563"></div>

### Unsubscribe Settings <a href="#unsubscribe-settings-ekyqh" id="unsubscribe-settings-ekyqh"></a>

You can also configure unsubscribe settings.

Unsubscribe links are mandatory for bulk emails as per privacy laws. If your emails don't include an unsubscribe link, Mailtrap will add an Unsubscribe Footer automatically. This is what it will look like:

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/sending-domains-godaddy-all-records-added.png" alt="Example unsubscribe footer in email with unsubscribe link and company address" width="563"></div>

To add an unsubscribe link anywhere in your template, include this tag in your HTML template: `<a href="__unsubscribe_url__">unsubscribe</a>` . Mailtrap will render a clickable link in your email.

Unsubscribe Footer and Links are optional for transactional emails and are switched off by default.

However, if you want to, you can still add an Unsubscribe Footer to your transactional emails by toggling the switch On under Unsubscribe Footer for Transactional emails or adding an HTML tag mentioned above.

<div data-with-frame="true"><img src="../.gitbook/assets/sending-domains-verification-complete.png" alt="Unsubscribe Settings showing toggles for Bulk and Transactional emails"></div>

If you’d like, you can mix both approaches - automatically add a footer to emails sent from one domain and do it manually (when applicable) for emails sent from another domain.

If an end-user uses an unsubscribe link, Mailtrap will reject any future emails sent to this address from this particular domain. You can quickly find all such emails in the Email Logs by filtering by a “reject” event.

You will still be able to email them using other domains or subdomains added to your Mailtrap account.

For that reason, it’s worth having different domains or subdomains for different types of emails. This way, users can, for example, unsubscribe from your bulk or marketing messages while still receiving vital transactional messages.

### (Optional) Webhooks <a href="#optional-webhooks-4hmes" id="optional-webhooks-4hmes"></a>

Lastly, you can set up webhooks to receive event information almost real-time.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/sending-domains-compliance-in-progress.png" alt="Webhooks page with Add New Webhook button" width="563"></div>

Click the Add New Webhook button, choose the Sending Stream, paste the webhook URL (your endpoint) into the designated field, select the events you want to listen to, and then test the setup.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/sending-domains-webhook-setup.png" alt="Add new webhook form showing webhook URL, sending stream selection, and events to listen for" width="563"></div>

Mailtrap also allows you to batch up to 500 events within a webhook; that is - group all events under one object, and thus save on computing power.

### Useful tips <a href="#sending-domains-j_1ht" id="sending-domains-j_1ht"></a>

After completing the setup process, you can always return to the Sending Domains tab to add any additional domains or subdomains. If you, for example, misspelled a domain, you’ll need to delete it and re-add it with the correct spelling.

{% hint style="info" %}
You can't create any additional demo domains, but you can delete the existing one if needed.
{% endhint %}

<figure><img src="../.gitbook/assets/sending-domains-verified-list.png" alt="Sending Domains list showing verified domains with status and emails sent"><figcaption><p>Sending Domains list with verified domains</p></figcaption></figure>

Remember that the domain with the Demo badge can be used to send emails only to the email address you registered with.

<figure><img src="../.gitbook/assets/sending-domains-demo-restrictions.png" alt="Demo domain showing restriction message that it can only send to yourself"><figcaption><p>Demo domain restrictions</p></figcaption></figure>

You can send emails to your recipients only from domains that have Verified status. If the status is Pending or Rejected, you won't be able to send emails.

<figure><img src="../.gitbook/assets/sending-domains-pending-verified-statuses.png" alt="Sending Domains showing pending and verified status badges"><figcaption><p>Domain status badges - Pending and Verified</p></figcaption></figure>

From the Sending Domains menu, you can also delete the domains, subdomains, or the demo domain you no longer use. Just press the bin icon next to the domain. This will remove the domain from the list, and you won't be able to send any further emails until you add and verify it again.

<figure><img src="../.gitbook/assets/sending-domains-delete-button.png" alt="Sending Domains with delete button highlighted"><figcaption><p>Delete domain button</p></figcaption></figure>

Note that removing a domain won't remove it from your Mailtrap account completely. It will still appear, for example, in analytics, and will be displayed with the (deleted) suffix, just like in the example below:

<figure><img src="../.gitbook/assets/sending-domains-deleted-in-stats.png" alt="Stats overview showing deleted domains with (deleted) suffix"><figcaption><p>Deleted domains shown in stats</p></figcaption></figure>

We do this to preserve your historical stats that would otherwise be lost.
