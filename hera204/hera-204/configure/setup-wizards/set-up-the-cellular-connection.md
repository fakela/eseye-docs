---
description: Configure cellular profiles in the Setup Wizard.
---

# Set up the cellular connection

The cellular connection page configures profiles used by the cellular WAN interface. Keep the existing profiles, or discard them and create a profile.

{% hint style="info" %}
This page does not appear in **Ethernet only** mode.
{% endhint %}

![Setup Pages — cellular profile](https://733576849-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FY2LsJ6998Uo7AtYcmJWd%2Fuploads%2FzmcvwTSnVlyIla0s0XYs%2Fsetup_pages_figure.png?alt=media\&token=c0bc1177-59c2-4eab-9684-cc49788ad7a4)

![Set up the connection (Cellular) — profile fields](https://733576849-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FY2LsJ6998Uo7AtYcmJWd%2Fuploads%2FqHwLxGnriASPYWadCzWT%2Fpage_image_figure_02.png?alt=media\&token=72333805-3659-4e0f-a5cf-6fd583e39105)

| Field name   | Value           | Description                                                                                  |
| ------------ | --------------- | -------------------------------------------------------------------------------------------- |
| Profile name | `wizardProfile` | Friendly name for the cellular profile. The wizard uses `wizardProfile` for a new profile.   |
| APN          | `eseye1`        | APN used by the cellular connection.                                                         |
| User name    | `user`          | APN username.                                                                                |
| Password     | `pass`          | APN password.                                                                                |
| PIN          | 0–99999999      | PIN for a protected SIM. Enter up to eight digits.                                           |
| SIM          | CHIP or SIM1    | SIM used for the connection. The Hera 204 has an embedded CHIP SIM and an external SIM slot. |
