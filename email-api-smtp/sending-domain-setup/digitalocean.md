---
description: >-
  Verify your Mailtrap sending domain in Digital Ocean. Add DNS records for
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

# DigitalOcean

To add and verify a sending domain in Mailtrap, you need access to your domain’s DNS records and your domain provider account.&#x20;

<a href="./" class="button secondary">Sending Domain Setup</a> check it for more details on setting up your sending domain. Continue reading to learn how to add Mailtrap DNS records to DigitalOcean.

{% hint style="info" %}
_This guide assumes that your domain is either registered and managed with DigitalOcean or registered elsewhere but points to DigitalOcean._ &#x20;
{% endhint %}

1. Choose Networking in the main menu of the control panel and click the domain you’ve added to Mailtrap.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/Xj508B4CnVz7hy60Tz0pQ5NPS46Ms1gRrYUIeLhsLhr71OPW_owlSG7zSDyIpD7pAczaJ2XX7VJwRPiITXQ0j2ah7S0N-srMF-2SmXnh02K74_aEOKT_YP3tck4XLAU2h4F51E-z_BH-7hvCmqTUmCg" alt="" width="563"></div>

You’ll see the Create new record heading. &#x20;

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/ftwbthSGTlITB0bs_kBBFzVCDOlxIUBc0w6h7-52ehH3G5alGVzUxCg6zePgYRVQ9_3o2nA3iQu5KR9nlx4Y6cHuBRE_soJQxJkkz_UTK3R876fwrSpnRFQNXb24jdnVlURioAZTBb2Lf-UsEX0gERE" alt="" width="563"></div>

2. Return to Mailtrap. On the Domain Verification page, you’ll see the DNS records you need to add to DigitalOcean. These are Domain Verification, DKIM, SPF, DMARC, and Domain Tracking. You’ll need the values under Type, Name, and Value.&#x20;

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/MNtfy42VGLnF39Z_ryfC8SEFH1zflHdBiIlgrUOk9H3UPh1eNOjvLmvnDOagFh4x13h9VIH7pE6paQFVPSbv8C6NWvfom5NnKc6uBdNfGAPrXDECHezC7EHCAUvePGJZfAO6q75IihrlI5CShwNK-wg" alt="" width="563"></div>

3. Check the type next to each record in Mailtrap and choose a relevant one in DigitalOcean (CNAME or TXT). Mailtrap has four CNAME type records (Domain Verification, DKIM (2), and Custom Tracking Domain) and two TXT type records (SPF and DMARC).

<div align="left" data-with-frame="true"><figure><img src="https://lh7-us.googleusercontent.com/bM9FND7e6AGkHTmYNOWdqwhpxMXBDv3x2hFyASTUB7-9xQmcaxkH_u3f3_cly3q3x9xdukFOwhtjp7S5_5p4QeOjZPU09lil3fI7nuYvkC8vmyqdHCrhI5HtWDhDVKb3OxZtR8kmP8ZTbmAgZRwWfBE" alt="" width="563"><figcaption><p>DNS Types and Categories in Mailtrap </p></figcaption></figure></div>

<div align="left" data-with-frame="true"><figure><img src="https://lh7-us.googleusercontent.com/D7Woj03gFVDyjmseclLnPCbA31dpguLzXDQtrg7dQJI2oglX4oBJDYlrYnXxXaO_fRIHg8vMtPIbw8VE_efNt6O-aZqhBcjJ47ANCePWm-i30ZBt_zcaihvJm5pUruAg73U0MAppODq--wUqLzzIhU8" alt="" width="563"><figcaption><p>DNS record types in DigitalOcean </p></figcaption></figure></div>

{% hint style="warning" %}
_You should have only one SPF record. So, if you already have one for your domain, update its value to include Mailtrap. It’s okay to have multiple DMARC records._&#x20;
{% endhint %}

4. Copy the Name and Value for each record one by one. You can do this by hovering and clicking each record.&#x20;

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/AofIJNI87UQrbHTMRrUDiQksKQMLrdibzct-6NqaimJFjXMmDgIYB5bD90RpQDFn5ykG7wwaLPaCY9PFOcUKMnD4N1KrxW5NF8ei8MiF3124CbbFHVce203e7W1RMZtu3AfJhzGufBovf4nnPzDAABg" alt="" width="563"></div>

5. And paste them into DigitalOcean. Remember that DigitalOcean refers to the Name field as Hostname for all record types. For CNAME type records, it refers to the Value field as Is an Alias of.&#x20;

<div align="left" data-with-frame="true"><figure><img src="https://lh7-us.googleusercontent.com/pKpnIFGHlEZRLzah0cWwBVLHr3UublDrOpngcS4aGH2KquwbEPpn-pbxAs8PN5oYWlFdnqb_ii7-dh64Id0dhV3ue8bmpB3xiP3Rot_I68-Gu3MG-VHLldAc-kZjx_n3OkIYdwKVURL4zAfGWmlU3AI" alt="" width="563"><figcaption><p>Naming of TXT-type records in DigitalOcean</p></figcaption></figure></div>

<div align="left" data-with-frame="true"><figure><img src="https://lh7-us.googleusercontent.com/PCc1TfpITKClJ7UKv-G5rDpFj2w75KDvIUNy4cBmqVHy7pMGqfmZWMzcyLQM-jSm06eK9H71ErKc262DF4mUp1818eTuhOA5qJUNW7rAIhbn3oAueP9Zf8A4EbamI_q2tc5Ebcy-qK0G51n6Y9uy4oE" alt="" width="563"><figcaption><p>Naming of CNAME-type records in DigitalOcean</p></figcaption></figure></div>

6. Use the default value for TTL.&#x20;
7. Click Create Record after adding each record in DigitalOcean.&#x20;
8. Repeat the process of copying and pasting for each record until you’ve added all the Mailtrap DNS records to DigitalOcean.&#x20;

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/WyDAEe9K-ha4pS8WVu_kafysOVFL70xqD1zWW6-df-CavQmVMLUe2m-QmwcpB3SxJhqGfXx98T2zUykr_Lv7YoSqbwfhHCvgTY3fTlE_YHi8zsBR9QJadFI_QxClirZmNgectF-M2_sOylfFMneC7gM" alt="" width="563"></div>

9. Then, return to Mailtrap. Some records may be verified immediately, while some may take more time. Mailtrap will check the DNS records automatically every hour, but you can force a check by clicking the Re-check DNS Records button.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/n3BuZzCpa9auEJmGBfLq8kp4Y7Z9EsoUYpzcOmAmhvQK2vD_UdUVA5HgxlDnwlol9YzrnVLInF_JPJlO0G4MvW7dk_tDJEPCI77GG2LtvLrDeH3SsR0kY-ydXO0_qbCLeZ4eN76blwzBRL2AKG9l-Rw" alt="" width="563"></div>

10. If you add all the required DNS records correctly, the Status of DNS records will change from Missing to Verified, and the red dots will turn green.&#x20;

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/SEELEf34aJW3U6YP8FJCN3aBWwg47a52owTusSelnzUI3Q0TW8Jc1wFxyK3hqgXUCcK6yllCG409wSUNbPr5ufWLri38MSC3m9_UtksKmJB4OJgTd_n0DYidlJEbDQnuoAZ1hstN8CpipColPSIaH88" alt="" width="563"></div>

{% hint style="info" %}
_If you have additional questions,_ [_consult DigitalOcean documentation_](https://docs.digitalocean.com/products/networking/dns/how-to/manage-records/) _or contact us at_ [_support@mailtrap.io_](mailto:support@mailtrap.io)_._
{% endhint %}
