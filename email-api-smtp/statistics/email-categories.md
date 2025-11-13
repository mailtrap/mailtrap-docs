# Email Categories

Email Categories were built to show the performance of various types of emails, such as welcome emails, billing emails, confirmation emails, etc.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/Wd7CbaaScN5rdfFH1Gi1rlxt3hjixESk_LqxD0mjjs2MD4Vdb6aaBIJN_P8mWIUc6jXUH7gC-6w8h_04qA6SemooLhJr2irDObZWT0O9bsaQKPrSKaR9vgk3-iIJ5I0LUl0TnZosO4y40MCTb60cb6g" alt="" width="563"></div>

### Why should you use categories?

* See statistics for each type of email you send.
* Analyze key metrics of each category, such as open, click, or bounce rates. A single underperforming category can influence your overall sender reputation.
* Compare different types of emails and know straight away which perform better.
* Debug specific templates when, for example, an open rate suddenly drops.
* Simplify the search for any particular message. Filter out only emails matching a certain category to narrow down the results.

Email categories examples:

* “Feature XYZ intro”
* “Password reset 1st email”
* “Test A Order Confirmation”
* “Downgrade flow Tier 1”
* “Onboarding Msg 3”
* “Newsletter 04/20”

### How to use

You specify categories when creating an email to be sent with Mailtrap, by inserting a category name into the `X-MT-Category` header if you are using SMTP.

If you are using the API, refer to our [Api Docs](https://api-docs.mailtrap.io/docs/mailtrap-api-docs/67f1d70aeb62c-send-email-including-templates).

At this point, categories can only be specified when sending an email. Once you add one to an email and a message is sent, the category will appear in Mailtrap - in the Email Logs’ filters as well as in statistics.&#x20;

Categories cannot be removed or modified at this point. The number of categories in your account is unlimited.

### How to analyze performance

Categories can be tracked via the Email Categories tab in the Stats menu.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/A1iMU0riNtq2_h0I9KV4IcAgD0VQ447rtaWnyVLwGdbQxIlfGB1CdRTIFS9vIZG4F7NAD5rREEmgi8p7KTRa14rJIaE8DW9alBM_mAIVBQDTZjs5RWOaoAma1l95nKchIpzqQTLxbBXtLAIwK5Jz9hs" alt="" width="563"></div>

You can filter out the data for specific domains or mailbox providers using the filters. You can also limit the number of domains displayed and compare statistics only for some of them.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/X2D1t5yxsVbuXtErUtudEbHPUFR2RWe_liwnxZ9INLB-IxR2keY2WQd9A8vTvLeS7XRZ3ZGpZT3XmxXum7JtlqovW6cUyyW4RlOA9Yl8o9SwGhWC9o70CxHe2A_n1H0UkBHEM19sobJwG6HK-h1LRa0" alt="" width="563"></div>

Mailtrap tracks statistics for each day separately, which can sometimes lead to, for example, open rates going into hundreds of percent.

<div align="left" data-with-frame="true"><img src="https://lh7-us.googleusercontent.com/jnAcgiDWuXUlsXwPw0Knl7D33m0-dpIjWdV81w7A0GoleM1YDM0umfsR9ua_Y0ibf8okxjnma-XvTXBeIPfFouCM1p0K_2zV6l7L2y25VLMe2vpISgQTAeeqgxnnZ-nNNxeJg9OH_AGCcwG519UvERY" alt="" width="563"></div>
