---
title: Email Marketing
description: Learn how to set up and send email marketing campaigns with Mailtrap
---

# Email Marketing

Make sure you've added and [verified a domain](../email-api-smtp/setup/sending-domain.md), or you won't be able to send a campaign.

### How to set up and send a campaign

{% @arcade/embed flowId="K6tN0H7X2QFnrfLcQeTq" url="https://app.arcade.software/share/K6tN0H7X2QFnrfLcQeTq" %}

{% stepper %}
{% step %}
Go to **Email Marketing** and click **Create New Campaign**.
{% endstep %}

{% step %}
Choose a domain from the **Select domain** dropdown, then set the **Campaign name**, **Subject**, and **From** email address. Optionally, set the From name, Reply-To name, and Reply-To email. If you have only one domain, no need to choose anything, it's selected for you by default. Click **Continue**.
{% endstep %}

{% step %}
You'll be taken to the Design step, where you can choose between Drag & Drop and HTML editors. If you have templates stored, you'll see them here. You can use them in your campaigns. Read more about creating templates [here](../email-api-smtp/email-templates.md).
{% endstep %}

{% step %}
Create your campaign design, click **Save**, and then **Continue**.

{% hint style="info" %}
Instead of continuing to the next step, you can click **Send Test** to send a test to one email address to check the design in your email client or click **Finish Later** to return to the campaign **Details**, where you can change any of the parameters you set in previous steps.
{% endhint %}
{% endstep %}

{% step %}
If you've already imported your contacts, select your audience by including or excluding specific lists. Then, click **Confirm Audience**.

{% hint style="success" %}
With **Including** and **Excluding** features, you can easily send campaigns to specific audience groups only.
{% endhint %}

{% hint style="warning" %}
If you didn't upload your contacts before creating a campaign, you'll be prompted to import contacts at this stage. Simply click **Import Contacts** and follow the steps ([refer to this section](../email-marketing/contacts.md#how-to-upload-contacts-nag8y) in our Contacts guide for more details). **Important**: you should create Fields beforehand to be able to assign variables to the fields (map fields) when importing contacts.
{% endhint %}
{% endstep %}

{% step %}
Choose whether to send all emails **at once** or send them **gradually (throttling)** by setting how many emails are sent per hour. For more details, refer to the [email throttling guide.](https://docs.mailtrap.io/email-marketing/campaigns/email-throttling)
{% endstep %}

{% step %}
At this point, you can click **Send Test** to send a test email to one email address, choose **Send now** to send the campaign immediately, or select **Schedule campaign** to send it at a specific date and time.

{% hint style="info" %}
To schedule the campaign, click **Schedule Campaign**, select the date, and choose the time. Then, confirm the action by clicking **Schedule Sending**.
{% endhint %}
{% endstep %}
{% endstepper %}

### What's next?

Once your campaign has been sent, you can check the campaign deliverability data and stats. Here's how to do it:

{% stepper %}
{% step %}
Click **Email Marketing** in the left navigation panel, and you'll have a quick preview of all the campaign data. If we're still collecting the data, you'll be notified accordingly.

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/marketing-campaign-list-view.png" alt="Campaign sent confirmation messages" width="563"><figcaption></figcaption></figure></div>
{% endstep %}

{% step %}
If you want more details for a particular campaign, click the campaign name, then select the **Reports** tab, where you'll see the full [Statistics report](../email-marketing/campaigns/statistics.md).

<div align="left" data-with-frame="true"><figure><img src="../.gitbook/assets/marketing-campaign-statistics.png" alt="Campaign statistics report showing delivery rates, opens, clicks, and mailbox provider breakdown" width="563"><figcaption></figcaption></figure></div>
{% endstep %}
{% endstepper %}
