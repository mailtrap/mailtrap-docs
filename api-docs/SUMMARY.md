# Table of contents

* [API Reference](README.md)
* [Authentication](authentication.md)

## Email API

* [Overview](email-api/overview.md)

### Sending

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
        spec: email-sending-transactional
  ```
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
        spec: email-sending-bulk
  ```
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
        spec: email-batch
  ```

### Management

* ```yaml
  type: builtin:openapi
  props:
    models: false
    downloadLink: false
    expandOperations: false
  dependencies:
    spec:
      ref:
        kind: openapi
        spec: email-api
  ```

## Email Sandbox

* [Overview](sandbox/overview.md)
* ```yaml
  type: builtin:openapi
  props:
    models: false
    downloadLink: false
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
    models: false
    downloadLink: false
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
    models: false
    downloadLink: false
  dependencies:
    spec:
      ref:
        kind: openapi
        spec: general
  ```

## Webhooks

* ```yaml
  type: builtin:openapi
  props:
    models: false
    downloadLink: false
  dependencies:
    spec:
      ref:
        kind: openapi
        spec: webhooks
  ```
