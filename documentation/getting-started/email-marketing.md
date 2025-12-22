---
title: Email Marketing
description: Learn how to set up and send email marketing campaigns with Mailtrap
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

# Email Marketing

Make sure you've added and [verified a domain](../email-api-smtp/setup/sending-domain.md), or you won't be able to send a campaign.

### How to set up and send a campaign

{% stepper %}
{% step %}
Go to **Email Marketing** and click **Create New Campaign**.

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/marketing-campaign-create-button.png" alt="Email Marketing page with Create New Campaign button" width="563"><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
Fill out the form with your company details, such as name, address, city, zip code, and country. Optionally, enter your company's phone number and link to the website. Click **Continue**.

{% hint style="info" %}
This information will be added to email footers to ensure compliance with existing regulations. You'll only have to complete this step once when creating your first campaign.
{% endhint %}

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/marketing-campaign-company-details.png" alt="Company details form for campaign compliance" width="563"><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
Choose a domain from the **Select domain** dropdown, then set the **Campaign name**, **Subject**, and **From** email address. Optionally, set the From name, Reply-To name, and Reply-To email. If you have only one domain, no need to choose anything, it's selected for you by default. Click **Continue**.

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/marketing-campaign-settings.png" alt="Campaign details form with domain, name, subject, and email settings" width="563"><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
You'll be taken to the Design step, where you can choose between Drag & Drop and HTML editors. If you have templates stored, you'll see them here. You can use them in your campaigns. Read more about creating templates [here](../email-api-smtp/email-templates.md).

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/template-design-selection.png" alt="Template selection page with Drag &#x26; Drop and HTML editors" width="563"><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
Create your campaign design, click **Save**, and then **Continue**.

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/marketing-campaign-design-editor.png" alt="Drag and drop email editor interface" width="563"><figcaption></figcaption></figure></div>

{% hint style="info" %}
Instead of continuing to the next step, you can click **Send Test** to send a test to one email address to check the design in your email client or click **Finish Later** to return to the campaign **Details**, where you can change any of the parameters you set in previous steps.
{% endhint %}
{% endstep %}

{% step %}
If you've already imported your contacts, select your audience by including or excluding specific lists. Then, click **Confirm Audience**.

{% hint style="success" %}
With **Including** and **Excluding** features, you can easily send campaigns to specific audience groups only.
{% endhint %}

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/getting-started-audience-selection.png" alt="Audience selection with including and excluding lists" width="563"><figcaption></figcaption></figure></div>

{% hint style="warning" %}
If you didn't upload your contacts before creating a campaign, you'll be prompted to import contacts at this stage. Simply click **Import Contacts** and follow the steps ([refer to this section](../email-marketing/contacts.md#how-to-upload-contacts-nag8y) in our Contacts guide for more details). **Important**: you should create Fields beforehand to be able to assign variables to the fields (map fields) when importing contacts.
{% endhint %}
{% endstep %}

{% step %}
At this point, you can click **Send Test** to send a test email to one email address, choose **Send now** to send the campaign immediately, or select **Schedule campaign** to send it at a specific date and time.

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/marketing-campaign-send-options.png" alt="Send and schedule campaign options" width="563"><figcaption></figcaption></figure></div>

{% hint style="info" %}
To schedule the campaign, click **Schedule Campaign**, select the date, and choose the time. Then, confirm the action by clicking **Schedule Sending**.
{% endhint %}

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/marketing-campaign-schedule-form.png" alt="Schedule campaign form with date and time picker" width="375"><figcaption></figcaption></figure></div>
{% endstep %}
{% endstepper %}

### What's next?

Once your campaign has been sent, you can check the campaign deliverability data and stats. Here's how to do it:

{% stepper %}
{% step %}
Click **Email Marketing** in the left navigation panel and you'll have a quick preview of all the campaign data. If we're still collecting the data, you'll be notified accordingly.

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/marketing-campaign-list-view.png" alt="Campaign sent confirmation messages" width="563"><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
If you want more details for a particular campaign, click the campaign name, then select the **Reports** tab where you'll see the full [Statistics report](../email-marketing/statistics.md).

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/marketing-campaign-statistics.png" alt="Campaign statistics report showing delivery rates, opens, clicks, and mailbox provider breakdown" width="563"><figcaption></figcaption></figure></div>
{% endstep %}
{% endstepper %}
