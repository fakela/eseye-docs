# Suspend or unsuspend SIMs

Suspending a SIM disables all services on it (i.e. Data, SMS and Voice), although you will still be charged the agreed monthly tariff. A suspended SIM is still provisioned. To re-enable services (i.e. Data, SMS and Voice), the SIM should be unsuspended.

Unsuspending a SIM can only be achieved after at least two hours of suspension because the suspension process may take up to two hours to complete.

You can suspend SIMs using the:

* **Infinity Classic portal**, which enables you to:
* [Suspend or unsuspend individual SIMs](suspend-or-unsuspend-sims.md#suspending-individual-sims)
* [Bulk suspend SIMs](suspend-or-unsuspend-sims.md#suspending-sims-in-bulk) (via email)
* Configure alert profiles which can automatically suspend SIMs that exceed their usage limits until the next billing period.
* **Tigrillo API**, which provides [suspendSIMs](https://docs.eseye.com/Content/API/Tigrillo/suspendSIMs.htm) and [unsuspendSIMs](https://docs.eseye.com/Content/API/Tigrillo/unsuspendSIMs.htm) API commands to suspend/unsuspend SIMs.

## Suspending individual SIMs

You can suspend or unsuspend SIMs by changing the SIM state in Infinity Classic.

To suspend an individual SIM using Infinity Classic:

1. Go to: SIMS > SIMs List > Action ![](../.gitbook/assets/infinityclassic-0143-SIAMnetworksettings_ic_24x24.png).
2. Select Change State.
3. In the Requested State drop-down menu, select Suspend SIM.
4. Select Request. The suspension process takes up to two hours. When suspended, the SIM will continue to connect to the network, and service charges will continue.

To unsuspend an individual SIM using Infinity Classic:

You can only unsuspend a SIM after it has completed the suspension process (this takes up to two hours). When unsuspended, the SIM will authenticate on the network, and can use available services.

1. Go to: SIMS > SIMs List > Action ![](../.gitbook/assets/infinityclassic-0143-SIAMnetworksettings_ic_24x24.png)
2. Select Change State.
3. In the Requested State drop-down menu, select Reactivate SIM.
4. Select Request.

## Suspending SIMs in bulk

You can only bulk suspend SIMs via email.

To suspend multiple SIMs via email:

1. Use this [email](mailto:support@eseye.com?subject=Please%20suspend%20these%20SIMs\&Body=Hello%20Support,%0D%0DMy%20SIAM%20account%20username%20is:%0DPlease%20suspend%20the%20following%20ICCIDs%20\(no%20quotation%20marks\):%0D%0D%0D%0D%0DI%20understand%20that%20Service%20Charges%20will%20continue%20for%20these%20SIMs.%0DPlease%20reply%20to%20this%20email%20to%20notify%20me%20when%20the%20SIMs%20are%20suspended.%0D%0DKind%20regards,%0D%0D) link, or create your own email.
2. Add the following information:

* Infinity Classic account username.
* List of SIM ICCIDs you want to suspend (without quotation marks).
* I understand that Service Charges will continue for these SIMs.

3. Send the email to support@eseye.com.

## Next step

Next: Terminate SIMs
