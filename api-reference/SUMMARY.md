# Table of contents

* [Overview](README.md)
* [Add a user for Infinity API access](add-a-user-for-infinity-api-access.md)
* [Authentication](authentication/README.md)
  * [Request access token](authentication/request-access-token.md)

## API conventions

* [Request headers](api-conventions/request-headers.md)
* [Pagination](api-conventions/pagination.md)
* [Error handling](api-conventions/error-handling.md)

## Sim API

* [Overview](sim-api/overview.md)
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
        spec: anynet-sim-public
  ```

## Location API

* [Overview](location-api/overview.md)
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
        spec: location
  ```
* [Location Error Codes](location-api/location-error-codes.md)

## SMS

* [Overview](sms/overview.md)
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
        spec: sms
  ```

## Bulk Operations API

* [Overview](bulk-operations-api/overview.md)
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
        spec: bulk-operations
  ```
* [Error codes](bulk-operations-api/error-codes.md)

## Connectivity Metrics

* [Overview](connectivity-metrics/overview.md)
* [Authentication metrics](connectivity-metrics/authentication-metrics.md)
* [Accounting metrics](connectivity-metrics/accounting-metrics.md)
* [Traffic flow (NetFlow) metrics](connectivity-metrics/traffic-flow-netflow-metrics.md)
* [Correlate the datasets](connectivity-metrics/correlate-the-datasets.md)
* [How the data feed works (Delivery flow)](connectivity-metrics/how-the-data-feed-works-delivery-flow.md)
* [Scope and boundaries](connectivity-metrics/scope-and-boundaries.md)
* [Data volume and commercial model](connectivity-metrics/data-volume-and-commercial-model.md)

## Audit

* ```yaml
  type: builtin:openapi
  props:
    models: false
    downloadLink: true
    grouping: by-tag
  dependencies:
    spec:
      ref:
        kind: openapi
        spec: audit-family
  ```

## Common

* ```yaml
  type: builtin:openapi
  props:
    models: false
    downloadLink: true
    grouping: by-tag
  dependencies:
    spec:
      ref:
        kind: openapi
        spec: common-family
  ```

## Dictionary

* ```yaml
  type: builtin:openapi
  props:
    models: false
    downloadLink: true
    grouping: by-tag
  dependencies:
    spec:
      ref:
        kind: openapi
        spec: dictionary-family
  ```

## Invoice

* ```yaml
  type: builtin:openapi
  props:
    models: false
    downloadLink: true
    grouping: by-tag
  dependencies:
    spec:
      ref:
        kind: openapi
        spec: invoice-family
  ```

## MNO

* ```yaml
  type: builtin:openapi
  props:
    models: false
    downloadLink: true
    grouping: by-tag
  dependencies:
    spec:
      ref:
        kind: openapi
        spec: mno-family
  ```

## Order

* ```yaml
  type: builtin:openapi
  props:
    models: false
    downloadLink: true
    grouping: by-tag
  dependencies:
    spec:
      ref:
        kind: openapi
        spec: order-family
  ```

## Package

* ```yaml
  type: builtin:openapi
  props:
    models: false
    downloadLink: true
    grouping: by-tag
  dependencies:
    spec:
      ref:
        kind: openapi
        spec: package-family
  ```

## Portfolio

* ```yaml
  type: builtin:openapi
  props:
    models: false
    downloadLink: true
    grouping: by-tag
  dependencies:
    spec:
      ref:
        kind: openapi
        spec: portfolio-family
  ```

## Permission

* ```yaml
  type: builtin:openapi
  props:
    models: false
    downloadLink: true
    grouping: by-tag
  dependencies:
    spec:
      ref:
        kind: openapi
        spec: permission-family
  ```

## Report

* ```yaml
  type: builtin:openapi
  props:
    models: false
    downloadLink: true
    grouping: by-tag
  dependencies:
    spec:
      ref:
        kind: openapi
        spec: report-family
  ```

## SIMS Internal

* ```yaml
  type: builtin:openapi
  props:
    models: false
    downloadLink: true
    grouping: by-tag
  dependencies:
    spec:
      ref:
        kind: openapi
        spec: sim-family
  ```

## Ticket

* ```yaml
  type: builtin:openapi
  props:
    models: false
    downloadLink: true
    grouping: by-tag
  dependencies:
    spec:
      ref:
        kind: openapi
        spec: ticket-family
  ```

## Utility

* ```yaml
  type: builtin:openapi
  props:
    models: false
    downloadLink: true
    grouping: by-tag
  dependencies:
    spec:
      ref:
        kind: openapi
        spec: utility-family
  ```
