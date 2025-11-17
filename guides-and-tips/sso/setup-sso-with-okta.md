---
title: <i class="fa-shield-halved">:shield-halved:</i> Setup SSO with Okta
description: Learn how to configure Single Sign-On (SSO) integration between Okta and Mailtrap using SAML 2.0, including role mapping and debugging.
---

# Overview

This guide walks you through setting up SSO integration between Okta and Mailtrap using SAML 2.0, including optional role mapping configuration.

## On Okta side

{% stepper %}
{% step %}
### Navigate to Applications and create integration

Navigate to Applications and click **Create App Integration**.

![Okta Create App Integration screen showing Web platform and SAML 2.0 selection](../.gitbook/assets/setup-sso-with-okta-1.png)
{% endstep %}

{% step %}
### Select Web Platform and SAML 2.0

Select the Web Platform and SAML 2.0 as the Sign on method.
{% endstep %}

{% step %}
### Enter app name

Enter app name and click on Next.
{% endstep %}

{% step %}
### Configure SAML Provider details

Provide the following SAML Provider details to Okta from Mailtrap:
- Entity ID = **Audience URI** (SP Entity ID)
- Assertion Consumer Service URL = **Single sign on URL**
- **Name ID format** should be set to `EmailAddress`
- **Application username** should be set to `email`

![Okta SAML settings configuration screen](../.gitbook/assets/setup-sso-with-okta-2.png)
{% endstep %}

{% step %}
### Add attribute mapping (Optional)

To apply role mapping please add used for mapping attribute in **Attribute Statements (optional)**
{% endstep %}

{% step %}
### Complete setup

Click **Next** and **Finish**.
{% endstep %}
{% endstepper %}

## On Mailtrap side

After configuration is ready on Okta side, next step would be to setup configuration on Mailtrap side.

In Okta, you will see info that "**SAML 2.0** is not configured until you complete the setup instructions"

![Okta showing SAML 2.0 setup incomplete message](../.gitbook/assets/setup-sso-with-okta-3.png)

{% stepper %}
{% step %}
### View Setup Instructions

Click **"View Setup Instructions"**

![Okta setup instructions showing Identity Provider details](../.gitbook/assets/setup-sso-with-okta-4.png)
{% endstep %}

{% step %}
### Provide Okta details to Mailtrap

Provide the following to Mailtrap from Okta:
- IdP Entity ID (Identity Provider Issuer) = Identity Provider Issuer
- Single Sign-on URL = Identity Provider Single Sign-On URL
- X509 Certificate = X509 Certificate
{% endstep %}

{% step %}
### Save configuration

Click Save in Mailtrap SSO configuration.
{% endstep %}

{% step %}
### Configure Role mapping (Optional)

For Role mapping there is additional configuration, please find more details in the SSO Guide Step 4: Role mapping section
{% endstep %}
{% endstepper %}

## SAML role mapping

There are different ways how you can configure your Okta to provide needed `attribute` to Mailtrap.

Mailtrap allows you to configure role attributes mapping (it's name and value). So you can configure will Mailtrap receive a role name from Okta or `true|false` as a value.

![Okta attribute configuration showing boolean values](../.gitbook/assets/setup-sso-with-okta-5.png)

Example of receiving boolean values in Attribute value

![Okta attribute configuration showing role name values](../.gitbook/assets/setup-sso-with-okta-6.png)

Example with Role name in Attribute value

There are several ways to do it in Okta. The best way is to consult with your team with help with configuration.

### Map Okta group names to Mailtrap permissions

1. Create groups in Okta
   - "MT Admin Group"
   - "MT Viewer Group"

![Okta groups list showing MT Admin and Viewer groups](../.gitbook/assets/setup-sso-with-okta-7.png)

2. Add users to groups
3. Update Okta application SAML attributes mapping

![Okta SAML attribute mapping configuration](../.gitbook/assets/setup-sso-with-okta-8.png)

4. Update attribute statements to return new SAML attributes:
   - `isMailtrapAdmin` with value `isMemberOfGroupName("MT Admin Group")`
   - `isMailtrapViewer` with value `isMemberOfGroup("00ggiqham4LuYTBPL5d7")`
     - `isMemberOfGroup` accepts group id. Group id can be taken from URL when visiting group page
   - More about Okta expressions language [here](https://developer.okta.com/docs/reference/okta-expression-language/)

![Okta attribute statements configuration](../.gitbook/assets/setup-sso-with-okta-9.png)

5. Add SAML attributes mapping in Mailtrap with same attribute names

![Mailtrap SSO role mapping configuration](../.gitbook/assets/setup-sso-with-okta-10.png)

## Debugging Okta integration

You can use [SAML tracer](https://developer.okta.com/docs/guides/saml-tracer/main/) to debug your SAML integration with Mailtrap.

You need to see a proper Attribute Name and Attribute Value in SAML request from Okta and they should matched to the ones you specified in Mailtrap SSO settings.
