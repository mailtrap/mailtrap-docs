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

<div align="left" data-with-frame="true"><img src="https://lh6.googleusercontent.com/vpfkDzsnhMaH31WfguPmHIYvno-O9ClndrRfOOUtaVF9nvFIR1H4MuIP0ONvNG3nR0Vv6lKp6EYO1htbXoJRtvdq0sAgFjNsWmLrTvFg_8DptmuTrBav6vUGOfTf-ocF1n2Rli0c" alt="" height="104" width="624"></div>

#### Mailbox providers filter <a href="#mailbox-providers" id="mailbox-providers"></a>

1. Click the arrows in the Mailbox Provider box.
2. Choose the provider you’d like to use.
3. Check the corresponding stats in the table below.

<div align="left" data-with-frame="true"><img src="https://lh5.googleusercontent.com/S-UD50rd3idZc1ShZjGNvOiIcPECAVw96rTsGqHB6T6Orm01BVBp_ep-7nEVn6zmXVFEdXDSZbDvoxxb-ka5oMqy8TpKbmIJMKhccxj-1hNPrPVP4UTH7FNFAJGXWKNAodIvPRPf" alt="" height="199" width="624"></div>

You can select a few providers at the same time - just repeat the actions listed above.

<div align="left" data-with-frame="true"><img src="https://lh6.googleusercontent.com/PzJfZa8sLQBIvDRDyYbL85AbD_lcLBu5eJjsf6733OtBuh5Rh_2ZdCCpyp3x89VT53lvBmE-q8mNplY0krew-ugwyv2lZRhEBn2itzkGuGQGuxz5G21tkv_SIlLtAQS8VGw-S5zQ" alt="" height="152" width="624"></div>

#### Categories <a href="#categories" id="categories"></a>

1. Click the arrows in the **Categories** box.
2. Choose a category or categories.
3. Preview the stats for that category in the table below.

<div align="left" data-with-frame="true"><img src="https://lh3.googleusercontent.com/j5OBpa_TB2oa0_DOZ1wlZQUmJMId8RLuf0VnwCwBFc9zPK4a-Pb2OOP86Jf8q2ajtManNEgiiVkeknKtljlRDumZ8RDLTw8jN5uS33JGlqn_D337kbwZ0-gt4GGBsM9PR_Cn6w5h" alt="" height="139" width="624"></div>

### Navigating mailbox providers <a href="#navigating" id="navigating"></a>

#### Table <a href="#table" id="table"></a>

The first column features **Mailbox Providers** of your recipients.

<div align="left" data-with-frame="true"><img src="https://lh6.googleusercontent.com/m13rOM0FHV5kON2zz-H5DdSft8KsNj3rockaWrPmwHoQj58Spi0tX-W2Ofuk7-MXA245GFVgAgauwhOaxe7NqpucR6I5kVW2YyF6JBy1Yv0NA5Y-ig5pOxo2B3RFYbXHsDnmloFK" alt="" height="168" width="624"></div>

The stats include the number of **Delivered** emails. You can also see **Unique Opens** and **Unique Open Rate**, as well as **Clicked** emails and **Click Rate**.

Also, the Tables tab shows **Bounce** emails and **Bounce Rate**, plus **Spam** and Spam **Complaints**. Finally, you can see the **Clicked to Open Rate**.

You can learn more about [Stats](./) here.

**Color coding**

To immediately understand email deliverability, the table features colors that signal if the value is good, bad, or just average.

<div align="left" data-with-frame="true"><img src="https://lh5.googleusercontent.com/zeo6_1SMSoBHvqKawNLMzvxaTL-exoks0HorHFKcDF_pDJFA8a20UkveFzzRG51NbFMyqpYqBXaKv5-M2tFwoNX6bQi2JUnleAfTrWcnJuZpl7XvxlK3iOcCFHZhMhz9DxeWHKQh" alt="" width="563"></div>

* Green - good results - exceed what we perceive as a satisfactory value for a particular data point.

<div align="left" data-with-frame="true"><img src="https://lh3.googleusercontent.com/nWW9UXum4BwAu_4GENneVSfhe33PosbBL_598oB9TWvDt8d4P0czsl1c395whI96_yRPy0-mqGXUq04qwhATmgGg5MWMm5WgZL-ugalaekq4Rk4paVycb6C1CxpQAhxbVCfs-qkF" alt="" width="563"></div>

* <mark style="background-color:yellow;">Yellow</mark> - borderline results - neither good nor bad, and may require your attention or action.

<div align="left" data-with-frame="true"><img src="https://lh4.googleusercontent.com/TpXJsG_K_Y2TwAmKbVeHYM-0UiKe9SIWRJC0usWWw2U65Ss6WytwFOq0a60cR2No8MwlRpdAFD_ADwJ0yRXO8SRh29u-ApH5vC67M_TuNPdfGSjMTCZ1OfGI-5zaoWyCXgK3kKtZ" alt="" width="563"></div>

* <mark style="background-color:red;">Red</mark> - the result is under the threshold we consider satisfactory and it requires your action to improve the performance of a specific mailbox provider.

<div align="left" data-with-frame="true"><img src="https://lh3.googleusercontent.com/zkwGR4Fpxfsx9E97uJ6g7SyZnSc2DfUyuNZxzPFd-Bw3xlQNU7OlOPyAHwpmEURaNsV59avONK3bVcaQxyaFxyqIgXFm3gJc16oE0mkHnT6Ks0JIfhXnZVv0B9KQ7BteUm9HF03S" alt="" width="563"></div>
