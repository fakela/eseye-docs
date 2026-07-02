---
description: >-
  The Home Location Register (HLR) forms a critical part of mobile telecommunications networks. It serves as a central database that stores and manages mobile ...
---
# About the Home Location Register (HLR)

The Home Location Register (HLR) forms a critical part of mobile telecommunications networks. It serves as a central database that stores and manages mobile network subscriber information, such as authentication data, service profiles, and subscriber location. This facilitates service provisioning and mobility management within the network.

The HLR also interacts with various network elements and systems through standardized interfaces, such as the Mobile Switching Center (MSC), [Visitor Location Register (VLR)](vlr.md), Authentication Center (AuC), and Short Message Service Center (SMSC). These interfaces facilitate communication and data exchange to enable seamless network operations.

Each mobile network operator has its own HLR.

The HLR holds data such as a SIM's International Mobile Subscriber Identity (IMSI), Mobile Subscriber ISDN Number (MSISDN), authentication keys, and service profiles. The HLR enables the network to securely and reliably identify subscribers to the network, authenticate them, and provide appropriate services based on their subscription and location.

## HLR operations

- Subscriber registration and information management – When a subscriber joins a network, their information is stored in the HLR through the registration process. This process involves associating the subscriber's SIM with the IMSI and MSISDN, and provisioning the appropriate service settings.
- Authentication and security – The HLR, in conjunction with the Authentication Center (AuC), handles authentication and security-related operations for IoT devices. It stores authentication keys, algorithms, and security parameters required to verify the identity of IoT devices and ensure secure communication within the network.
- Roaming and VLR interaction – When subscribers roam into another network, the HLR interacts with the visited network's VLR to ensure seamless service continuity. The HLR provides the necessary subscriber information to the VLR, enabling efficient routing of data packets and service provisioning in the visited network.
- Service provisioning – The HLR manages service profiles and configurations for IoT devices. It stores information about subscribed services, activation status, and service preferences for each IoT device. These services can include over-the-air updates, remote device management, data analytics, and more.
