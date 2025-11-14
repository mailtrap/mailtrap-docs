---
description: >-
  Verify your Mailtrap sending domain in Cloudflare. Add DNS records for
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

# Cloudflare

To add and verify a sending domain in Mailtrap, you need access to your domain’s DNS records and your domain provider account.&#x20;

<a href="./" class="button secondary">Sending Domain Setup</a> check it for more details on setting up your sending domain. Continue reading to learn how to add Mailtrap DNS records to Cloudflare.

{% hint style="info" %}
_This guide assumes that your domain is either registered with Cloudflare and uses its nameservers or isn’t registered with Cloudflare but uses its nameservers._
{% endhint %}

1. Open the Cloudflare dashboard and click the domain you’ve added to Mailtrap.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/QmB2QDMu0w8zNaXcSsXwa6IEPjADvJIv_BNH8NAhtiYg88hjX8jdxKZ95Fat0tmhC5cUGUstrHbJoMCDQdTT9FQZuAxDZGjoyurLVckbf-7vx_cAzvNG-teciT6L0EhKJJ4RUVyeVTbwfXV6vCXp2Gk" alt="" width="563"></div>

2. Click DNS in the left navigation panel. This will open DNS records.&#x20;

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/eGsHRQaz9dy8B7dChorApEb_DDbkU5npd5ZNvEE3EIBtkuTM_WHQQFpqcvri2WVXhL__IlBK7NW2VcNHh-Wj38FNy3pLFC16hHkb5aL49WibKhmPsuXrDVPM49tfdOR6IV66snaUrRIkFJP0XJ_UZuw" alt="" width="188"></div>

3. Click the Add Record button.&#x20;

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/TKQsrU_-_YbPslByDxv2oOqVs3CJR5PLSj9X1yZKaU1dc3XiP6QJcOcpCGm_UDnoxwCZKtE2hgvgcatq506aYqq6Vq6weQY4pTy8Y9vJYypR_dyYFrSR4E-88Z5N8uZpg4HD_q1_g6uHiCya_NVdubY" alt="" width="563"></div>

4. Return to Mailtrap. On the Verification page, you’ll see the DNS records you need to add to Cloudflare. These are Domain Verification, DKIM, SPF, DMARC, and Domain Tracking. You’ll need the values under Type, Name, and Value.&#x20;

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/9o4WFJFxpHS61BaVEPjDIuqdGgs8NmGZ2OEHZCxdz6IveDi5g8yXP-BxScmt6ag-Gg9Mz--_G8Poi0l_7BWqb0xTzjAzf7ozsi0ox2ArEJAnqAuUSA_DwgvMVBddqx4Y6UYJbzK55vXgqiKK0qItGTw" alt="" width="563"></div>

Pay attention to the Type next to each record in Mailtrap and choose a relevant one in Cloudflare. There are four CNAME type records (Domain Verification, DKIM (2), and Custom Tracking Domain) and two TXT type records (SPF and DMARC).&#x20;

<div align="left" data-with-frame="true"><figure><img src="https://lh7-us.googleusercontent.com/iUaqSwsg-2zyTrTaxQrcURNAlq2lz0wKze36U7tkhc1x-RrI3t6lBwiNMOnu_R2PDHbgL0hZFeR3NPndUl0G6LlyGZD0iDxC7offWZuHf7UI1Z0yX603hz2rsvS0I6nvpmAh7NOg3LV_JU_VI9T2xdQ" alt="" width="563"><figcaption><p>DNS Types and Categories in Mailtrap </p></figcaption></figure></div>

<div align="left" data-with-frame="true"><figure><img src="https://lh7-us.googleusercontent.com/atCnv_kJ9yeF4Kwkm7dHFslUv4_I4ayjeo0BwnwedGj_A4iYgiHOSqK4I5Rk1s7pLjAW3xUk31kU2Tpmjt0GjjW4TaULx1DA8L3AbWZGHnT0KXrevCfKnQ7ITz4-vdH70EyrgTJ0ucdRcUbR9_jhhtE" alt="" width="375"><figcaption><p>DNS record types in Cloudflare </p></figcaption></figure></div>

{% hint style="warning" %}
You should have only one SPF record. So, if you already have one for your domain, update its value to include Mailtrap. It’s okay to have multiple DMARC records.
{% endhint %}

5. Copy the Name and Value for each record one by one. You can do this by hovering and clicking each record.&#x20;

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/CjJeWwRcaf5kNPA53rcvVnDuo1ePD6stFinGJaMtHcNEGDp6gOqPKJfr0rdmwm4oY0hvpRvUBAF1vVIIIXeq2k8LJlvOY0fq_GxSMqzQZZ_oOyDLrg2diNs03aIqZkJCDgHvUsdWc_b-JArrUq9MJG8" alt="" width="563"></div>

6. And paste them into Cloudflare. Remember that Cloudflare refers to the Value field as Target for CNAME records and Content for TXT records.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/QSdLgWq8MQwQBSji3ijuevh7DMPwIsk60j9rssaa9PvjSs85KwYJriCuLQgDBBOybPtOLSXdOSe7wybvB8SG934_xrRPHfQp1ozkLPNP5krm_utcXshT-B3JHjF9ay_hdwvo_OluM-63dcMg_TKw_qU" alt="" width="563"></div>

7. If you’re not using proxy, make sure you disable it. By default, it will be enabled.&#x20;

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/Nt39GclUopeZS4bK6EN35GZts9RyxC7MTzEshUXs6oFHecwI_hpVUNzQNW55GGjThNU0GKRpRXIojBuz-vb9GQOOlD3E7n65emly2leSE8AeTHJ7bJbM8hKDtMSNnehun9h1LyZrSbst8Mfrer58xfg" alt=""></div>

8. Use the default value for TTL.&#x20;
9. Click Save and repeat the process for all the remaining DNS records.&#x20;
10. Then, return to Mailtrap. Some records may be verified immediately, while some may take more time. Mailtrap will check the DNS records automatically every hour, but you can force a check by clicking the Re-check DNS Records button.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/SpFbbOffRLO_l5BZtsrGEupHnZ0xhD8_flZQnC8WljPwtKqFXNS66Codp8StmZ3ZuhqrkeKopLroxiJEHewyOKwW9U8Oj0dwvhS9FOLK-6LbfhMQf74OoE2Z1oNKSAJmRHFKxmUCSitRwU8f9PmROQ4" alt="" width="563"></div>

11. If you add all the required DNS records correctly, the Status of DNS records will change from Missing to Verified, and the red dots will turn green.&#x20;

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/YySDXIfun5cMQMKAeZnp2MdqIjBZghp3Szt5T6uZ43Jz1WyJhYbLmpZ24wDuMDWCFWz_bmyEJDGEyv4PGc0FFDds3hbKAzJ8Dc_2SiUXsj06Hg3NeXuoYYf6uxG-Z1c2uKhFJ0_HyH7Gu6XCHbdQSBU" alt="" width="563"></div>

{% hint style="info" %}
&#x20;_If you have additional questions,_ [_consult Cloudflare documentation_](https://developers.cloudflare.com/dns/manage-dns-records/how-to/create-dns-records/) _or contact us at_ [_support@mailtrap.io_](mailto:support@mailtrap.io)
{% endhint %}
