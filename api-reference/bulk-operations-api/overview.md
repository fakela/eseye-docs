# Overview

Bulk Operations APIs run one action against many items, such as SIM cards. You can activate, suspend, terminate, and update items in bulk.

Use these APIs to manage large device or SIM fleets. Bulk operations use a CSV file to change many SIMs.

Common job types update status, packages, portfolios, and `customerSuspend`. You can also update attributes such as `friendlyName` and `orderId`. When the job completes, download its response file for each SIM result.

### When to use bulk operations

Use bulk operations to perform the same action on many items. For example:

* Activate multiple SIM cards.
* Suspend or terminate a batch of SIM cards.
* Update attributes or configurations for a group of items.
* Upload and process large datasets in one operation.

Before you start, obtain these values:

| Item          | Description                                                                                     |
| ------------- | ----------------------------------------------------------------------------------------------- |
| `base64`      | Base64 encoding of `clientId:clientSecret` for a service account with file and job permissions. |
| `fileUrl`     | Base URL of the File service.                                                                   |
| `jobUrl`      | Base URL of the Job service.                                                                    |
| `env`         | Your environment: `stage` or `prod`.                                                            |
| `portfolioId` | The portfolio that owns the files and jobs.                                                     |

{% hint style="info" %}
If you need these values, email [Sales Admin](mailto:orders@eseye.com?subject=Request%20Prerequisites%20for%20bulk%20operations.) with the subject **Request Prerequisites for bulk operations.**

Include these details in the email:

* Company name
* Your role
* Contact phone number
* Contact email address
{% endhint %}

### Workflow

Run the bulk workflow in this order:

1. **Get Token:** Mint an OAuth2 access token.
2. **Create File:** Create a file record and S3 path.
3. **Upload or Download File:** Use `action=upload` to retrieve presigned S3 upload credentials.
4. **Upload File to S3:** Select and send your local CSV file.
5. **Job Create:** Start the bulk job for the uploaded CSV.
6. **Job Update:** Set the status to `queued` to trigger orchestration.
7. **Get ResponseFile:** Poll until `responseFileId` is not null.
8. **Upload or Download File:** Use `action=download` to request a presigned results URL.
9. **Download via Pre-signed URL:** Retrieve the results file and save it locally.

### Choose a CSV template

Choose the template for your operation. Then select it during **Upload File to S3**.

| Operation                           | Template                                                                                                              |
| ----------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| Update ICC `customerSuspend`        | [Download the `customerSuspend` template](https://resources.anynetiot.com/template/update-icc-customerSuspend.CSV)    |
| Update ICC package                  | [Download the package template](https://resources.anynetiot.com/template/update-icc-package.CSV)                      |
| Update ICC portfolio                | [Download the portfolio template](https://resources.anynetiot.com/template/update-icc-portfolio.CSV)                  |
| Update ICC status                   | [Download the status template](https://resources.anynetiot.com/template/update-icc-status.CSV)                        |
| Update ICC attribute `friendlyName` | [Download the `friendlyName` template](https://resources.anynetiot.com/template/update-iccAttribute-friendlyName.CSV) |
| Update ICC attribute `orderId`      | [Download the `orderId` template](https://resources.anynetiot.com/template/update-iccAttribute-orderId.CSV)           |

For status updates, enter the status value in lowercase.
