---
title: 2FA
description: >-
  Set up two-factor authentication (2FA) for your Mailtrap account to enhance
  security. Learn how to enable, disable, and recover your account with 2FA.
---

# 🔐 Two-Factor Authentication

### Setting up 2FA

1. Go to Account (top-right) → My profile → Authentication
2. Click on Enable 2FA under the Two-Factor Authentication (2FA) section

<div align="left"><img src="../.gitbook/assets/2fa-enable-button.png" alt="Mailtrap My Profile Authentication page showing Enable 2FA button under Two-Factor Authentication section" width="563"></div>

You will then be taken to the 2FA setup page, where you can either:

* Use the authenticator app of your choice to scan the QR code
* Input the corresponding key if your authenticator app does not support QR scanning

<div align="left"><img src="../.gitbook/assets/2fa-setup-qr-code.png" alt="2FA setup page displaying QR code and manual key for authenticator app configuration" width="563"></div>

Whichever of the two options you choose, your authenticator app will provide a code, which you need to enter in the following window, then click on Verify Code.

<div align="left"><img src="../.gitbook/assets/2fa-verify-code.png" alt="2FA verification page with code input field and Verify Code button" width="563"></div>

This will take you to the following page, where you will be provided with the recovery codes you can use in case you lose access to your authenticator app.

<div align="left"><img src="../.gitbook/assets/2fa-recovery-codes.png" alt="2FA recovery codes page displaying multiple recovery codes with download and copy options" width="563"></div>

Lastly, click on Finish Setup, and you will have enabled 2FA for your Mailtrap account.

### Disabling 2FA

1. Navigate to Account (top-right) → My profile → Authentication.
2. Click on Disable under the Two-Factor Authentication section.

<div align="left"><img src="../.gitbook/assets/2fa-disable-button.png" alt="Mailtrap My Profile Authentication page showing Disable button for Two-Factor Authentication" width="563"></div>

Please also note that disabling 2FA also resets the recovery codes, so after setting it up again, the old codes will no longer work, regardless of whether they had been used or not.

### Logging in via 2FA

During login, if you have enabled 2FA, you will be redirected to the following screen upon entering the correct username/password combination:

<div align="left"><img src="../.gitbook/assets/2fa-login-screen.png" alt="Mailtrap login page showing two-factor authentication code input field" width="563"></div>

To successfully login, all you have to do is enter the code provided by your authenticator app.

### Recovering account

#### No access to the authenticator app

If you can't access your authenticator app, simply use one of the recovery codes at the two-factor authentication step. Then, disable the 2FA and set it up with a different device or app. Please remember to save your new recovery codes, as the old ones will no longer work.

Important: Each recovery code only works once.

#### Lost recovery codes

In case you cannot access or use your recovery codes for any reason, you can contact Support for help. Our Support Agent will:

* Confirm your identity
* Disable 2FA for your user

Lastly, the Support Agent will inform you that you can login and set up 2FA again.

Note: If 2FA is enforced by your account owner, you will be prompted to set it up the first time you log in.

### Enforcing 2FA for all account users

As a Mailtrap account owner, you can enforce 2FA for all users linked to the account, except those who login via SSO. Moreover, you can add a grace period, during which setting up 2FA can be skipped.

1. Navigate to Settings → Account Settings → Two-Factor Authentication tab
2. Tick the "Require 2FA for all users on this account" box

<div align="left"><img src="../.gitbook/assets/2fa-enforce-account-setting.png" alt="Account Settings page with Require 2FA for all users checkbox highlighted" width="563"></div>

After enforcing 2FA as an account owner, you can set a grace period, during which the users can skip setting up 2FA. Simply choose the date on the calendar until which you want the grace period to last and click on Save Date.

<div align="left"><img src="../.gitbook/assets/2fa-grace-period-calendar.png" alt="2FA grace period settings with calendar date picker for setting grace period end date" width="563"></div>

### Email-based 2FA on unrecognized devices

To protect accounts with no 2FA enabled, Mailtrap will require email-based 2FA for new unrecognized devices.

1. On a new device, enter the correct username/password combination

<div align="left"><img src="../.gitbook/assets/2fa-email-login-credentials.png" alt="Mailtrap login page showing username and password input fields" width="563"></div>

2. A verification code is then requested in order to proceed with the login.

<div align="left"><img src="../.gitbook/assets/2fa-email-verification-code.png" alt="Email-based verification code input page requesting code from email" width="563"></div>

3. Check the inbox for the email address associated with your Mailtrap user. You should see an email from Mailtrap<[notifications@mailtrap.io](mailto:notifications@mailtrap.io)>, with the subject line "Verify your identity to proceed with the login.

<div align="left"><img src="../.gitbook/assets/2fa-email-inbox.png" alt="Email inbox showing Mailtrap verification email with subject Verify your identity to proceed with the login" width="563"></div>

Important:

* If you are unable to find it in your inbox, please check your spam folder.
* To ensure the email reaches your inbox every time, please add [notifications@mailtrap.io](mailto:notifications@mailtrap.io) to your address book.
* Copy the code and paste it into the "verification code" field, then click "Verify". Login should proceed as normal, and the device should be recognized on future logins.

<div align="left"><img src="../.gitbook/assets/2fa-email-verification-code.png" alt="Email-based verification code input page requesting code from email" width="563"></div>

Cases when a new device might be detected:

* The same physical device but another browser
* The same browser (e.g. Chrome) on a different physical device
* An updated version of the same browser on the same device
* The same version of the same browser on the same device, after some time has passed

### 2FA Support FAQ

#### 1. What's happening? Why has our signing-in behavior changed?

Mailtrap implemented 2FA, or two-factor authentication, to additionally protect customer's accounts against attackers.

#### 2. When did we release the changes?

We released those features on Monday Oct 7, 2024 1:08 PM (UTC+3:00)

#### 3. Can we disable the OTP sent via email?

There's no way to disable the OTP sent via email. The only way to skip it is having 2FA enabled.
