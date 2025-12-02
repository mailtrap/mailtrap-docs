---
title: Authentication
description: How to authenticate HTTP requests to Mailtrap APIs
---

# Authentication

There are several ways to send authenticated HTTP requests:

- Send a HTTP header `Api-Token: {api_token}`, where `{api_token}` is your API token
- Send a HTTP header `Authorization: Bearer {api_token}`, where `{api_token}` is your API token (more info: [Token Access Authentication](https://datatracker.ietf.org/doc/html/rfc6750))

You can manage your API token on the [API Tokens](https://mailtrap.io/api-tokens) page. API token does not have an expiration date, you may reset it manually.

{% hint style="info" %}
All requests must be sent over HTTPS protocol.
{% endhint %}

# HTTP Methods

Allowed HTTP requests include:

| Method | Description |
| ------ | ----------- |
| `POST` | Create a resource |
| `PATCH` | Update a resource |
| `PUT` | Replace a resource |
| `GET` | Get a resource or a list of resources |
| `DELETE` | Delete a resource |

# Response Codes

Here is the description of common server responses:

| Code | Status | Description |
| ---- | ------ | ----------- |
| `200` | OK | The request was successful (some API calls may return 201 instead) |
| `204` | No Content | The request was successful but there is no representation to return (i.e. the response is empty) |
| `401` | Unauthorized | Authentication failed or user doesn't have permissions for requested operation |
| `403` | Forbidden | Access denied |
| `404` | Not Found | Resource was not found |
| `422` | Unprocessable Entity | Requested data contain invalid values |
