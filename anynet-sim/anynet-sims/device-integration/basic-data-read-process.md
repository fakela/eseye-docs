# Basic data read process

Repeat the basic read data process for each file that Eseye delivers to the AnyNet Secure SIM. For more information, see [Available files and sizes](https://eseye-v3.gitbook.io/eseye-docs/L25WdLp1CEZBZ0aOlPAR/anynet-sims/device-integration/about-anynet-secure-sim-files#available-files-and-sizes).

Use the following process actions:

```
Read file header using the block read function

If ((HeaderLength != 0) and (HeaderLength != 0xFFFF) and (HeaderChecksum != 0) and (HeaderChecksum != 0xFFFFFFFF)) then

{

// FILE ready to read

Read file data in chunks() // using calls to block read function()

Verify checksum ()

File Format Conversion () // convert DER to PEM as required

}

else

{

// FILE not found – random back-off and try again

}
```

## Read block function

We recommend that you implement a single function to request a block read of file data from the AnyNet Secure SIM.

For a description of the parameters, see AT+CRSM – reading files from the SIM.

Use AT+CRSM to achieve a block read, with the following format:

```
AT+CRSM=,,(/256),( MOD 256),\
,,
```

where data is unused and therefore empty.

This command returns:

```
+CRSM: 144,0,""
```

where "" is an ASCII hex string that you must return to binary form.

#### Example

To read the Thing Name file header into a buffer called returned\_data, call the read block function as follows:

```
output\_data (byte pointer) = returned\_data
```

* Thing Name fileid: 28640
* Offset: 0
* readlength: 6 bytes

```
AT+CRSM=176,28640,0,0,6,,"3F007FEE"

+CRSM: 144,0,"4D4150"
```

where "4D4150" is the string for "MAP".

The first character in the data is the upper nibble of the first data byte. The second character is the lower nibble of the first data byte. You must convert each nibble into its hexadecimal data byte value.

### Converting the returned data into binary

You must convert the "RETURNEDDATA" ASCII hexadecimal string into binary.

#### Example

The following example processes the returned string, reading two ASCII characters and converting them to binary. The resultant byte value is stored at the location defined by output\_data:

```
index = 0;

while (index < )

{

sscanf( \&data\[index], “%02X”, \*output\_data++);

index = index + 2

}
```

## Reading the file header

The following example uses the read block function to read the Thing Name header, returning 6 bytes from offset 0. 6 bytes is the header size.

Call the read block function with the following parameters:

```
output\_data = returned\_data
```

* Thing Name fileid: 28640
* offset: 0
* readlength: 6 bytes

If you use the suggested read block functionality, then the returned data is in binary format, not the ASCII hex returned by the modem.

After the response data is received, you can extract the file header length (2 bytes) and checksum (4 bytes). For more information, see File format.

Both values are big-endian. You may need to reverse the byte order.

```
datalength = \*(unsigned short \*)\&returned\_data\[0] // read 16 bit length

checksum = \*(unsigned int \*)\&returned\_data\[2] // read 32 bit checksum
```

If datalength is not equal to 0 and 0xFFFF, and the checksum is not equal to 0 and 0xFFFFFFFF, you can read the rest of the file.

## Reading the file in chunks

After reading the file header, you can read the data content, starting at offset 6. Read up to 255 bytes at a time.

Check the modem command manual, as shorter length limits per read may apply.

### Example

The following example reads the Root CA file, of length 1239 bytes.

```
file\_data = malloc(1240); // allocate storage for the file read assembly

offset=6; // skip the header bytes

while (length)

{

if (length > 255)

bytes\_to\_read = 255;

else

bytes\_to\_read = length;

// Wait for the read block response and process the data nibbles

read\_block\_function(\&file\_data\[offset – 6], 28640, offset, bytes\_to\_read)

length = length – bytes\_to\_read

offset = offset + bytes\_to\_read

// repeat if more data to read

}
```

For a file with a data record of 927 bytes, this code results in the following call sequence:

```
read\_lock\_function(\&file\_data\[0], 28641, 6, 255)

read\_lock\_function(\&file\_data\[255], 28641, 261, 255)

read\_lock\_function(\&file\_data\[510], 28641, 516, 255)

read\_lock\_function(\&file\_data\[765], 28641, 771, 255)

read\_lock\_function(\&file\_data\[1020], 28641, 1026, 219)
```

which in turn will issue the following AT commands:

```
AT+CRSM=176,28641,0,6,255,,”3F007FEE”

AT+CRSM=176,28641,1,5,255,,”3F007FEE”

AT+CRSM=176,28641,2,4,255,,”3F007FEE”

AT+CRSM=176,28641,3,3,255,,”3F007FEE”

AT+CRSM=176,28641,4,2,219,,”3F007FEE”
```

## File verification

After all the data bytes are read from the AnyNet Secure SIM, you must verify them. Perform a CRC32 calculation for the data and compare it to the checksum in the header. If the sum matches, the file read is complete. Otherwise randomly backoff to wait until the file update completes, and then try again.

For more information, see CRC-32 code example.

## File format conversion

The following files are transferred in Binary DER-encoded / ASN.1 BER-encoded format:

* Root CA fileid: 28641
* Public signed certificate fileid: 28642
* Private key fileid: 28643

You may need to convert these into PEM or base64 format for use with the SSL/TLS client. Use base64 to encode the data and add header and footer lines.

#### Example

For the Public signed certificate file:

```
certificate = sprint( "-----BEGIN CERTIFICATE-----\n")

offset = strlen( certificate);

cert\_offset = 0;

while (cert\_offset < cert\_length )

{

Length = (cert\_length – cert\_offset);

If (length > 64) length = 64;

base64encode(encoded, certificate\[cert\_offset], length);

cert\_offset += length;

Memcpy( certificate\[offset], encoded, length);

Offset += length;

certificate\[offset++] = '\n';

}

Memcpy( certificate\[offset], "-----END CERTIFICATE-----\n" )
```
