# Table of contents

* [Overview](README.md)
* [Authentication](authentication.md)
* [Rate Limits](rate-limits.md)
* [OpenAPI Specs](openapi-specs.md)

## Email Sending

* ```yaml
  type: builtin:openapi
  props:
    models: false
    downloadLink: false
    grouping: by-operation
  dependencies:
    spec:
      ref:
        kind: openapi
        spec: email-sending-transactional
  ```
* ```yaml
  type: builtin:openapi
  props:
    models: false
    downloadLink: false
    grouping: by-operation
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
    grouping: by-operation
  dependencies:
    spec:
      ref:
        kind: openapi
        spec: email-sending
  ```

## Email Sandbox

* ```yaml
  type: builtin:openapi
  props:
    models: false
    downloadLink: false
    grouping: by-operation
  dependencies:
    spec:
      ref:
        kind: openapi
        spec: sandbox-sending
  ```
* ```yaml
  type: builtin:openapi
  props:
    models: false
    downloadLink: false
    grouping: by-operation
  dependencies:
    spec:
      ref:
        kind: openapi
        spec: sandbox
  ```

## Email Marketing

* ```yaml
  type: builtin:openapi
  props:
    models: false
    downloadLink: false
    grouping: by-operation
  dependencies:
    spec:
      ref:
        kind: openapi
        spec: contacts
  ```
* ```yaml
  type: builtin:openapi
  props:
    models: false
    downloadLink: false
    grouping: by-operation
  dependencies:
    spec:
      ref:
        kind: openapi
        spec: email-campaigns
  ```

## Inbound

* ```yaml
  type: builtin:openapi
  props:
    models: false
    downloadLink: false
    grouping: by-operation
  dependencies:
    spec:
      ref:
        kind: openapi
        spec: inbound
  ```

## Templates

* ```yaml
  type: builtin:openapi
  props:
    models: false
    downloadLink: false
    grouping: by-operation
  dependencies:
    spec:
      ref:
        kind: openapi
        spec: templates
  ```

## Account Management

* ```yaml
  type: builtin:openapi
  props:
    models: false
    downloadLink: false
    grouping: by-operation
  dependencies:
    spec:
      ref:
        kind: openapi
        spec: account-management
  ```
