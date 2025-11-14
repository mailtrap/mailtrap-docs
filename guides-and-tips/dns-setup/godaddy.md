---
description: >-
  Verify your Mailtrap sending domain in GoDaddy. Add DNS records for
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

# GoDaddy

To add and verify a sending domain in Mailtrap, you need access to your domain’s DNS records and your domain provider account.&#x20;

<a href="./" class="button secondary">Sending Domain Setup</a> check it for more details on setting up your sending domain. Continue reading to learn how to add Mailtrap DNS records to _GoDaddy_.

{% hint style="info" %}
_This guide assumes that your domain is either registered with GoDaddy and uses its nameservers or isn’t registered with GoDaddy but uses its nameservers._&#x20;
{% endhint %}

1. Go to GoDaddy and locate the domain you’ve added to Mailtrap.&#x20;

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/wyrJEQ5AJnbJLPfGOg6tOdlXiIaofFbqsmDK-NCYX3mMhqWxRGDcFCmCU45YYJXjap3vu6Hva5YWluDhmpg28tOgpQMoGbKEGhKiSgFYqzpIPNWwukxBLRgypFj21t6FS0C5qDrXsHduJzSg5IB_DWE" alt="" width="375"></div>

2. Open the DNS settings and click Add New Record.&#x20;

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/MI4cp8Dkov5UQWToE8vnofRMC6EKYITfDI8z6wiiK4pOmjv6DReaO0Ti5ZAOAWpdgWhWuWkldUsIA6aXvj-HK-pHUnxTYp8xIf0LrByTivsbTqv1RtG6YD0SNr3mpmWpj4flAKB8EOFcnwW_jnJAm-Y" alt="" width="563"></div>

3. Return to Mailtrap. On the Domain Verification page, you’ll see the DNS records you need to add to GoDaddy. These are Domain Verification, DKIM, SPF, DMARC, and Domain Tracking. You’ll need the values under Type, Name, and Value. The namings of these records in Mailtrap are the same as in GoDaddy.&#x20;

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/PLIjIZXbA2ou6wa1WWnJi107NbBefJuqpYIWMsr4tclem-mDBxGxEUAo87qgM1FDp_mMctWrpNeQgdayOZ8COIWSjeOozeCzLyHXVmJAhXZburu9Jal9UjmAcn11dTPwIKCaphnSEB3FfdkWzInRx0M" alt="" width="563"></div>

Make sure you check the type next to each record in Mailtrap and choose a relevant one in GoDaddy. There are four CNAME type records (Domain Verification, DKIM (2), and Custom Tracking Domain) and two TXT type records (SPF and DMARC).

<div align="left" data-with-frame="true"><figure><img src="https://lh7-us.googleusercontent.com/PfcOKF0sC6cYYdthewhRcrUkQOM-H3MhAhuEdJZKF-Ns48erWX6A_AF0Ve_IgK1gYt-tQbCvpr-Gu01PzbvZMLISAODZteX_eddKg2aZ8Qbg9fcGB7YoYB1b5OSgqHUFGj7zn9slZHBNzozrwQuL7BQ" alt="" width="563"><figcaption><p>DNS Types and Categories in Mailtrap </p></figcaption></figure></div>

<div align="left" data-with-frame="true"><figure><img src="https://lh7-us.googleusercontent.com/h9MTkynkLNhbkQsob45GXe25dbENjYh0EdS6I32TCBxNUsVJ-w44GLm564-bQbCiu4mTbgeuqexX5oHhf3Hu2w7uRMrKJOdaOS2r3vpHnjTEA9INak5VJyz27_tvJBjs9ixtR_3ghMGgACfBAWba5aA" alt="" width="375"><figcaption><p>DNS record types in GoDaddy </p></figcaption></figure></div>

{% hint style="warning" %}
_You should have only one SPF record. So, if you already have one for your domain, update its value to include Mailtrap. It’s okay to have multiple DMARC records._
{% endhint %}

4. Copy the Name and Value for each record one by one. You can do this by hovering and clicking each record.&#x20;

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/ggZNvUVHN5-ke_HtETlZmUIVxX_PO3KE2gTYUqsbVals4_gYRdl3U0IzTCkscrJ7xB5KV7964k9XeNJLG3ZpOi0rCu7o4ciXnPlWt4cumvPaaq4ngOrXgbonLp3tsDrS49UZrn9yJTgtEXhd75KWymo" alt="" width="563"></div>

5. And paste them into GoDaddy.&#x20;

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/1FitTMartZrU0PhXUN77NVABcdIJZq-zA247Gp3Y334umY_iE-xScvw12U9iqk9_HvjAaiSMP0Zl1HSUsQnAP5dBJ8ABzWEckwzdVQ0JIJEDXcf3zpcXD8nc0BGWSNmgxXv8XL7u0HfFGkcVyFTP-rE" alt="" width="563"></div>

6. Use the default value for TTL.&#x20;
7. Click Save after adding each record in GoDaddy.&#x20;
8. Repeat the process of copying and pasting for each record until you’ve added all the Mailtrap DNS records to GoDaddy.&#x20;

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/pK55Yr5ZJ5Md5yWlCrWLB-WJgmzRlZaAVmCh0Ed9Xk3MHdnQcDNdiFiNJPlHI-zd0PUGLS7QqcQHiqFFNw4mrI_i1vMt3YEI9KLC3259ZrTlS-7ZRNIA4q5yl5YtU71GLnAEE408Qp8kvixjNj-ryFo" alt="" width="563"></div>

9. Then, return to Mailtrap. Some records may be verified immediately, while some may take more time. Mailtrap will check the DNS records automatically every hour, but you can force a check by clicking the Re-check DNS Records button.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/kzuxWGuyGZp-inyFiLWDt5HLkGyHEwqeKJjXRe4DMHIDyacO_JJR2qH0zpq--vBGJVImCGdkXnVXZwCRRExoko6ic24ONonkqewgXCFgoBHHiZyvDpVLseDrB67-c9lidf5oLqs1yTrSGh6I3EEpDU4" alt="" width="563"></div>

10. If you add all the required DNS records correctly, the Status of DNS records will change from Missing to Verified, and the red dots will turn green.&#x20;

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/rYCy8uA9XnRl_WMzj00e7HyovOvuVjZdMGgDxtWbl2sKKcpmxA2POFxbK1FxaozmRc3DMkQILbPzHSlh0rAoVJ-hq7QJLQqolbWS2tnoF9GQXTfpSRHkNmCZ5QNvIGe0q8DbDaI5I8fhk0v5gQlt_FY" alt="" width="563"></div>

{% hint style="info" %}
_If you have additional questions,_ [_consult GoDaddy documentation_](https://uk.godaddy.com/help/manage-dns-records-680) _or contact us at_ [_support@mailtrap.io_](mailto:support@mailtrap.io)_._&#x20;
{% endhint %}
