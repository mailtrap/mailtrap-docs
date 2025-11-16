---
description: >-
  Analyze email performance by mailbox providers like Gmail, Outlook, and Yahoo.
  Filter by domain and category, track metrics, and identify deliverability
  issues.
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

<details>

<summary>Why is it important to monitor mailbox provider stats?</summary>

It’s important because the deliverability towards a specific provider can suddenly drop. This is a clear sign that a provider has started treating you negatively, so it’s critical to take action to improve the situation.

</details>

The following sections detail how to take advantage of **Mailbox Providers** feature within **Mailtrap API/SMTP**.

### Mailbox Providers filters <a href="#mailbox" id="mailbox"></a>

Mailbox Providers Overview panel allows you to filter by **Domains**, **Mailbox Providers**, and **Categories**. Here’s how to use each filter.

#### Domains <a href="#domains" id="domains"></a>

1. Click on arrows in the All Domains box.
2. Choose one or more domains you’d like to use.
3. When you select the domain, the Table automatically shows corresponding statistics.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/mailbox-providers-domains-filter.png" alt="Domains filter dropdown in Mailbox Providers panel" height="104" width="624"></div>

#### Mailbox providers filter <a href="#mailbox-providers" id="mailbox-providers"></a>

1. Click the arrows in the Mailbox Provider box.
2. Choose the provider you’d like to use.
3. Check the corresponding stats in the table below.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/mailbox-providers-provider-filter.png" alt="Mailbox Provider filter dropdown showing available providers" height="199" width="624"></div>

You can select a few providers at the same time - just repeat the actions listed above.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/mailbox-providers-multiple-selection.png" alt="Multiple mailbox providers selected in filter dropdown" height="152" width="624"></div>

#### Categories <a href="#categories" id="categories"></a>

1. Click the arrows in the **Categories** box.
2. Choose a category or categories.
3. Preview the stats for that category in the table below.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/mailbox-providers-categories-filter.png" alt="Categories filter dropdown in Mailbox Providers panel" height="139" width="624"></div>

### Navigating mailbox providers <a href="#navigating" id="navigating"></a>

#### Table <a href="#table" id="table"></a>

The first column features **Mailbox Providers** of your recipients.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/mailbox-providers-table-column.png" alt="Mailbox Providers statistics table showing provider names and metrics" height="168" width="624"></div>

The stats include the number of **Delivered** emails. You can also see **Unique Opens** and **Unique Open Rate**, as well as **Clicked** emails and **Click Rate**.

Also, the Tables tab shows **Bounce** emails and **Bounce Rate**, plus **Spam** and Spam **Complaints**. Finally, you can see the **Clicked to Open Rate**.

You can learn more about [Stats](./) here.

**Color coding**

To immediately understand email deliverability, the table features colors that signal if the value is good, bad, or just average.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/mailbox-providers-green-status.png" alt="Mailbox Providers table row with green status indicator showing good performance" width="563"></div>

* Green - good results - exceed what we perceive as a satisfactory value for a particular data point.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/mailbox-providers-yellow-status.png" alt="Mailbox Providers table row with yellow status indicator showing borderline performance" width="563"></div>

* <mark style="background-color:yellow;">Yellow</mark> - borderline results - neither good nor bad, and may require your attention or action.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/mailbox-providers-red-status.png" alt="Mailbox Providers table row with red status indicator showing poor performance requiring attention" width="563"></div>

* <mark style="background-color:red;">Red</mark> - the result is under the threshold we consider satisfactory and it requires your action to improve the performance of a specific mailbox provider.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/mailbox-providers-table-example.png" alt="Mailbox Providers table showing email statistics with color-coded performance indicators" width="563"></div>
