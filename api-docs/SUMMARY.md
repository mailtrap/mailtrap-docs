# Table of contents

* [Overview](README.md)
* [Authentication](authentication.md)
* [Rate Limits](rate-limits.md)
* [OpenAPI Specs](openapi-specs.md)

## Email Sending

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
  type: builtin:openapi
  props:
    models: false
    downloadLink: false
  dependencies:
    spec:
      ref:
        kind: openapi
        spec: email-sending
  ```

## Promotional

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

## Inbound

* ```yaml
  type: builtin:openapi
  props:
    models: false
    downloadLink: false
  dependencies:
    spec:
      ref:
        kind: openapi
        spec: inbound
  ```

## Templates

* ```yaml
  props:
    models: false
    downloadLink: false
  type: builtin:openapi
  dependencies:
    spec:
      ref:
        kind: openapi
        spec: templates
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
        spec: sandbox-sending
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
        spec: account-management
  ```
