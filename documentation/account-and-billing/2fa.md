# 2FA

* [Setting up 2FA](https://help.mailtrap.io/article/153-2fa#Setting-up-2FA-G9N4i)
* [Disabling 2FA](https://help.mailtrap.io/article/153-2fa#Disabling-2FA-jf2bm)
* [Logging in via 2FA](https://help.mailtrap.io/article/153-2fa#Logging-in-via-2FA-x-3AR)
* [Recovering an account](https://help.mailtrap.io/article/153-2fa#Recovering-account-hpc-7)
* [Enforcing 2FA for all account users](https://help.mailtrap.io/article/153-2fa#Enforcing-2FA-as-an-account-administrator-N-R_R)
* [Email-based 2FA on unrecognized devices](https://help.mailtrap.io/article/153-2fa#Email-based-2FA-on-unrecognized-devices-Gj62j)
* [2FA Support FAQ](https://help.mailtrap.io/article/153-2fa#2FA-Support-FAQ-SlZCq)

### Setting up 2FA <a href="#setting-up-2fa-g9n4i" id="setting-up-2fa-g9n4i"></a>

1\. Go to Account (top-right) → My profile → Authentication&#x20;

2\. Click on Enable 2FA under the Two-Factor Authentication (2FA) section

![](https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/671793a46d43ca7b17b2c2a8/file-XqMLFOKqia.png)

You will then be taken to the 2FA setup page, where you can either:

* Use the authenticator app of your choice to scan the QR code
* Input the corresponding key if your authenticator app does not support QR scanning

![](https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/671794681198281bd860a416/file-AQCM4TY3nK.png)

Whichever of the two options you choose, your authenticator app will provide a code, which you need to enter in the following window, then click on Verify Code.

![](https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/6717943c44fbd7540103b9fb/file-IxxTMZqfum.png)

This will take you to the following page, where you will be provided with the recovery codes you can use in case you lose access to your authenticator app.

![](https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/6717949215d0b82233065a09/file-QILJzTOxE1.png)

Lastly, click on Finish Setup, and you will have enabled 2FA for your Mailtrap account.

### Disabling 2FA <a href="#disabling-2fa-jf2bm" id="disabling-2fa-jf2bm"></a>

1. Navigate to Account (top-right) → My profile → Authentication.
2. Click on Disable under the Two-Factor Authentication section.

![](https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/671794e644628317ef905813/file-TT7Hw9wjiw.png)

Please also note that disabling 2FA also resets the recovery codes, so after setting it up again, the old codes will no longer work, regardless of whether they had been used or not.

### Logging in via 2FA <a href="#logging-in-via-2fa-x-3ar" id="logging-in-via-2fa-x-3ar"></a>

During login, if you have enabled 2FA, you will be redirected to the following screen upon entering the correct username/password combination:

![](https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/671795038af27b34842c06b0/file-EZzvkj87Gp.png)

To successfully login, all you have to do is enter the code provided by your authenticator app.

### Recovering account <a href="#recovering-account-hpc-7" id="recovering-account-hpc-7"></a>

#### No access to the authenticator app

If you can’t access your authenticator app, simply use one of the recovery codes at the two-factor authentication step. Then, disable the 2FA and set it up with a different device or app. Please remember to save your new recovery codes, as the old ones will no longer work.

Important: Each recovery code only works once.&#x20;

#### Lost recovery codes

In case you cannot access or use your recovery codes for any reason, you can contact Support for help. Our Support Agent will:

* Confirm your identity
* Disable 2FA for your user

Lastly, the Support Agent will inform you that you can login and set up 2FA again.

Note: If 2FA is enforced by your account owner, you will be prompted to set it up the first time you log in.

### Enforcing 2FA for all account users <a href="#enforcing-2fa-as-an-account-administrator-n-r_r" id="enforcing-2fa-as-an-account-administrator-n-r_r"></a>

As a Mailtrap account owner, you can enforce 2FA for all users linked to the account, except those who login via SSO. Moreover, you can add a grace period, during which setting up 2FA can be skipped.

1\. Navigate to Settings → Account Settings → Two-Factor Authentication tab

2\. Tick the “Require 2FA for all users on this account” box

![](https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/671797266d43ca7b17b2c2ab/file-4wzHYZiOEk.png)

After enforcing 2FA as an account owner, you can set a grace period, during which the users can skip setting up 2FA. Simply choose the date on the calendar until which you want the grace period to last and click on Save Date.

![](https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/6717956915d0b82233065a0a/file-mGUfmP2r31.png)

### Email-based 2FA on unrecognized devices <a href="#email-based-2fa-on-unrecognized-devices-gj62j" id="email-based-2fa-on-unrecognized-devices-gj62j"></a>

To protect accounts with no 2FA enabled, Mailtrap will require email-based 2FA for new unrecognized devices.

1. On a new device, enter the correct username/password combination

![](https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/671795916d43ca7b17b2c2aa/file-5axd9mvEI2.png)

2. A verification code is then requested in order to proceed with the login.

![](https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/671795ad44fbd7540103b9fe/file-KmBXjaUL8H.png)

3. Check the inbox for the email address associated with your Mailtrap user. You should see an email from Mailtrap<[notifications@mailtrap.io](mailto:notifications@mailtrap.io)>, with the subject line “Verify your identity to proceed with the login.

![](https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/671795e08af27b34842c06b1/file-5pCiYsNiPL.png)

Important:

* If you are unable to find it in your inbox, please check your spam folder.
* To ensure the email reaches your inbox every time, please add [notifications@mailtrap.io](mailto:notifications@mailtrap.io) to your address book.
* Copy the code and paste it into the “verification code” field, then click “Verify”. Login should proceed as normal, and the device should be recognized on future logins.

![](https://d33v4339jhl8k0.cloudfront.net/docs/assets/5ed6bd832c7d3a10cba8416b/images/671795ad44fbd7540103b9fe/file-KmBXjaUL8H.png)

Cases when a new device might be detected:

* The same physical device but another browser&#x20;
* The same browser (e.g. Chrome) on a different physical device
* An updated version of the same browser on the same device
* The same version of the same browser on the same device, after some time has passed

### 2FA Support FAQ <a href="#id-2fa-support-faq-slzcq" id="id-2fa-support-faq-slzcq"></a>

#### 1. What’s happening? Why has our signing-in behavior changed?

Mailtrap implemented 2FA, or two-factor authentication, to additionally protect customer’s accounts against attackers.

#### 2. When did we release the changes?

We released those features on Monday Oct 7, 2024 1:08 PM (UTC+3:00)

#### 3. Can we disable the OTP sent via email?

There’s no way to disable the OTP sent via email. The only way to skip it is having 2FA enabled.
