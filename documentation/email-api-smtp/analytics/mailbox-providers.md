---
description: >-
  Analyze email performance by mailbox providers like Gmail, Outlook, and Yahoo.
  Filter by domain and category, track metrics, and identify deliverability
  issues.
icon: mailbox
---

# Mailbox Providers

<details>

<summary>Why is it important to monitor mailbox provider stats?</summary>

It’s important because the deliverability towards a specific provider can suddenly drop. This is a clear sign that a provider has started treating you negatively, so it’s critical to take action to improve the situation.

</details>

The following sections detail how to take advantage of **Mailbox Providers** feature within **Mailtrap API/SMTP**.

#### Mailbox Providers filters <a href="#mailbox" id="mailbox"></a>

Mailbox Providers Overview panel allows you to filter by **Domains**, **Mailbox Providers**, and **Categories**. Here’s how to use each filter.

**Domains**

1. Click on the arrows in the All Domains box.
2. Choose one or more domains you’d like to use.
3. When you select the domain, the Table automatically shows corresponding statistics.

<div align="left" data-with-frame="true"><figure><img src="../../.gitbook/assets/SCR-20260924-sqjk-2.png" alt="" width="563"><figcaption><p>Domains filter dropdown in Mailbox Providers panel</p></figcaption></figure></div>

**Mailbox providers filter**

1. Click the arrows in the Mailbox Provider box.
2. Choose the provider you’d like to use.
3. Check the corresponding stats in the table below.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/SCR-20260924-ssah.png" alt="Mailbox Provider filter dropdown showing available providers" width="563"></div>

You can select a few providers at the same time - just repeat the actions listed above.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/SCR-20260924-stec.png" alt="Multiple mailbox providers selected in filter dropdown" width="563"></div>

**Categories**

1. Click the arrows in the **Categories** box.
2. Choose a category or categories.
3. Preview the stats for that category in the table below.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/SCR-20260924-suim.png" alt="Categories filter dropdown in Mailbox Providers panel" width="563"></div>

#### Navigating mailbox providers <a href="#navigating" id="navigating"></a>

**Table**

The first column features **Mailbox Providers** of your recipients.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/SCR-20260924-svik.png" alt="Mailbox Providers statistics table showing provider names and metrics" width="563"></div>

The stats include the number of **Delivered** emails. You can also see **Unique Opens** and **Unique Open Rate**, as well as **Clicked** emails and **Click Rate**.

Also, the Tables tab shows **Bounce** emails and **Bounce Rate**, plus **Spam** and Spam **Complaints**. Finally, you can see the **Clicked to Open Rate**.

You can learn more about [Stats](./) here.

**Color coding**

To immediately understand email deliverability, the table features colors that signal if the value is good, bad, or just average.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/SCR-20260924-swsz.png" alt="Mailbox Providers table row with green status indicator showing good performance" width="563"></div>

* No color highlight - good results - exceed what we perceive as a satisfactory value for a particular data point.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/SCR-20260924-sxvt-3.png" alt="Mailbox Providers table row with yellow status indicator showing borderline performance" width="563"></div>

* <mark style="background-color:yellow;">Yellow</mark> - borderline results - neither good nor bad, and may require your attention or action.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/SCR-20260924-sxvt.png" alt="Mailbox Providers table row with red status indicator showing poor performance requiring attention" width="563"></div>

* <mark style="background-color:red;">Red</mark> - the result is under the threshold we consider satisfactory, and it requires your action to improve the performance of a specific mailbox provider.

<div align="left" data-with-frame="true"><img src="../../.gitbook/assets/SCR-20260924-sxvt-2.png" alt="Mailbox Providers table showing email statistics with color-coded performance indicators" width="563"></div>
