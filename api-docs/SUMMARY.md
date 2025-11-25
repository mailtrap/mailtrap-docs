# Table of contents

* [API Reference](README.md)

## Email API

* [Overview](email-api/overview.md)
* ```yaml
  type: builtin:openapi
  props:
    models: true
    downloadLink: true
    expandOperations: false
  dependencies:
    spec:
      ref:
        kind: openapi
        spec: email-api
  ```
* [Email Templates](templates/overview.md)

## Email Sandbox

* [Overview](sandbox/overview.md)
* ```yaml
  type: builtin:openapi
  props:
    models: true
    downloadLink: true
  dependencies:
    spec:
      ref:
        kind: openapi
        spec: sandbox
  ```

## Email Marketing

* [Contacts API](contacts/overview.md)
* ```yaml
  type: builtin:openapi
  props:
    models: true
    downloadLink: true
  dependencies:
    spec:
      ref:
        kind: openapi
        spec: contacts
  ```

## Account Management

* [General API](general/overview.md)
* ```yaml
  type: builtin:openapi
  props:
    models: true
    downloadLink: true
  dependencies:
    spec:
      ref:
        kind: openapi
        spec: general
  ```

## Webhooks

* [Webhooks API](webhooks/overview.md)
* ```yaml
  type: builtin:openapi
  props:
    models: true
    downloadLink: true
  dependencies:
    spec:
      ref:
        kind: openapi
        spec: webhooks
  ```
