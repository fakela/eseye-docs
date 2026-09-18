# Connecting the Quectel BGxx module to a LwM2M server

AnyNet SMARTconnect™ uses the essential AnyNet files to connect a Quectel BGxx module to a LwM2M bootstrap server. For more information, see Creating the essential AnyNet files.

AnyNet SMARTconnect™ then obtains the certificates and data required to connect to a LwM2M server from the LwM2M bootstrap server. There are two modes for the connection:

* Secure – CoAP messages are encrypted using a DTLS connection.
* Non-secure – CoAP messages are exchanged unencrypted via UDP.

## About LwM2M certificates

After the bootstrap procedure completes, for secure mode, AnyNet SMARTconnect™ saves these files in the `datatx` folder:

* `lwm2m_server_public_key` – the x509 server certificate
* `lwm2m_public_key` – the LwM2M public certificate
* `lwm2m_secret_key` – the LwM2M public private key
*   `lwm2m_url` – the LwM2M server URL, in this format:

    ```
    coap(s)://<server>
    ```

    `coaps` indicates secure mode. `coap` indicates non-secure mode.

    If `coaps` is used, but a LwM2M file is missing, non-secure mode is used.

    For non-secure mode, only `anynet_thingname_store` and `lwm2m_url` are required.

LwM2M files require the same six-byte header as the essential AnyNet files. For more information, see Creating the essential AnyNet files.
