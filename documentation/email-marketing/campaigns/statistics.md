---
title: Statistics
description: View and analyze email campaign performance metrics and analytics
icon: chart-simple
---

# Stats

Mailtrap provides statistics for you to track the most important email marketing metrics.

In your campaign dashboard, you can find:

* [Campaign stats](statistics.md#campaign-stats)&#x20;
* [Recipients stats](statistics.md#recipients-stats)&#x20;
* [Clicks stats](statistics.md#clicks-stats)&#x20;
* [Mailbox provider stats](statistics.md#mailbox-providers-stats)&#x20;

{% hint style="info" %}
Feature applies to UI-launched campaigns only, not emails sent using the transactional or [bulk stream](https://docs.mailtrap.io/email-api-smtp/setup/bulk-stream)
{% endhint %}

### Campaign Stats

<div align="left" data-with-frame="true"><figure><img src="../../.gitbook/assets/campaign stats.png" alt=""><figcaption></figcaption></figure></div>

In the **Reports** tab, you can see the following campaign statistics:

* **Sent** – Emails attempted to be sent to recipients, including those that may have bounced or not yet been delivered.
* **Delivered** – Emails delivered to the recipient’s mailbox provider.
* **Opened** – Percentage of emails opened at least once.&#x20;
* **Clicked** – Percentage of emails where a recipient clicked any link.
* **Bounced** – Percentage of emails rejected by mailbox providers.
* **Spam complaints** – Percentage of emails recipients reported as spam.
* **Unsubscribed** – Percentage of recipients that unsubscribed from your campaign.

{% hint style="info" %}
By default, the Charts Overview shows data based on hourly sends, but you can also view it by daily totals.
{% endhint %}

### Recipients stats

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/recipient stats (2).png" alt=""><figcaption></figcaption></figure></div>

In the **Recipients** tab, you can see how your campaign is performing for each recipient.

The individual stats are shown in a list, as opposed to a chart, and you can filter the recipients by email, number of clicks or opens, and events (i.e., delivered, unsubscribed, etc.)

{% hint style="info" %}
You can also export the stats in a .csv file by clicking on the Download Recipients Report button.
{% endhint %}

### Clicks stats

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/click stats.png" alt=""><figcaption></figcaption></figure></div>

In the **Clicks** tab, you can keep track of the performance of your links, more specifically:

* **Clicks** – Number of emails where a recipient clicked any link.
* **% of total clicks** – The percentage of all campaign clicks that this link received.
* **Unique clicks** – Number of unique recipients who clicked this link at least once. Each recipient is counted only once.
* **% of unique clicks** – The percentage of all campaign clicks that came from unique users for this link.

### Mailbox providers stats

<div data-with-frame="true"><figure><img src="../../.gitbook/assets/mailbox providers.png" alt=""><figcaption></figcaption></figure></div>

Finally, you can go to the **Mailbox Providers Stats** and see how your campaign is performing with different Mailbox Providers, such as Google, Yahoo, Outlook, Apple Mail, and others.
