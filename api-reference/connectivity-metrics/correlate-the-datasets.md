# Correlate the datasets

The three datasets (authentication, accounting and traffic flow) can be used together to provide a complete view of a device’s connectivity activity or separately to answer specific operational questions.

#### Correlation keys

You can typically correlate records using **IMSI and timestamp**. The IMSI identifies the SIM across all three datasets, while the timestamp aligns records within the same period of activity.

#### How the records connect

The three datasets describe consecutive stages of a device’s connectivity activity:

1. Review **authentication records** to confirm whether the device attached successfully and identify rejected attempts or repeated reconnects.
2. Review **accounting records** to determine whether a session was established, how long it remained active and how much data it transferred.
3. Review **traffic flow (NetFlow) records** to identify where the data went while the session was active.

For example, repeated authentication rejections, short accounting sessions and few traffic flow records may indicate an unstable connection. A successful attachment, a long session and heavy traffic to an unexpected destination may point to a different issue. Correlating the datasets makes these patterns easier to distinguish.

#### Example investigation

Consider a device reported as consuming more data than expected.

Accounting records confirm the amount of data consumed and show when the relevant sessions occurred. Authentication records for the same IMSI and time period show whether the device was reconnecting repeatedly, which may indicate instability rather than expected usage. Traffic flow records then identify the destinations that received the data, helping you distinguish expected application traffic from unexpected communication.

Together, the records provide a complete, time-aligned view of the device’s connectivity behaviour.
