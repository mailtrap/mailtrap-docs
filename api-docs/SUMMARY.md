# Table of contents

* [Overview](README.md)
* [Authentication](authentication.md)
* [Rate Limits](rate-limits.md)
* [OpenAPI Specs](openapi-specs.md)

## Sending

* ```yaml
  props:
    models: false
    downloadLink: false
    expandOperations: false
  type: builtin:openapi
  dependencies:
    spec:
      ref:
        kind: openapi
        spec: email-sending-transactional
  ```
* ```yaml
  props:
    models: false
    downloadLink: false
    expandOperations: false
  type: builtin:openapi
  dependencies:
    spec:
      ref:
        kind: openapi
        spec: email-sending-bulk
  ```
* ```yaml
  props:
    models: false
    downloadLink: false
    expandOperations: false
  type: builtin:openapi
  dependencies:
    spec:
      ref:
        kind: openapi
        spec: email-batch
  ```

## Management

* ```yaml
  props:
    models: false
    downloadLink: false
    expandOperations: false
  type: builtin:openapi
  dependencies:
    spec:
      ref:
        kind: openapi
        spec: email-api
  ```

## Email Sandbox

* ```yaml
  props:
    models: false
    downloadLink: false
  type: builtin:openapi
  dependencies:
    spec:
      ref:
        kind: openapi
        spec: sandbox
  ```

## Email Marketing

* ```yaml
  props:
    models: false
    downloadLink: false
  type: builtin:openapi
  dependencies:
    spec:
      ref:
        kind: openapi
        spec: contacts
  ```

## Account Management

* ```yaml
  props:
    models: false
    downloadLink: false
  type: builtin:openapi
  dependencies:
    spec:
      ref:
        kind: openapi
        spec: general
  ```

## Webhooks

* ```yaml
  props:
    models: false
    downloadLink: false
  type: builtin:openapi
  dependencies:
    spec:
      ref:
        kind: openapi
        spec: webhooks
  ```
