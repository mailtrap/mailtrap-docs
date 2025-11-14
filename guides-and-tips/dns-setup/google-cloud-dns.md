---
description: >-
  Verify your Mailtrap sending domain in Google Cloud DNS. Add DNS records for
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

# Google Cloud DNS

To add and verify a sending domain in Mailtrap, you need access to your domain’s DNS records and your domain provider account.&#x20;

<a href="./" class="button secondary">Sending Domain Setup</a> check it for more details on setting up your sending domain. Continue reading to learn how to add Mailtrap DNS records to Google Cloud DNS.

{% hint style="info" %}
_Note: This guide assumes that your domain is either registered and managed with Google Cloud DNS or registered elsewhere but points to Google Cloud DNS. It also assumes that you’ve already created and configured a managed zone for your domain._&#x20;
{% endhint %}

1. Go to Google Cloud Console, type Cloud DNS in the search bar, and choose it from the results.&#x20;

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/F7O59bQYtOJ1KaydmyEbTl7i8XM2okDHbE880rzVMsKkuZEsLB9uTbqB0Z8-cpThPCWEQ88clE5e49ZTIklvhUbyDlQ51vKpdnvJrnHZCGd0ZBkX4sbp5Ze4EG5upRyDxqdU-5Jkn0R-FiCt8tN0a10" alt="" width="563"></div>

2. You’ll be taken to the Cloud DNS Zones page. Open the Zone details for the domain you’ve added to Mailtrap by clicking on the Zone name.&#x20;

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/VAAO9hWzOTRxFq0TFBDRGU5ezru3_zG7nB9b8VzfzVzS4qgGHuC44QT8lp7eayef6_aHKUnYRZgDe0-oh6DOeiL_I6SaXafKMoKTU54dXw19MkcQWtoajrCG8kXr3BWANSG4t8OywaF-7glIJRSCWTE" alt="" width="563"></div>

3. Click Add Standard.&#x20;

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/EuWIBxzj-_VbOqgfr6p0cA-96puXpbYOWq4kaK2KuSPNWwPe6ZCiOWgoH64U3PB2zmz7NjHdNCkcYjL4BIsHnnLS4fgh2rQmuQvM3kf7hUXshMErNeysmnpISSVvVNqWkCfpOPjJWEYKIbrcXifnQWg" alt="" width="563"></div>

4. Return to Mailtrap. On the Domain Verification page, you’ll see the DNS records you need to add to Google Cloud DNS. These are Domain Verification, DKIM, SPF, DMARC, and Domain Tracking. You’ll need the values under Type, Name, and Value. &#x20;

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/JRAb4U2DF1jruLzJfuaG9zRBGoSuLrIaj3CKZwlqO619TmCXkRAot_M8olJ8ulL2ARhqd6jOfsazjxktx2KHm3aoBL4bWUfDxMhxoV3PsamzQ_R0iJeShhFCYy64KLgj4J8JiT98Gml5xPww1G90szc" alt="" width="563"></div>

Make sure you check the type next to each record in Mailtrap and choose a relevant one in Google Cloud DNS. There are four CNAME type records (Domain Verification, DKIM (2), and Custom Tracking Domain) and two TXT type records (SPF and DMARC). Ignore Google’s SPF type record; it’s deprecated.

<div align="left" data-with-frame="true"><figure><img src="https://lh7-us.googleusercontent.com/hQrZQ1k6O7yqVY5gT3_GMcayL9no7tAIQSb5aGGZL1Cn4XgFeUgXo5wePTuoI1dQkAMOYRBA5-BIEBt_VsiJx1mbhbJ_vsOQ75Rcg17a4G7051cvIbs878oOtaehiu7f8_0SLlwUexSWLWo6XWtwqVE" alt="" width="563"><figcaption><p>DNS Types and Categories in Mailtrap </p></figcaption></figure></div>

Note that you should have only one SPF record. So, if you already have one for your domain, update its value to include Mailtrap. It’s okay to have multiple DMARC records.

5. Copy the Name and Value for each record one by one. You can do this by hovering and clicking each record.&#x20;

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/7dDZ0hd7GdDk0-vDo_2i2kY6ohsXl1yfwlxlqCh_umF3fEUynYBdgB3HkVIdhmqmR9z9UN1ILVWtvv3KpQHt0lf-rOpeTs7nHX9aOpWYm0SVv5R919ounDd9XDkT4sT1W3rUzztL9Nbk-zaaFBxnvR0" alt="" width="563"></div>

