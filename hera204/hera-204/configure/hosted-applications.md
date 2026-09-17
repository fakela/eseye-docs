# Hosted Applications

The 'Hosted Applications' page is used to configure specialised applications present on the Hera 204 router.

## AWS IOT

The 'AWS IOT' page is used to configure aspects of the AWS IOT application. When the application is enabled, the router automatically configures itself by downloading the required certification files. You can choose to set the router's WiFi LED to indicate that all the certification files have been received.

![AWS IOT](https://733576849-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FY2LsJ6998Uo7AtYcmJWd%2Fuploads%2FRyDHFLkhHx345ocikn4R%2Fhosted_applications_screenshot.png?alt=media\&token=129c34c3-a17e-49d3-877e-239e10279b12)

| # | Field Name                           | Sample value | Explanation                                                                                                                 |
| - | ------------------------------------ | ------------ | --------------------------------------------------------------------------------------------------------------------------- |
| 1 | Application                          | Enabled      | Enable or disable the AWS IOT application                                                                                   |
| 2 | Use WiFi LED for AWS IOT file status | Yes/No       | If set to yes, the WiFi LED on the top of the Hera 204 unit will illuminate to indicate successful download of certificates |
| 3 | Socket Port                          | 443          | Determines which network port to connect to the AWS IoT Core with                                                           |
| 4 | File name                            | privatekey   | The relevant AWS file to be configured                                                                                      |
| 5 | Type                                 | Certificate  | The filetype of the file                                                                                                    |
| 6 | Format                               | Base64 PEM   | The file format used for the X.509 certificate                                                                              |
| 7 | From SIM                             | Yes/No       | Determines whether the file is downloaded to the Hera204 filesystem or to the Eseye AnyNet SIM card.                        |
