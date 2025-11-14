# Inspect your email template

* [View email in the sandbox and check its content](https://help.mailtrap.io/article/20-test-email-template#html-tab)
* [Check HTML template code for validity](https://help.mailtrap.io/article/20-test-email-template#check-html-tab)
* [Make sure that HTML and TEXT versions of your message match](https://help.mailtrap.io/article/20-test-email-template#text-tab)

**1. View the email in the sandbox and check its content**&#x20;

Go to the **HTML tab**. It opens by default when you open a message. This tab demonstrates how the email is rendered in a web browser.&#x20;

* Check whether the template looks as expected: Markup is correct, images are displayed, and fonts are supported.&#x20;
* Review the message content, click the links and buttons.&#x20;
* Test the message for responsiveness: click the device icons in the tab to see how it looks on mobile, tablet, and desktop.&#x20;

![](https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/63ff71e53c396c395ec0f514/file-N7Cq7V0kcK.png)

**2. Check the HTML template code for validity**

Email clients use different rendering standards. This is why your email can be displayed not as you designed it. You need to check that your message code won't cause rendering issues.&#x20;

**HTML Check** scans through your email in search of problematic elements. For each it finds, it displays the list of email clients that lack support for it or support it only partially. It also estimates the support for your emails’ code across popular email clients, making adjustments for their popularity.&#x20;

Go to the **HTML Check** tab to see the report:

![](https://lh3.googleusercontent.com/Q3EVzmZWZH5jw8kCd7iDf809N6AzLCI36sJFSF9afTLHsTojw4YwXlUpOA_Xq8tXmnhoK8JlUvKz0pobisr2FGXwp3Iajd2dNz9qjbqM4GWOC1pGPq1f3m1qPb-b8SL0cTzVkctQTY7p5aiGRcSP4FIXpdgSMi47DJy34Gz5dH_nxIMr-bgwF0H1Ug)

**HTML Check** collects the list of rules used in your email and compiles it with the supporting data we have for the most popular email clients. The final result is the Market Support - the overall level of HTML/CSS support for your email.

Below you will see a list of rules that cause errors in the specified email clients. To the right of each element, you can see the numbers (\[1], \[2], etc.). Click on any of them, and the “show more” section will expand, explaining what the issue is and which client/version it applies to.&#x20;

Clicking on the line number will take you to the **HTML Source** tab where you can view your email’s entire HTML.&#x20;

![](https://lh3.googleusercontent.com/06dKCE7Wa-dKAx7Y8PwC2HG97AN7WgBn4446LcS1b7lOsU0JugJMECPpnCORZi8Wgr78dc1n4PzxDODArZhlp0VkVmfk8WdY7sbbVbT9uifH-fSu82uGgePpPAmTuc2S42cFjWv4pn-oJ1JkeCyIkEPskHfh2jO-KlV9K8n_rqGzDTPp7dLCNboREQ)

To learn more about the HTML Check feature, refer to the [HTML Check article](https://help.mailtrap.io/article/60-html-check)**.**&#x20;

**3. Make sure that the HTML and TEXT versions of your message match**

It is important to include both the HTML and text versions in your message. This not only affects the spam score but also helps your recipients to understand your message if the HTML part hasn't rendered for some reason. Go to the **Text** tab to inspect the text version.

![](https://lh3.googleusercontent.com/lU2RhE6DCkQuP2d8Kv0yyJ8Jp-WxZBNpF6GeNNs_H_ZMIV_fr_ha_ARcnfSmf01cGJFrj34O5YFlMbR08nEpH9CCBuDBMgwQyulq_Q7lM6NL5oqxzjLszfaZeErmK8j4JDJWene01xz4ebTTZdJV2oeUsKMAmMg4gVXQ98Eqjgc0XcsN7R5I7pEFXw)
