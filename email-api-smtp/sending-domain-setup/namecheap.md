---
description: >-
  Verify your Mailtrap sending domain in Namecheap. Add DNS records for
  SPF/DKIM/DMARC verification, pass compliance, and start sending emails.
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

# Namecheap

To add and verify a sending domain in Mailtrap, you need access to your domain’s DNS records and your domain provider account.&#x20;

<a href="./" class="button secondary">Sending Domain Setup</a> check it for more details on setting up your sending domain. Continue reading to learn how to add Mailtrap DNS records to Namecheap.

{% hint style="info" %}
_This guide assumes that your domain is either registered with Namecheap and uses its nameservers or isn’t registered with Namecheap but uses its nameservers._&#x20;
{% endhint %}

1. Go to Namecheap, locate the domain you’ve added to Mailtrap on the dashboard, and click Manage.&#x20;

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/_uLejw9C0l4EHypEa4SqI3YWCPrad7eltVGT5h-W51eCmSWkK8hyBYLd_cMk55_GAuKZ50tjYKbECJvRDFwSAzOcHbwz2XGnQI9EuQH0Cij65l2pxXo9YyYbNeB45nn47L5c5Yuf2XKPf15_6KkVaPI" alt="" width="563"></div>

2. Navigate to the Advanced DNS tab.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/IDwoqu5SLATURE6isJeoRaAANLCPavwJjm7ubWuqAZ7nBJoG65llp68C62Aqu_Q1IQUVO_JbV32HGPY7fR1gg2vnDLcx-PEwpm1ifQcvGiHX0WPWU7S8ZF9dxdBGfi0B0W7PBiICX9_JUELrW7ZTvL0" alt="" width="563"></div>

3. Click Add New Record.&#x20;

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/484ZQl1q0_he2ZCaKmkeZTxx1vDejfRibQ-rnJly4PsbLUSMxVGJCq9a5YuNhh1IHgWjfSoBJitxH60xJ8tXby3PVd8BJB5TKbm8W3aeB1OsVwcmSufTWJ1ltFjShxTpn5J4qLWUft19hB66ufySML8" alt="" width="563"></div>

4. Return to Mailtrap. On the Domain Verification page, you’ll see the DNS records you need to add to Namecheap. These are Domain Verification, DKIM, SPF, DMARC, and Domain Tracking. You’ll need the values under Type, Name, and Value. &#x20;

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/z_uaHPU_x1UURMe3WLc7dxRKby36Ynt0E57Jbdpqzn-nbfHDrjk-36HD-VEC6KPPmDHM8WgpzjIev0QGAsm9hVzH_EOjH550Ol_W_oz5qXUaxns0iHakYFeJvER0ShGE_Bo8Y-L-lKvxmO5bSNW12JI" alt="" width="563"></div>

Make sure you check the type next to each record in Mailtrap and choose a relevant one in Namecheap. There are four CNAME type records (Domain Verification, DKIM (2), and Custom Tracking Domain) and two TXT type records (SPF and DMARC).

<div align="left" data-with-frame="true"><figure><img src="https://lh7-us.googleusercontent.com/GQZhpvtGZjOqcsxL6evGQWXCyL3QMjpAp-EfzlaYTFglQX5mx6kiqdN8Sudd2DYF_l92bH6jTeMBtJJ1WvvYpkUh7cJeDmwmFDPZqZqcqawm6MCFAQYf4Iv6KhFE8Nn_96zznEv0qaBv5Wi36booMQM" alt="" width="563"><figcaption><p>DNS Types and Categories in Mailtrap </p></figcaption></figure></div>

{% hint style="info" %}
You should have only one SPF record. So, if you already have one for your domain, update its value to include Mailtrap. It’s okay to have multiple DMARC records.
{% endhint %}

5. Copy the Name and Value for each record one by one. You can do this by hovering and clicking each record.&#x20;

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/1aQmHzCwiK0MZcbfwFwLDXQv17iSfUeBxweVcRNakuG-Yit1WMIIvqwwt50zXfAKVQpzNKpfQAi2dBUjTEFNJ2QwBAwokgfq-Kbhz0sCBZ7BZ75jkDojvIiRThYOJ5cUusSlfYdrQ-_TN1_0E1tnDy4" alt="" width="563"></div>

6. And paste them into Namecheap. Remember that Namecheap refers to the Name field as Host.&#x20;

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/8r6N-SgDxHUE3WcqWdanp616YyDkosKUzZiraw8ZwKfEImbjx-V66fXMhNA1NHMpHcpTX0CJclINK9Dqud2T6WmW0VjC2XaUmdqXj84u4JYgjVaD5ijDVN30DF8a83C0snXoTQY8Rqcj671LDVF-iEk" alt="" width="563"></div>

7. Use the default value for TTL.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/1tFbbozHKpFk8HuHGAlNQXJkY_32JuuF3TckJ_2rK8A5bGvE6vHTel4OzZsI7HbQjwVfIGZVqkbJBcLn5oTIKV3kdSgOjyGjdJQpr2x50MDNeM_iReUeoslKckaSO2WsXS7nI0EYlkQmwI-qaW16TkI" alt="" width="375"></div>

8. Repeat the process of copying, pasting, and clicking Add New Record for each record until you’ve added all the Mailtrap DNS records to Namecheap. Click Save All Changes.&#x20;

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/oHDoi1ZPTpEuDsoMluJEIXXfvzzFlcoYKC1Kmz3QCYDJVxmZWh0gYE5wjLiYXkp6gNKA9WVWkRxTNcjlMYFiRHvgiwha_RZJ-uAlvWumy9kxRGTD6aEM4biYA5K8xXUrzTC9Nz2cx8VfadC6yNr3CpY" alt="" width="375"></div>

9. Then, return to Mailtrap. Some records may be verified immediately, while some may take more time. Mailtrap will check the DNS records automatically every hour, but you can force a check by clicking the Re-check DNS Records button.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/pPqovqrPA8oVLrLYCamuuOYIqJS9dcJAwhDdbvD0pfZrbNDlemkUUv7BsEwlmUC9QNDUaXcPNuuKXJpq9Vmazq1CZTzr6MBrX3lUY420lqnYSLscie7WIEEm_LwvOyS4KzCkgIrzTe1k2FByvSf-ytU" alt="" width="563"></div>

10. If you add all the required DNS records correctly, the Status of DNS records will change from Missing to Verified, and the red dots will turn green.&#x20;

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/adss8tUACGdVi9AUoWdyZqJLA6wLioy7FMU-RyGEVi0f7kdMvFdSpPOjZGlMqMnmHJdIaI8OzNuo7Yemf11JgRbW_G55o_HFRBlIunQEME8pm-3wKBA3ZAGyB2kf_ktlnjAUB1qHgorlAnnPQ9s1jAs" alt="" width="563"></div>

{% hint style="info" %}
_If you have additional questions,_ [_consult Namecheap documentation_](https://www.namecheap.com/support/knowledgebase/article.aspx/434/2237/how-do-i-set-up-host-records-for-a-domain/) _or contact us at_ [_support@mailtrap.io_](mailto:support@mailtrap.io)_._&#x20;
{% endhint %}
