---
title: Untitled
---

<details>

<summary><mark style="color:$info;">object · SendingWebhookEvent</mark> <mark style="color:blue;">optional</mark><br><mark style="color:$info;">Email lifecycle webhook event</mark></summary>

**event** <mark style="color:$info;">string · enum</mark> <mark style="color:$warning;">required</mark>\
<mark style="color:$info;">Event type</mark>\ <mark style="color:$info;">Possible values</mark>: `delivery` `open` `click` `unsubscribe` `spam` `soft bounce` `bounce` `suspension` `reject`

**message\_id** <mark style="color:$info;">string</mark> <mark style="color:$warning;">required</mark>\
<mark style="color:$info;">Unique message ID</mark>&#x20;

**sending\_stream** <mark style="color:$info;">string · enum</mark> <mark style="color:$warning;">required</mark>\
<mark style="color:$info;">Sending stream used</mark>\
<mark style="color:$info;">Possible values:</mark> `transactional` `bulk`

**email** <mark style="color:$info;">string</mark> <mark style="color:$warning;">required</mark>\
<mark style="color:$info;">Recipient email address</mark>

**sending\_domain\_name** <mark style="color:$info;">string</mark> <mark style="color:$warning;">required</mark>\
<mark style="color:$info;">Sending domain name</mark>

**category** <mark style="color:$info;">string</mark> <mark style="color:$primary;">optional</mark>\
<mark style="color:$info;">Category assigned when sending</mark>

**custom\_variables** <mark style="color:$info;">object</mark> <mark style="color:$primary;">optional</mark>\
<mark style="color:$info;">Custom variables from the email</mark>

* **Other properties** <mark style="color:$info;">string | number | boolean</mark> <mark style="color:$primary;">optional</mark>

**timestamp** <mark style="color:$info;">integer</mark> <mark style="color:$warning;">required</mark>\
<mark style="color:$info;">Unix epoch timestamp</mark>

**event\_id** <mark style="color:$info;">string</mark> <mark style="color:$warning;">required</mark>\
<mark style="color:$info;">Unique event ID (use for idempotency)</mark>

**reason** <mark style="color:$info;">string</mark> <mark style="color:$primary;">optional</mark>\
<mark style="color:$info;">Reason (for</mark> `suspension` <mark style="color:$info;">and</mark> `reject` <mark style="color:$info;">events)</mark>

**response** <mark style="color:$info;">string</mark> <mark style="color:$primary;">optional</mark>\
<mark style="color:$info;">Server response (for</mark> `soft bounce` <mark style="color:$info;">and</mark> `bounce` <mark style="color:$info;">events)</mark>

**response\_code** <mark style="color:$info;">integer</mark> <mark style="color:$primary;">optional</mark>\
<mark style="color:$info;">SMTP response code (for</mark> `soft bounce` <mark style="color:$info;">and</mark> `bounce` <mark style="color:$info;">events)</mark>

**bounce\_category** <mark style="color:$info;">string</mark> <mark style="color:$primary;">optional</mark>\
<mark style="color:$info;">Bounce category (for</mark> `soft bounce` <mark style="color:$info;">and</mark> `bounce` <mark style="color:$info;">events)</mark>

**ip** <mark style="color:$info;">string</mark> <mark style="color:$primary;">optional</mark>\
<mark style="color:$info;">User IP address (for</mark> `open`<mark style="color:$info;">,</mark> `click`<mark style="color:$info;">,</mark> `unsubscribe` <mark style="color:$info;">events)</mark>

**user\_agent** <mark style="color:$info;">string</mark> <mark style="color:$primary;">optional</mark>\
<mark style="color:$info;">User agent (for</mark> `open`<mark style="color:$info;">,</mark> `click`<mark style="color:$info;">,</mark> `unsubscribe` <mark style="color:$info;">events)</mark>

**url** <mark style="color:$info;">string</mark> <mark style="color:$primary;">optional</mark> \
<mark style="color:$info;">Clicked URL</mark> <mark style="color:$info;">(for</mark> `click` <mark style="color:$info;">events)</mark>

</details>

<details>

<summary><mark style="color:$info;">object · ActivityLogWebhookEvent</mark> <mark style="color:$primary;">optional</mark><br><mark style="color:$info;">Account activity webhook event (Enterprise only)</mark></summary>

**event** <mark style="color:$info;">string</mark> <mark style="color:$warning;">required</mark>\
<mark style="color:$info;">Activity log event type</mark>\ <mark style="color:$info;">Example:</mark> `activity_log.user.updated`

**description** <mark style="color:$info;">string</mark> <mark style="color:$warning;">required</mark>\
<mark style="color:$info;">User-friendly event description</mark>\ <mark style="color:$info;">Example:</mark> `updated the user profile`

**actor** <mark style="color:$info;">object</mark> <mark style="color:$warning;">required</mark>\
<mark style="color:$info;">User or system that performed the action</mark>

* **id** <mark style="color:$info;">integer</mark> <mark style="color:$primary;">optional</mark>\
  <mark style="color:$info;">Actor ID</mark>\ <mark style="color:$info;">Example:</mark> `1`
* **type** <mark style="color:$info;">string · enum</mark> <mark style="color:$primary;">optional</mark>\
  <mark style="color:$info;">Actor type</mark>\ <mark style="color:$info;">Possible values:</mark> `user` `api_token`
* **name** <mark style="color:$info;">string</mark> <mark style="color:$primary;">optional</mark>\
  <mark style="color:$info;">Actor name</mark>\ <mark style="color:$info;">Example:</mark> `John Doe`

**resource** <mark style="color:$info;">object</mark> <mark style="color:$primary;">optional</mark>\
<mark style="color:$info;">Affected resource (optional)</mark>

* **id** <mark style="color:$info;">string</mark> <mark style="color:$primary;">optional</mark>\
  <mark style="color:$info;">Resource ID</mark>\ <mark style="color:$info;">Example:</mark> `1`
* **type** <mark style="color:$info;">string · enum</mark> <mark style="color:$primary;">optional</mark>\
  <mark style="color:$info;">Resource type</mark>\ <mark style="color:$info;">Possible values:</mark> `user` `api_token` `billing` `account` `sso_config` `sending_domain` `project` `inbox` `contact_list` <kbd>contact\_field</kbd> `contact_segment`
* **name** <mark style="color:$info;">string</mark> <mark style="color:$primary;">optional</mark>\
  <mark style="color:$info;">Resource name</mark>\ <mark style="color:$info;">Example:</mark> `John Doe`

**changes** <mark style="color:$info;">object</mark> <mark style="color:$primary;">optional</mark>\
<mark style="color:$info;">Changes made (optional)</mark>\ <mark style="color:$info;">Example:</mark> `{"name":{"from":"John","to":"John Doe"}}`

* **Other properties** <mark style="color:$info;">object</mark> <mark style="color:$primary;">optional</mark>

**timestamp** <mark style="color:$info;">integer</mark> <mark style="color:$warning;">required</mark>\
<mark style="color:$info;">Unix epoch timestamp</mark>\ <mark style="color:$info;">Example:</mark> `1735830138`

</details>
