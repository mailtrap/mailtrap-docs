# API Tokens

* [Mailtrap Email API/SMTP](https://help.mailtrap.io/article/103-api-tokens#Mailtrap-Email-Sending-C-ZqM)
  * [Add and manage tokens manually](https://help.mailtrap.io/article/103-api-tokens#Add-and-manage-tokens-manually-4nBKj)
  * [Auto-created token per domain ](https://help.mailtrap.io/article/103-api-tokens#Auto-created-token-per-domain-wTkkI)
  * [Where to find tokens?](https://help.mailtrap.io/article/103-api-tokens#Where-to-find-tokens-5hMzB)
    * [API Integration](https://help.mailtrap.io/article/103-api-tokens#API-Integration-rMX3s)
    * [SMTP Integration](https://help.mailtrap.io/article/103-api-tokens#SMTP-Integration-Y42P2)
* [Email Sandbox](https://help.mailtrap.io/article/103-api-tokens#Mailtrap-Email-Testing-oO5xu)
  * [Where to find tokens?](https://help.mailtrap.io/article/103-api-tokens#Where-to-find-tokens-h2wP5)
* [Reset token](https://help.mailtrap.io/article/103-api-tokens#reset)
* [Edit permissions](https://help.mailtrap.io/article/103-api-tokens#edit)
* [Delete token](https://help.mailtrap.io/article/103-api-tokens#delete)

### Mailtrap Email API/SMTP <a href="#mailtrap-email-sending-c-zqm" id="mailtrap-email-sending-c-zqm"></a>

#### Add and manage tokens manually <a href="#add-and-manage-tokens-manually-4nbkj" id="add-and-manage-tokens-manually-4nbkj"></a>

Navigate to Settings in the menu on the left and select API Tokens.&#x20;

![](https://lh7-us.googleusercontent.com/HOHLr9BiceUOoSzAHzSinz0kCy1HrLoUMEeu0EVzpF6srKFvgZ6w35ITVn9FqkUFbMeIjoeaYtzAHqGU2_qSEUVHCHfltGRwt0wxTimDTOmYn48LBdI4Zz77_eJlTbThhgbR3HBbfJSsvyam4AGPXaY)

To add a new token, click the Add Token button in the upper right corner.&#x20;

![](https://lh7-us.googleusercontent.com/IVGXXUhhcdsnaO9Gq3vaehuJxiim5MJcUjo6fmBipZGGTA-oymsFko_edoUvBMbv4ZtLzVPQbEV5PtjArOn9lN-gmDun_hG48yyIUmZ98W_p8MQrk1K7NM-Qq5UGaZWtEj0ZsdgT-a0SSuP1aF3NGFU)

Type the token name into the designated field. It’s perfectly fine to have a custom name for the API token, as it’s only for your reference, regardless of the use case. &#x20;

Then, assign permissions by checking the boxes in the corresponding access level columns. Note that you must have admin permissions on a particular domain to send emails with this token.&#x20;

![](https://lh7-us.googleusercontent.com/J2h3E6nhkcN4QwFmvyZoAWvi4sl-Lkrj3_jfuCne4EJpGyV56Wx3hOrT4ofL-DNxBfnxUmptN-upsdqalSMSB9EMSsdNrpKIzlsc4xkJfeZYLb6uQ4MMqqCszRS7EuDp2Z2nVeEnv1Idn1A9vEYFFM0)

Click the Save button and preview the new token under the API Tokens main menu.&#x20;

#### Auto-created token per domain <a href="#auto-created-token-per-domain-wtkki" id="auto-created-token-per-domain-wtkki"></a>

When you create a domain, a token is automatically created and named based on the following formula: \[domain name] + \[token] + \[token ID].&#x20;

For example, if you add the example.com domain, the token for that domain will be named example.com token 1234. By default, the automatically generated token gets Domain Admin Mailtrap for the given domain.&#x20;

Note: You’ll need to edit permissions for the automatically generated token to allow for authorization on other domains.&#x20;

#### Where to find tokens? <a href="#where-to-find-tokens-5hmzb" id="where-to-find-tokens-5hmzb"></a>

**API Integration**

The automatically assigned token per domain is under the Integration tab in Sending Domains. Choose the desired stream, click Integrate, and toggle the switch to API. You’ll see the endpoint (Host) and your API Token.&#x20;

![](https://lh7-us.googleusercontent.com/wBOM1H64cF2sz12W6ykn_P9CeC10icdC4Lgdt8VeC7YcU1QCwLdY1w3eu3H3R2JFakvX4HCekNqgiEinWWAzB0fFc1Cc6qmkjn8h4S7nyJGCZ2Z2OY49gJDoGTQmd-5kUvBwU2sfjslAJ0n5vy-so5s)

**SMTP Integration**

The automatically assigned token per domain is under the Integration tab in Sending Domains. Choose the desired stream, click Integrate, and toggle the switch to SMTP. SMTP password is the same as the API Token. &#x20;

![](https://lh7-us.googleusercontent.com/JVVNUZ-yaCDccwChkNni8KgN1Pe8qHVESEg0dKzOseNNVdYyCZgCisZneCsBqOLLaHTdut-ntcz8-brzj5y-0haVCbnYYHG7ZXrILm05Fz_53xHvIyccwMyfQzK8xsxmoFeP_foZ6PR-qkUL7pgCqTc)

### &#x20;<a href="#reset-token-ahbet" id="reset-token-ahbet"></a>

### Email Sandbox <a href="#mailtrap-email-testing-oo5xu" id="mailtrap-email-testing-oo5xu"></a>

The guidelines assume that you’ve set up Email Sandbox and use the corresponding [APIv2](https://api-docs.mailtrap.io/docs/mailtrap-api-docs/a2041e813d169-sandbox-api).&#x20;

#### Where to find tokens? <a href="#where-to-find-tokens-h2wp5" id="where-to-find-tokens-h2wp5"></a>

Select Settings in the left menu, then API Tokens. You’ll see all active tokens, their creator, and their access level.&#x20;

![](https://lh7-us.googleusercontent.com/HOHLr9BiceUOoSzAHzSinz0kCy1HrLoUMEeu0EVzpF6srKFvgZ6w35ITVn9FqkUFbMeIjoeaYtzAHqGU2_qSEUVHCHfltGRwt0wxTimDTOmYn48LBdI4Zz77_eJlTbThhgbR3HBbfJSsvyam4AGPXaY)

Click the three-dot menu to the far right of the specific user token and select Edit permissions.&#x20;

![](https://lh7-us.googleusercontent.com/xPFulONHXCaefLhwXWJokoNxAH1OXFJsQd6_1Ckh0kOWR-_3cc4Ie3XWl2rZg6k6ZsfkWu9l-04kPdwPQh_K9PB9iaw0pMafiyeCb6oWkDR0bEUIRREOEtIRU3hnJs80rCQaxNnsJ7BAvM7RU0qxRSU)

\


Important Notes:

* You can also give Account Admin access to the token and get access to all Projects, Sandboxes, and domains on that account.&#x20;

![](https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/68b2f0cda00b8f11821d3f55/file-QkTsbzytP8.png)

If you want to test how it works, you need to get authenticated using your API token. Mailtrap uses Bearer Authentication, so you must pass the token under the Authorization header of your email.&#x20;

### Reset token <a href="#reset-token-ahbet" id="reset-token-ahbet"></a>

There are two ways to reset API tokens: clicking Reset Credentials under Integration or resetting them from the API Tokens menu.&#x20;

**Resetting API tokens from the Integration menu**

To reset tokens, go to the Integration tab in the Sending Domains menu and click Integrate under Transactional or Bulk Stream (depending on which tokens you want to reset). You’ll find the Reset Credentials function next to your credentials.&#x20;

![](https://lh7-us.googleusercontent.com/sc_AS430D6Y36R4l5ZsXhJYeV2mOjTjwlYeVce6_Ed3Ti60KfYEktjRj9sj47AtXLS917gqUjKKLjH9AlciRNiZIjEb1WCzxeWNeNzjqiA1P5eqval-naSFY0Yl8ao_I7x6MiCzye4x0LqbSrB1Dk8k)

Then, click Reset Credentials and confirm your choice with the Yes, Reset button.

![](https://lh7-us.googleusercontent.com/PN4NtmMp1y_LkjMH4MeU24KrN5SbwL33dRILFAd8Q4KchJ4wXw-KCjC8N-1VseuEArxGmY608cUbMmn1O7HbKMukdhcw8Gb23Pq_iP_kZL0zO5bcsS7AInZM2ptHesHm573ATeIYJ_4hv4KnPptzWbs)

**Resetting API Tokens from the API Tokens menu**

Go to API Tokens, click the three-dot menu icon next to the token you want to reset, and click Reset API Token.&#x20;

![](https://lh7-us.googleusercontent.com/ptIjbOxoGzED9uf-o7pXySTtgDt51sh5qmaS5vd_k38cb-0AN7Ks7lPuPTi6751U_rdTSNctjf9jPdo81AY4YHMZDasW429H77dzg15DjLBng5nz6v44x94V0YpJn6mzU8rcm-kp4zSvCNhhSGkys40)

Confirm your choice by clicking on the corresponding button.&#x20;

![](https://lh7-us.googleusercontent.com/qPGiUH7XGCLr1aCkAGhuRm6qhCqsZpRrAnasy44faYQvuJ0I1UOEpdNCYHGoZ8MHDWyTU8au5Edm0m6Cj5F9vRFmzdTHoZHjCEc6OTZwldmb9bJi2ZOTqRz0nuj3IC8EbCKRR7qOIYcP4a8OYCbw558)

Tip: The three-dot menu icon next to the token also allows you to copy a token to your clipboard.&#x20;

Important Notes:

* After clicking the Reset credentials or Reset API Token buttons, the existing token becomes invalid after 12 hours. So, you have a 12-hour window to update all apps that use the old API token. Once the old token expires, some parts of your application will not work properly unless you’ve updated the token. All expired tokens get deleted from your account within 24 hours after expiration.&#x20;
* After the API token is reset and expired, a new token is created. The token ID is added to the token name the same way it’s done for automatically generated tokens, e.g., mailtrap.example token 4231.

#### Edit permissions

As mentioned earlier, click the menu icon at the far right of a token and select Edit permissions.&#x20;

![](https://lh7-us.googleusercontent.com/twK_Fv_N2SigRoOe6SPIQcw1fQVVQXGCWceHXZ3tHjSXGisuCzFnsTHWFjmdIdsVzbK3c-MEw46oYOApOf9k0hFoJe_II-aS8-rl76BLaG8OOZbD-ZU37aKG1Pijq8a1yEKo9854Kc02RpzEvONYd5Q)

Click on the corresponding boxes to add or remove token permissions. Then, confirm your selection with the Save button.&#x20;

#### Delete token

To delete a token, click a three-dot menu icon and choose the Delete token option.&#x20;

![](https://lh7-us.googleusercontent.com/rGbs6ZE_ziTFqBGDlIc7p0YOABxGPoasxBWFJeA3pPd1oVZumnlu8gZIBntjGmIoyvGOeqm2MnAuH-th5jQCj-EnDWhAPgDBH5pUh4E5gYey6vSFZ_gKOZJ2d4Fz2ZD8ppRzXFDwdxuu-v0-4GXtm8o)

Confirm the action by clicking the Confirm button.

![](https://lh7-us.googleusercontent.com/QugUqWhTHcVC3zF6uVDmMGLAd8LqZI3O6srotIdDbbTUsgr1ermaZsL2yq08_SCZgEtymFoFy7SX-ap1X1AKXhLwiXj0SOMEQQCi9X-vM8IjofVHC8FMkD4O0o4eO-3xOdp-iricNx8Xgq5Vqi4ku8I)

Important Note: Keep in mind that a token is deleted immediately, and you can’t delete the last token per domain.

\
