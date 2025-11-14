# Deliverability tests

Learn how to check spam score and blacklisting.

### Spam Report

Go to the **Spam Analysis** tab to view the Spam Report. It contains the general score and a detailed table with spam test points and their descriptions.

[Apache SpamAssassin](https://mailtrap.io/blog/spamassassin-score/), the most popular email filter, runs numerous tests on email headers and body text and assigns a score to each of them.

A score below 5 points is considered good. If your email gets more than 5 points, it will most likely be treated as spam by various email clients. In this case, check the rules that gained the highest score and fix your email template accordingly.

![](https://lh3.googleusercontent.com/pco8hkEx5bycn315iT8A_Dxgk32bih3iRDc5P78C9uLhKaama9t3C3lrq6e0yXF072IfsuL50iqlKBBd7qh77fCfE9U7wdvWJult1E9xGnOZvPpyFOQkweuWVQYjPQrLbDFIBcrAOuSPxItwWZi6Ee-9dEEUMVF_QRymSVMHqdedVapSPFqIYucNOQ)

**Blacklists Report**

You will find the Blacklists Report in the **Spam** **Analysis** tab as well.

It checks whether your IP or domain has been listed on any of the commonly used blacklists. It shows resources that have been queried and your current status. If your domain or IP is blacklisted, click the resource name; it's hyperlinked to the blacklist website -- check their rules for delisting and follow their instructions.

![](https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/6349302e4d805871ceaa33e4/file-kPUnshfRWM.png)
