---
description: >-
  Connect AnyNet Secure SIM devices to AWS IoT Core using SIM-provisioned
  credentials.
---

# AnyNet Secure SIM Device Integration Developer Guide

Connect AnyNet Secure SIM devices to AWS IoT Core. Extract SIM-provisioned credentials with `AT+CRSM`, validate the files, and configure secure connectivity.

### Original PDF

{% file src="../.gitbook/assets/8424-AnyNet-Secure-SIM-Device-Integration-Developer-Guide.pdf" %}

{% hint style="info" %}
Source file: `8424-AnyNet-Secure-SIM-Device-Integration-Developer-Guide.pdf`
{% endhint %}

### Guide overview

* Prepare a SIM Toolkit-enabled modem and create a matching AWS IoT thing.
* Extract the SIM-provisioned identity and certificate files using `AT+CRSM`.
* Validate files with CRC-32 and convert DER certificate material when required.
