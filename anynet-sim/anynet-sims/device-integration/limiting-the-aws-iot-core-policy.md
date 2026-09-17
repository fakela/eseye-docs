---
hidden: true
---

# Limiting the AWS IoT Core policy

AWS IoT Core policies allow you to control access to the AWS IoT Core data plane. The data plane consists of operations that allow you to connect to the AWS IoT Core message broker, send and receive MQTT messages, and get or update the device shadow.

By default, the AnyNet Secure provisioning service creates things with an open policy. This occurs because the provisioning has no knowledge of your application, or the publish and subscribe topics and processing you are using with your AWS account.

It is best practice to limit the policy to allow access to only the required resource and to limit that access to only authenticated devices.

We recommend that you edit or replace the installed default policy. Only Allow required actions or Deny actions that the thing never performs. Use a resource control for each action to restrict resource access.

For example, if the thing only publishes and never subscribes, remove the subscribe action from the Allow policy statement. Alternatively, specifically Deny the subscribe action. Use a resource control such as Resource, which restricts the connection to a thing using a thing name registered in the AWS IoT registry and authenticated against the ARN. For example:

\["arn:aws:iot:Region:123456789012:client/${iot:Connection.Thing.AWSthingName}"]

For more detailed examples of how to adjust policies to manage resource access, see: AWS IoT Core policies.
