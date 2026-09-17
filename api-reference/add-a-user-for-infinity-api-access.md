# Add a user for Infinity API access

Before you can call the Eseye Infinity APIs, they need a **service account**. A service account holds machine credentials, a Client ID and a Client Secret, that your application uses to authenticate against the API. It sits separately from the portal logins your team uses to sign in.

### Prerequisite

Your portal account must have permission to manage user accounts. If **User Accounts** does not appear under **Portfolio**, contact your administrator.

### Create the service account

1. Sign in to the [Infinity portal.](https://infinity.anynetiot.com/)
2. Select **Portfolio** > **User Accounts**.

<figure><img src=".gitbook/assets/Screenshot 2026-09-04 at 01.43.15.png" alt=""><figcaption></figcaption></figure>



1. Select the **Service Accounts** tab.
2. Select **Actions**, and then select the option to create a service account.

<figure><img src=".gitbook/assets/Screenshot 2026-09-04 at 01.47.43.png" alt=""><figcaption></figcaption></figure>



1. Complete the following fields:

<figure><img src=".gitbook/assets/Screenshot 2026-09-04 at 01.48.07.png" alt=""><figcaption></figcaption></figure>



| Field                | Description                                                                                  |
| -------------------- | -------------------------------------------------------------------------------------------- |
| **Email Address**    | Enter the email address associated with the account.                                         |
| **First name**       | Enter the account holder’s first name.                                                       |
| **Last name**        | Enter the account holder’s last name.                                                        |
| **Access Roles**     | Select at least one service account role. Assign only the roles required by the application. |
| **Customer Suspend** | Leave this option clear to create an active account.                                         |

1. Select **Save**.

### Copy the client credentials

After you save the account, Infinity displays the following credentials:

* **Account**: The client ID.
* **Service Account Secret**: The client secret.

{% hint style="warning" %}
**Important:** Copy and securely store the client secret before you close the window. Infinity displays the secret only once.
{% endhint %}

After saving the credentials, select **Close**. The service account appears in the list with an **active** status.

### Replace a lost client secret

You cannot view or recover a client secret after closing the confirmation window. If you lose it:

1. Delete the existing service account.
2. Create a new service account.
3. Update the application with the new client ID and client secret.

Confirm that the credentials are no longer in use before deleting a service account.
