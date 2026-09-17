# Wireless

## Wireless Configuration

Configure the Hera 204 wireless interface. The router uses a 2.4/5 GHz dual-band radio.

| Field name       | Sample value                   | Explanation                                                                                  |
| ---------------- | ------------------------------ | -------------------------------------------------------------------------------------------- |
| 1. Hardware Mode | 802.11g                        | Selects the 802.11 standard. Options work with the bandwidth setting.                        |
| 2. Status        | Enabled                        | Shows whether the radio is enabled or disabled.                                              |
| 3. Country       | USA (United States of America) | Ensures local compliance and compatibility. Available channels vary by country.              |
| 4. Channel       | Auto                           | Wi-Fi channel used by the Hera 204 radio. Availability depends on hardware mode and country. |
| 5. Bandwidth     | 802.11ac rates 80MHz           | Selects bandwidth rates. Options vary by hardware mode.                                      |

![Wireless Configuration](https://733576849-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FY2LsJ6998Uo7AtYcmJWd%2Fuploads%2FbXV8Jy1C55ZSUFThz5bc%2Fwireless_configuration_screenshot.png?alt=media\&token=d2f16aaa-b2e3-462f-9b4f-a1128f06a4dc)

### How wireless configuration works

**2.4 GHz mode:** The wireless module selects 2.4 GHz mode when Hardware Mode is `802.11b` or `802.11g`.

With `802.11g`, select 20 MHz or 40 MHz bandwidth to enable 802.11n mode on 2.4 GHz.

**5 GHz mode:** The wireless module selects 5 GHz mode when Hardware Mode is `802.11a`.

Use Bandwidth to upgrade from 802.11a to 802.11n or 802.11ac. Available bandwidth ranges from 20 MHz to 80 MHz.

## Access Points

Configure wireless access points on the Hera 204 router.

![Access Points](https://733576849-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FY2LsJ6998Uo7AtYcmJWd%2Fuploads%2FMVTkX6IN8rDxvo6VvnNV%2Faccess_points_figure.png?alt=media\&token=7bd8a0c7-5e5e-4328-a691-73f3fa26df49)

| Field name              | Sample value                                         | Explanation                                                      |
| ----------------------- | ---------------------------------------------------- | ---------------------------------------------------------------- |
| 1. Name                 | Default\_radio0                                      | Name for the access point.                                       |
| 2. Device               | Wifi0                                                | Always set to Wifi0.                                             |
| 3. Status               | Enabled/Disabled                                     | Enables or disables the access point.                            |
| 4. Network Name         | Hera200AccessPoint                                   | Wireless network name shown to nearby devices.                   |
| 5. SSID Visibility      | Broadcast/Hidden                                     | Hidden SSIDs must be entered manually by clients.                |
| 6. Security             | None/WEP Open System/WEP Shared Key/WPA-PSK/WPA-PSK2 | Wireless encryption level, from least to most secure.            |
| 7. Pass phrase          | Unique Password                                      | Password required to join the SSID.                              |
| 8. MAC Filter           | No filtering/Allow/Deny                              | Allows all clients, creates an allowlist, or creates a denylist. |
| 9. Filtered MAC address | One or more MAC addresses                            | Specifies one or more MAC addresses.                             |

For Wireless Client configuration, contact Eseye Support or Device Management.
