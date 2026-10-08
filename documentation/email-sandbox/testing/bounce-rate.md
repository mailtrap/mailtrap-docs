---
title: Bounce Emulator
description: >-
  Learn how to test your SMTP client's behavior when the server responds with an
  error
icon: arrow-turn-down-left
---

# Bounce Emulator

## Constructing the address

The recipient's username should start with bounce+ and contain the response in URL-encoded form: `bounce+550+no+such+user+here@inbox.mailtrap.io`. The domain must be `inbox.mailtrap.io`.

If you send to `bounce@inbox.mailtrap.io` without a custom response, you'll get the default one: `550 5.1.1 The email account that you tried to reach does not exist.`

To create it, use [https://www.urlencoder.org](https://www.urlencoder.org/) or any other URL encoding solution.

Tip: Write the address in lowercase. For example, `Bounce+...` won't trigger the emulator. To get capital letters in the response text, use URL encoding:  `bounce+550+%4Eo+such+user+here@inbox.mailtrap.io` returns `550 No such user here`.

## Using Bounce Emulator with an email client

Just use the inbox.mailtrap.io host with any email client or application and send an email to `bounce+451+server+unavailable@inbox.mailtrap.io` .

## Using Bounce Emulator with Sandbox

If your application is connected to Email Sandbox SMTP, send an email from the application to `bounce+454+authentication+required@inbox.mailtrap.io` , and your application will receive a bounce response from the Sandbox SMTP server. Bounce addresses on any other domain are captured in your inbox as regular emails.

_Note: This feature does not work with API, as bounce codes are specific to SMTP._
