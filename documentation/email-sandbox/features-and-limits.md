---
title: Features and limits
description: All Mailtrap features and possible limits explained
---

## Total test emails per month

The maximum number of emails you can test with Sandbox per month, depends on your [billing plan](https://mailtrap.io/pricing/?tab=email-sandbox).

## Rate limits per 10 sec

The number of emails you can send to each of your Sandboxes every 10 seconds. The exact number depends on your billing plan.

Once the rate limit per 10 seconds is reached, the messages are not getting sent and are rejected with the error  "550 5.7.0 Requested action not taken: too many emails per second".

## Sandboxes

Sandboxes are separate folders where your test messages from different environments (Dev, QA, staging) are captured. Every Sandbox is created inside a Project - a folder which can be shared with other users, according to the Team Members options (available in the Team plan and more advanced billing plans)

## Projects

The groups that help you arrange your Sandboxes and distinguish different tasks you are working on simultaneously. You can share your projects with other team members (available in the Team and more advanced billing plans).

## Team members

Mailtrap users who you can interact with by inviting them to your account and sharing projects or the billing section. This feature is available from the Basic Testing plan and more advanced billing plans. [Click here](../user-management/user-management.md) to learn more about the User Management feature.

## Max emails per sandbox

The total number of emails you can store in each of your sandboxes at once. The exact number depends on your billing plan.When the limit is reached, Mailtrap uses the FIFO model for automatic sandbox cleanup (oldest messages first).

## Sandbox API

Sandbox API allows developers to run integration or load tests, as well as receive messages or email lists via API . To learn how to use the Email Sandbox API, refer to the [Email Sandbox API documentation](https://api-docs.mailtrap.io/docs/mailtrap-api-docs/a2041e813d169-sandbox-api).

## Email address per sandbox

The dedicated email address for each of your Sandboxes that you can use to send messages from other email accounts or right from your application during the testing process. It is available in the Basic Testing plan and more advanced billing plans.

## Email size, MB

The maximum allowed size of each email message, including attachments, in megabytes, is between 5MB and 25MB, depending on your plan.

## Total forwarded emails per month

The maximum number of emails you can forward from your account to real inboxes for testing and preview purposes. The maximum number of forwarding rules is 300. Email forwarding is available in the Basic Testing plan and more advanced billing plans.