6. And paste them into Google Cloud DNS. Remember that Google Cloud DNS refers to the Name field as DNS Name and the Value field as either Canonical name (for CNAME-type records) or TXT data (for TXT-type records).

<div align="left" data-with-frame="true"><figure><img src="https://lh7-us.googleusercontent.com/2y3z8GLlGv-aHB9yen9A9LxcViEANMFoLSoPjhURkUTB_dgtWh2SUVdx8uSgyIrmeK9bxLzIq8BVFP0I2TX6_W7fiqVnF-yTxVZFPycE5_74DjpYopbEVBxulTnwSyC4XwyxvUFYkZPiEn0UeYnsY4U" alt="" width="375"><figcaption><p>CNAME-type record in Google Cloud DNS</p></figcaption></figure></div>

<div align="left" data-with-frame="true"><figure><img src="https://lh7-us.googleusercontent.com/sMFDBxmraucux4-57rv6mpK5mvJdnfjkCk4uKIW6aOwUHfwVoqQl2w0mdIKvZnvHp180OiKK6UCD_s5ugrDpWR-QUayvtaCMvIAHluH_lDP4djkN18H-TNK74htEsdQq5ZSR-eud0XqbIAlCezqNdZg" alt="" width="563"><figcaption><p>TXT-type record in Google Cloud DNS</p></figcaption></figure></div>

* When adding TXT-type records, add double quotes in the beginning and the end of the record string in the TXT data field. For example, you should enter `“v=spf1 include:_spf.smtp.mailtrap.live ~all”` instead of `v=spf1 include:_spf.smtp.mailtrap.live ~all` .&#x20;
* For SPF records, leave the DNS name field empty (don’t enter ‘@’ symbol as it’s not required in Google Cloud DNS).&#x20;

7. Use the default value for TTL.&#x20;
8. Click Create after adding each record in Google Cloud DNS.&#x20;

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/NK6dwLtJqYy1Uo7eEmSXZuQHJJ4twhW7jvLhjkBvUip4231VMLCUHX0cB7OZQ7u8ofirbMKbiSu_oenWw9rWkRyZcWL5SF_XrLG44X8960PeGykbF18af3BnduA-j-nrDYAlK95FH-2iCEQZcM0fkeQ" alt="" width="563"></div>

9. Repeat the process of copying and pasting for each record until you’ve added all the Mailtrap DNS records to Google Cloud DNS.&#x20;

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/sDKzw4v02BUJ_31ddXydENIvZBV5fx72bIhmTQ5efa_Xb2vnekvJVdjqSCcYZ26_Qr1SkZYfLoUHyJmzuey4_KV7QghezrunlL5I1-hJ9mqXgIJfXTNEQnX62e31cEmvKGPZngIhKunCFVQ5_DMQ4Ek" alt=""></div>

10. Then, return to Mailtrap. Some records may be verified immediately, while some may take more time. Mailtrap will check the DNS records automatically every hour, but you can force a check by clicking the Re-check DNS Records button.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/bA1_MZ1H8qa-kBkW7NJr_tzwS8N6I7qriL7KLs5fM6PMb0rgQmu6RzspTZBGFBuZ-yCBziLsHdiajepwngPZaq0wJtWRO3J1HxI922OKlwQ8TS-05tBHaBHbAk0wavMMMYcGN7nA6tMoNHK28RpVWwQ" alt="" width="563"></div>

11. If you add all the required DNS records correctly, the Status of DNS records will change from Missing to Verified, and the red dots will turn green.&#x20;

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/CUENvug4Hi0tAAXg3Htc3p20V8R-anirQUm0x_E2KOb9wF2Ga2F2TmZwtnqM6QmPhgL8Ht70m-HfhQdGcZZVdZ1k7imSdZQqi3QyZ-CiiIGE4cYUbkvZme6Tpn8Lwbm5FeIk7aXv9rB1HTm_9AmX0mY" alt="" width="563"></div>

{% hint style="info" %}
_If you have additional questions,_ [_consult Google Cloud DNS documentation_](https://cloud.google.com/dns/docs/records) _or contact us at_ [_support@mailtrap.io_](mailto:support@mailtrap.io)_._&#x20;
{% endhint %}
