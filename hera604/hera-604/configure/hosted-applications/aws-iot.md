# AWS IOT

Open **Hosted Applications > AWS IOT** to connect the Hera 604 to an AWS IoT deployment.

When the application is enabled, the router uses the configured endpoint and device identity files to establish the AWS IoT connection. Obtain the socket port, certificate formats, and file locations from the deployment configuration before enabling it.

<figure><img src="../../.gitbook/assets/Screenshot 2026-08-14 at 16.45.47.png" alt=""><figcaption></figcaption></figure>

**Application settings**

| Field                                | Value shown             | Description                                                                                                                                             |
| ------------------------------------ | ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Application                          | `Enabled` or `Disabled` | Starts or stops the AWS IoT application. Keep it disabled until the endpoint and identity files have been configured.                                   |
| Use WiFi LED for AWS IOT file status | `Yes` or `No`           | Uses the Wi-Fi LED to indicate the status of the files required by the AWS IoT application. This changes the LED's purpose while the option is enabled. |
| Socket port                          | Blank                   | Network port used to connect to the AWS IoT service. Enter the port specified in the deployment configuration.                                          |

**AWS IoT files**

| File name  | Type        | Available format             | From SIM      | Purpose                                                                         |
| ---------- | ----------- | ---------------------------- | ------------- | ------------------------------------------------------------------------------- |
| privatekey | Key         | `Base64 PEM` or `Binary DER` | `Yes` or `No` | Private key used to authenticate the Hera 604. Treat this file as confidential. |
| clientcert | Certificate | `Base64 PEM` or `Binary DER` | `Yes` or `No` | Client certificate that identifies the router to AWS IoT.                       |
| rootca     | Certificate | `Base64 PEM` or `Binary DER` | `Yes` or `No` | Root certificate authority used to verify the AWS IoT service certificate.      |
| url        | ---         | Not applicable               | `Yes` or `No` | AWS IoT endpoint assigned to the device or deployment.                          |
| thingname  | ---         | Not applicable               | `Yes` or `No` | AWS IoT Thing name assigned to the router.                                      |

**From SIM** determines whether the router obtains that value or file from the SIM. Set it to **No** only when the deployment is designed to use a file or value stored elsewhere on the router.

**Configure AWS IOT**

1. Leave **Application** set to **Disabled** while entering the settings.
2. Enter the **Socket port** supplied for the AWS IoT deployment.
3. For **privatekey**, **clientcert**, and **rootca**, select the format that matches the supplied files.
4. For each row, set **From SIM** according to where the deployment stores that item.
5. Set **Use WiFi LED for AWS IOT file status** to **Yes** only when the LED is required as a file-status indicator.
6. Confirm that the endpoint, Thing name, certificate, and private key belong to the same AWS IoT device identity.
7. Set **Application** to **Enabled**.
8. Select **Save**.

> **Security:** Do not copy private keys into tickets, emails, screenshots, or operator notes. If a private key is exposed, follow the deployment's credential-replacement procedure.
