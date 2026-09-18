# AnyNet SMARTconnect™ AT Commands

AT commands (Hayes command set) are instructions for controlling modules. The commands consist of a series of short text strings for a range of uses, including:

* Configuring a module
* Establishing the module's network connection
* Discovering module and connection status information, to ensure they are working correctly
* Managing the module
* Encrypting and transporting data to and from the module
* Directly accessing the cloud

Your software must send test, read and write AT commands to your module.

{% hint style="info" %}
Search the module supplier documentation for a full set of the AT commands you can use on your module. This link may not point to the latest version.
{% endhint %}

AnyNet SMARTconnect™ AT commands extend the available AT commands on your AnyNet SMARTconnect™-enabled module.

### Before you begin

Before you use any AT commands on the module, ensure that it is ready to receive them.

To test that the module is ready to receive AT commands:

*   Using a terminal emulator connected to your module, enter:

    ```
    at
    ```

    The terminal emulator will return any of the following:

    * `OK` – The module and port are connected and ready to communicate.
    * `ERROR` – The module and port cannot communicate. Contact the modem supplier.
    * Nothing – ensure you have set the correct baud rate in your code. For more information, see Connecting to the Quectel module using a terminal emulator.

If you are using AnyNet SMARTconnect™, ensure that it is correctly installed on the modem. For more information, see Installing AnyNet SMARTconnect™ on a Quectel BGxx module.

To test that AnyNet SMARTconnect™ is ready to receive AnyNet SMARTconnect™ AT commands:

*   Using a terminal emulator connected to your module, enter:

    ```
    at+etminfo=version
    ```

    The terminal emulator will return either of the following:

    *   AnyNet SMARTconnect™ V, where is the current software version – the module is ready to receive AnyNet SMARTconnect™ AT commands.

        Verify that the version number is AnyNet SMARTconnect™ V0.99\_ma or higher.
    * `ERROR` – AnyNet SMARTconnect™ software has not yet initialised. Try again in 5 seconds.

### AT command syntax

Use the following syntax:

`AT+<COMMAND><CR>`

Where:

* `AT` is uppercase or lowercase.
* `<COMMAND>` is a test, read, or write command in uppercase or lowercase.
*   `<CR>` is the end-of-line character. It is also called carriage return (`\r`).

    The modem executes the command after receiving `<CR>`.
* `<LF>` is the line feed character. It moves the cursor to the next line.

{% hint style="info" %}
This document displays commands only. `<CR><LF>` after a command is intentionally omitted.
{% endhint %}

AT commands are usually followed by a response:

`<CR><LF><RESPONSE><CR><LF>`

`<RESPONSE>` is the command response.

{% hint style="info" %}
This document displays responses only. `<CR><LF>` is intentionally omitted.
{% endhint %}

The response may include:

* `OK` – The command executed without errors.
* `ERROR` – The command is invalid, or the command line is too long.

## Types of AT Commands and responses

| Command type | Command syntax | Description                                                                                                                                                                                                        |
| ------------ | -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Test         | `AT+=?`        | Returns a list of parameters and value ranges set by the corresponding Write command or internal processes.                                                                                                        |
| Read         | `AT+?`         | Returns the currently set value of each parameter.                                                                                                                                                                 |
| Write        | `AT+=`         | Sets the user-defined parameter values.                                                                                                                                                                            |
| Execute      | `AT+`          | Reads non-variable parameters affected by internal processes in the Eseye-enabled modem. For example, see [CCID – request unique SIM number (ICCID)](general-at-commands/ccid-request-unique-sim-number-iccid.md). |
