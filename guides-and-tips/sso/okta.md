---
title: <i class="fa-shield-halved">:shield-halved:</i> Setup SSO with Okta
description: >-
  Learn how to configure Single Sign-On (SSO) integration between Okta and
  Mailtrap using SAML 2.0, including role mapping and debugging.
---

# Setup SSO with Okta

This guide walks you through setting up SSO integration between Okta and Mailtrap using SAML 2.0, including optional role mapping configuration.

## On Okta side

{% stepper %}
{% step %}
**Navigate to Applications and create integration**

Navigate to Applications and click **Create App Integration**.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-okta-1.png" alt="" width="375"></div>
{% endstep %}

{% step %}
**Select Web Platform and SAML 2.0**

Select the Web Platform and SAML 2.0 as the Sign on method.
{% endstep %}

{% step %}
**Enter app name**

Enter app name and click on Next.
{% endstep %}

{% step %}
**Configure SAML Provider details**

Provide the following SAML Provider details to Okta from Mailtrap:

* Entity ID = **Audience URI** (SP Entity ID)
* Assertion Consumer Service URL = **Single sign on URL**
* **Name ID format** should be set to `EmailAddress`
* **Application username** should be set to `email`

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-okta-2.png" alt="" width="563"></div>
{% endstep %}

{% step %}
**Add attribute mapping (Optional)**

To apply role mapping please add used for mapping attribute in **Attribute Statements (optional)**
{% endstep %}

{% step %}
**Complete setup**

Click **Next** and **Finish**.
{% endstep %}
{% endstepper %}

## On Mailtrap side

After configuration is ready on Okta side, next step would be to setup configuration on Mailtrap side.

In Okta, you will see info that "**SAML 2.0** is not configured until you complete the setup instructions"

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-okta-3.png" alt="" width="375"></div>

{% stepper %}
{% step %}
**View Setup Instructions**

Click **"View Setup Instructions"**

<div data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-okta-4.png" alt="Okta setup instructions showing Identity Provider details"></div>
{% endstep %}

{% step %}
**Provide Okta details to Mailtrap**

Provide the following to Mailtrap from Okta:

* IdP Entity ID (Identity Provider Issuer) = Identity Provider Issuer
* Single Sign-on URL = Identity Provider Single Sign-On URL
* X509 Certificate = X509 Certificate
{% endstep %}

{% step %}
**Save configuration**

Click Save in Mailtrap SSO configuration.
{% endstep %}

{% step %}
**Configure Role mapping (Optional)**

For Role mapping there is additional configuration, please find more details in the SSO Guide Step 4: Role mapping section
{% endstep %}
{% endstepper %}

## SAML role mapping

There are different ways how you can configure your Okta to provide needed `attribute` to Mailtrap.

Mailtrap allows you to configure role attributes mapping (it's name and value). So you can configure will Mailtrap receive a role name from Okta or `true|false` as a value.

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-okta-5.png" alt="Okta attribute configuration showing boolean values" width="375"></div>

Example of receiving boolean values in Attribute value

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-okta-6.png" alt="Okta attribute configuration showing role name values" width="563"></div>

Example with Role name in Attribute value

There are several ways to do it in Okta. The best way is to consult with your team with help with configuration.

### Map Okta group names to Mailtrap permissions

{% stepper %}
{% step %}
**Create Groups in Okta**

Create groups in Okta:

* "MT Admin Group"
* "MT Viewer Group"

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-okta-7.png" alt="Okta groups list showing MT Admin and Viewer groups" width="375"></div>
{% endstep %}

{% step %}
**Add Users to Groups**

Add users to groups
{% endstep %}

{% step %}
**Update SAML Attributes Mapping**

Update Okta application SAML attributes mapping

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-okta-8.png" alt="Okta SAML attribute mapping configuration" width="375"></div>
{% endstep %}

{% step %}
**Update Attribute Statements**

Update attribute statements to return new SAML attributes:

* `isMailtrapAdmin` with value `isMemberOfGroupName("MT Admin Group")`
* `isMailtrapViewer` with value `isMemberOfGroup("00ggiqham4LuYTBPL5d7")`
  * `isMemberOfGroup` accepts group id. Group id can be taken from URL when visiting group page
* More about Okta expressions language [here](https://developer.okta.com/docs/reference/okta-expression-language/)

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-okta-9.png" alt="Okta attribute statements configuration" width="375"></div>
{% endstep %}

{% step %}
**Add SAML Attributes Mapping in Mailtrap**

Add SAML attributes mapping in Mailtrap with same attribute names

<div align="left" data-with-frame="true"><img src="../.gitbook/assets/setup-sso-with-okta-10.png" alt="Mailtrap SSO role mapping configuration" width="563"></div>
{% endstep %}
{% endstepper %}

## Debugging Okta integration

You can use [SAML tracer](https://developer.okta.com/docs/guides/saml-tracer/main/) to debug your SAML integration with Mailtrap.

You need to see a proper Attribute Name and Attribute Value in SAML request from Okta and they should matched to the ones you specified in Mailtrap SSO settings.
