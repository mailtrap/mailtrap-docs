---
description: AWS Route 53
---

# AWS Route 53

To add and verify a sending domain in Mailtrap, you need access to your domain’s DNS records and your domain provider account.&#x20;

<a href="broken-reference" class="button secondary">Sending Domain Setup</a> check it for more details on setting up your sending domain. Continue reading to learn how to add Mailtrap DNS records to AWS Route 53.&#x20;

{% hint style="info" %}
_This guide assumes that your domain is either registered and managed with AWS Route 53 or registered elsewhere but points to AWS Route 53. It also assumes that you’ve already created and configured a Hosted Zone for your domain._&#x20;
{% endhint %}

1. Go to the AWS Management Console, type Route 53 in the search bar, and click on it.&#x20;

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/q-O0xR-vxapizwnVBTgHKq79KieFLNckbd4OZBPrpP_9nRasrHFeltZPuE9m4e53YIjU2BqC15dA1BGjK-v_a_Tc2m_6sQt4_f88C2aRy-3UOvbgILzYeBG0eWq-9Zh_FuqBlBrROGBVNXPjLdA8jdE" alt="" width="375"></div>

2. Navigate to Hosted Zone settings for the domain you’ve added to Mailtrap.&#x20;

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/S1mHXb0m2-4Hm0ejRMcVEI3t8oA8oo4DqDTOARv-uZtvIjH_JlBAUC400cGTV2hQg6rex5CW5T9ODNi4XIVpgeD86NS4APCRpKHvdpIVTcTdp77SE5Y204WSj--9qeCI0Pbb1PoxvlPsPF59xnTFx4I" alt="" width="375"></div>

3. Click the domain you’ve added to Mailtrap.&#x20;

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/IrQNK6G1t8Xc51Zj9YnjWz3gfIukEmjmPfENjmUZKuR5A8Z7ESuSBX8N20VV2-RuQ3z-Xk4oKPWkI9FD0to7TUPaN-9Dqx4Rq4UoLNwctwEjLDhTIHTkKWM5rUr9IMSZLLrobW37OIgtUZAacvub7es" alt="" width="563"></div>

4. Click Create record button.&#x20;

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/le-dGEtyQwqdLP-5biQJRuOrHqNchcnTb60kMV_X71oyVxdGZOMsdWJK8RZjW0WZKf1DRyiOjxdsC4ltabRwskgoszDbF3Vy0BUogsn-TpFWdo9MBSgjWwiF6EHuNDU03UAJ_8YHdg04o1ky-eWhEqY" alt="" width="375"></div>

5. Return to Mailtrap. On the Domain Verification page, you’ll see the DNS records you need to add to AWS Route 53. These are Domain Verification, DKIM, SPF, DMARC, and Domain Tracking. You’ll need the values under Type, Name, and Value.&#x20;

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/GRkXpLcLv2GiCIRKw8GROf7Mrl_KVsgGqPT8ykSjPiINvsvS6KerRtc4YlnR8oNBqKEZBeLIV3tESJOtLrGSfYRaiejoBK2IhfvkemV1dcZjVyJ5C1BtSfBLFZ56INp6EYRSLULYVdIs9NxIjlrDZHo" alt="" width="563"></div>

Make sure you check the type next to each record in Mailtrap and choose a relevant one in AWS Route 53. There are four CNAME type records (Domain Verification, DKIM (2), and Custom Tracking Domain) and two TXT type records (SPF and DMARC).&#x20;

<div align="left" data-with-frame="true"><figure><img src="https://lh7-us.googleusercontent.com/yBlqx7eX3DXAsed4VggyJ_nNyLw1XiA27pDuVU-lQtMRVjRt_1jPTDXWj21GgAUnGy-Kd3nnmDshfEq8Rf-vZELQPa1k1YEKcMSpyGvh9AyIJssI7EUFGN1K3EzzA0edNLNRGhSEh9eMWkDwQ679CUg" alt="" width="563"><figcaption><p>DNS Types and Categories in Mailtrap </p></figcaption></figure></div>

{% hint style="warning" %}
_You should have only one SPF record. So, if you already have one for your domain, update its value to include Mailtrap. It’s okay to have multiple DMARC records._
{% endhint %}

6. Copy the Name and Value for each record one by one. You can do this by hovering and clicking each record.&#x20;

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/ntbM8E2Dbky4CQBUUMwn4o_6JmRO10NTsV0srdbL9aYTZp0HPNTJdAASPYpr6k5ufaD2Gr9CsHlMHJKncswOIs1WyIE7hka0oSgqSsCaHMmZiAwBcEbImTqAsqL7Z7aK5GCl-B1MwswyiXXir4OwMq4" alt="" width="563"></div>

7. And paste them into AWS Route 53. The namings of the records are the same in AWS Route 53 as in Mailtrap.&#x20;

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/BBdU5wPAes3rRUFsg6-dmpF60GC4D7uvHw0khwnZPmM1T9mtCtQS3tWhs2cYSTOMgi5KrkyavxRVW80VkRu8pRJy2kk1bu7Oldh1URudtS8PmQtYhQ8OyG1VP6sCWZl1prW7WWQhJzeLtatZtUog34M" alt="" width="563"></div>

8. Use the default value for TTL as indicated in Mailtrap.
9. Click Add another record after adding each record in AWS Route 53.&#x20;
10. Repeat the process of copying and pasting for each record until you’ve added all the Mailtrap DNS records to AWS Route 53. Click Create Records.&#x20;

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/GDT34rcF80mq2LhLdlh_KQ75GAtPEaP8NyhH7dUxM20H9wxbc7FhHWRX4Ec68YzJJpDhtbtec5Lqjp7hjBg3bBjAXNy_7MpGZ7fYqGXY2E_ZCwX3U-qlMNN78elEX0Grun7Ar45gIegwOkA0bC2UQYE" alt="" width="563"></div>

11. Then, return to Mailtrap. Some records may be verified immediately, while some may take more time. Mailtrap will check the DNS records automatically every hour, but you can force a check by clicking the Re-check DNS Records button.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/R1vtSymKKGP7B3ztsTWVH7L0nzAYjuuA2UurOz6rwAM7MHjNqPiNeeGpRUYDy_8BhlrYvxysSC7mloP63GCqLCknScHxGVko9EEbrIdN6gYyKKA6hLxZJxjlTpY1aszoZRKghRVIgGtoyx-5JSpttJs" alt="" width="563"></div>

12. If you add all the required DNS records correctly, the Status of DNS records will change from Missing to Verified, and the red dots will turn green.&#x20;

<div align="left" data-with-frame="true"><img src="https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/66164752d9cffa6c1049d26d/file-zEocAHY6Fc.png" alt="" width="563"></div>

{% hint style="info" %}
&#x20;_If you have additional questions,_ [_consult AWS documentation_](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/resource-record-sets-creating.html) _or contact us at_ [_support@mailtrap.io_](mailto:support@mailtrap.io)
{% endhint %}
