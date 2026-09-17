# Creating a thing with AnyNetThingType

When you create an AWS IoT thing that uses an AnyNet Secure SIM, select one of these types:

* `AnyNetThingType` for Eseye-designed implementations.
* `CompatibleAnyNetThingType` for bespoke implementations. This type indicates that Eseye must manage the thing.

### AnyNetThingType attributes

| Attribute      | Description                                                                                                                                                                                                                   | Mandatory? |
| -------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- |
| ActionRequest  | Allows actions to be performed when updating the thing                                                                                                                                                                        | ✗          |
| PolicySelector | The name of the policy that you want to attach to the thing. The policy must exist in the same AWS Region where you are creating the thing. Leave blank to use the Eseye-supplied default policy. For more information, see . | ✗          |
| SimID          | The SIM number of the Eseye SIM card associated with the device.                                                                                                                                                              | ✓          |

{% hint style="warning" %}
If you create custom things, `CompatibleAnyNetThingType` is mandatory. It must contain the `SimID` attribute and your bespoke attributes.
{% endhint %}

For information about thing properties, see the [AWS ThingAttribute API reference](http://docs.aws.amazon.com/iot/latest/apireference/API_ThingAttribute.html).
