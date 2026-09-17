# Updating the modem firmware using AWS IoT jobs – Quectel module

At any time the AWS IoT Core Device Management service may instruct the module to install an OTA update by publishing a job document to the jobs/next topic.

When the module receives a valid JSON job document, it retrieves the firmware package from the Amazon S3 instance using a pre-signed URL within the job document.

Throughout the update process, the module publishes status information to AWS IoT Core. After the update completes, a SUCCEEDED status is published, and the AWS IoT Core Device Management service marks the job as complete.

For information about jobs, see https://docs.aws.amazon.com/iot/latest/developerguide/iot-jobs.html.

### Before you begin

Obtain the firmware image file from Eseye. Contact Support for more information: support@eseye.com.

## Creating a JSON job description file

1.  Create a UTF-8 encoded JSON job description file for the firmware update.

    The job description must contain operation and location parameters that specify which update to apply, and where to find it.

    For more information, see Example job document.
2.  Upload the JSON job description file and firmware image file to the S3 bucket in the same root account as the IoT things.

    For more information, see https://docs.aws.amazon.com/AmazonS3/latest/user-guide/upload-objects.html

    The Job process does not permit cross-region operation. You must upload the S3 bucket in the same region as the things you are updating. If you are operating across multiple regions, upload the .zip file into an S3 bucket for each region.

### Example job document

Possible operations include:

| Operation        | Description                                                                                                                                                                                                                                                                       |
| ---------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| firmware\_update | Updates AnyNet SMARTconnect™ application on the module. The location parameter contains the image file URL. The image file must exist in Eseye bin.ota format. This operation can optionally include fota\_location to update the firmware and application in a single operation. |
| fota             | Updates the module firmware. The location parameter contains the image file URL.                                                                                                                                                                                                  |
| config\_update   | Updates the AnyNet SMARTconnect™ configuration file. The location parameter contains the new configuration file URL.                                                                                                                                                              |
| host\_firmware   | Downloads a software image for the host MCU. When the download completes, the host is not notified by URC. To see details of the downloaded image, send: `AT+HFWREAD=?`                                                                                                           |

For example:

```json
{
  "operation": "firmware_update",
  "location": "${aws:iot:s3-presigned-url:https://s3.amazonaws.com/BucketName/ImagefileName.ota}"
}
```

## Creating an AWS IoT custom job

The AWS IoT Console is regularly updated. The procedure below may differ from the Console version you are using. Refer to the AWS documentation for more information.

1. In the left-hand AWS IoT menu, select Manage > Jobs.
2.  On the Start a job for your devices page, select Create a job.

    The Select a job page appears.
3.  Select Create custom job.

    The Create a job page appears.
4. Type in a Job ID and optional Description.
5. Under Select devices to Update, click or tap Select to view a list of Thingsthat exist in the selected region.
6. Select one or more checkboxes alongside the things that require the firmware update.
7. Under Add a job file, select the JSON job description you created from the S3 bucket.
8. Under Pre-sign resource URLs select I want to pre-sign my URLs and have configured my job file.
9.  Select the pre-signing role from the drop down list.

    Alternatively, create a pre-signing role if required.
10. Under URL will expire at this time, select the URL expiry time from the drop-down list.
11. Leave all other settings as the default settings.
12. Select Next.
13. On the Advanced configurations page, leave all settings as the default settings.
14. Select Create to create the job and start the update process.

## Where to next?

* [AT commands](https://app.gitbook.com/s/TZG4LrCHVlGSXoDpMgo3/at-command-reference/at-commands)
* [MQTT AT commands](https://app.gitbook.com/s/TZG4LrCHVlGSXoDpMgo3/at-command-reference/mqtt-at-commands)
* [Management AT commands](https://app.gitbook.com/s/TZG4LrCHVlGSXoDpMgo3/at-command-reference/management-at-commands)
* [General AT commands](https://app.gitbook.com/s/TZG4LrCHVlGSXoDpMgo3/at-command-reference/general-at-commands)
* [Using the AnyNet SMARTconnect™ configuration file](https://app.gitbook.com/s/TZG4LrCHVlGSXoDpMgo3/getting-started/using-the-anynet-smartconnect-tm-configuration-file)
