# AT commands

AT commands (Hayes command set) are instructions for controlling modules. The commands consist of a series of short text strings for a range of uses, including:

* Configuring a module
* Establishing the module's network connection
* Discovering module and connection status information, to ensure they are working correctly
* Managing the module
* Encrypting and transporting data to and from the module
* Directly accessing the cloud

Your software must send test, read and write AT commands to your module.

Search the module supplier documentation for a full set of the AT commands you can use on your module. For example, Quectel supply the BG95\&BG77\&BG600L Series AT Commands Manual (PDF). (Note, this link may not point to the latest version).

AnyNet SMARTconnect™ AT commands extend the available AT commands on your AnyNet SMARTconnect™-enabled module.

### Before you begin

Before you use any AT commands on the module, ensure that it is ready to receive them.

To test that the module is ready to receive AT commands:

*   Using a terminal emulator connected to your module, enter:

    ```
    at
    ```

    The terminal emulator will return any of the following:

    * OK – the module and port are connected and ready to communicate
    * ERROR – the module and port cannot communicate. Contact the modem supplier.
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
    * ERROR – AnyNet SMARTconnect™ software has not yet initialised. Try again in 5 seconds.

## AT Command syntax

Use the following syntax:

```
AT+
```

where:

* AT is in upper or lowercase
* is a test, read or write command in upper or lower case
*   is the end-of-line character marking the end of a command line (alias \r – carriage return)

    The modem will execute the command line after receiving the end-of-line character.
* is the line feed, which will move the cursor to the next line

This document displays commands only. after a command is intentionally omitted.

AT commands are usually followed by a response that includes:

where is the command response

This document displays responses only. is intentionally omitted.

The response may include:

* OK – indicates the command executed with no errors
* ERROR – indicates an invalid command, or that the command line was too long

## Types of AT Commands and responses

| Command type | Command syntax | Description                                                                                                                                                                                                        |
| ------------ | -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Test         | `AT+=?`        | Returns a list of parameters and value ranges set by the corresponding Write command or internal processes.                                                                                                        |
| Read         | `AT+?`         | Returns the currently set value of each parameter.                                                                                                                                                                 |
| Write        | `AT+=`         | Sets the user-defined parameter values.                                                                                                                                                                            |
| Execute      | `AT+`          | Reads non-variable parameters affected by internal processes in the Eseye-enabled modem. For example, see [CCID – request unique SIM number (ICCID)](general-at-commands/ccid-request-unique-sim-number-iccid.md). |
