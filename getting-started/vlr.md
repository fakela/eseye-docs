---
description: >-
  The Visitor Location Register (VLR) forms a vital part in mobile telecommunications networks. It serves as a temporary database that stores subscriber inform...
---
# About the Visitor Location Register (VLR)

The Visitor Location Register (VLR) forms a vital part in mobile telecommunications networks. It serves as a temporary database that stores subscriber information when they roam into a different network area, outside their home network. The VLR plays a crucial role in enabling seamless communication and providing localized services for roaming subscribers.

The VLR also interacts with various network elements and systems through standardized interfaces, such as the [Home Location Register (HLR)](hlr.md), Mobile Switching Center (MSC), Authentication Center (AuC), and Short Message Service Center (SMSC). These interfaces facilitate communication and data exchange to enable seamless network operation for roaming subscribers.

Each mobile network operator has its own VLR.

The VLR holds data such as a SIM's International Mobile Subscriber Identity (IMSI), Mobile Subscriber ISDN Number (MSISDN), authentication keys, and service profiles. The VLR enables the network to securely and reliably identify roaming subscribers to the network, authenticate them, and provide appropriate services based on their subscription and location.

## VLR operations

- Subscriber registration and temporary data storage – When a network subscriber roams onto a visited network, the VLR receives the necessary temporary subscriber information from the HLR. The VLR registers the subscriber's presence in the visited network and stores the relevant subscriber data in its database for efficient call routing and service provisioning.
- Authentication and security – The VLR communicates with the HLR to authenticate the roaming device's identity and obtain the necessary security information. This ensures that the device is authorized to access services in the visited network securely.
- Roaming and HLR interaction – When subscribers roam into another network, the VLR interacts with the home network's HLR to ensure seamless service continuity. The HLR provides the necessary subscriber information to the VLR, enabling efficient routing of data packets and service provisioning in the visited network.
