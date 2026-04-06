# Architecture Documentation

## Overview

This document provides a comprehensive overview of the SAL and Bluetooth profile architecture, detailing the components involved, their interactions, and the connection flows for HFP (Hands-Free Profile) and A2DP (Advanced Audio Distribution Profile).

## SAL (Service Abstraction Layer)
SAL serves as a mediator between the application and the Bluetooth stack. It abstracts the details of Bluetooth communication, allowing higher-level applications to interact with Bluetooth services seamlessly.

### Key Components:
1. **SAL Interface**: Provides methods for application interaction.
2. **Bluetooth Driver**: Interfaces directly with Bluetooth hardware.
3. **Profile Managers**: Manage specific Bluetooth profiles (HFP, A2DP).

## Bluetooth Profiles
Bluetooth profiles define the possible uses of a Bluetooth device. This document specifically outlines HFP and A2DP profiles.

### HFP (Hands-Free Profile)
**Connection Flow**:
1. **Device Discovery**: The hands-free device searches for paired devices.
2. **Connection Establishment**:
    - Initiation by the hands-free device.
    - Pairing process includes authentication and encryption steps.
    - Connection is established through RFCOMM (Radio Frequency Communication).
3. **Audio Stream Setup**: Audio routes are established for voice communication.

### Component Interactions for HFP:
- **Application Layer**: Initiates HFP connection requests.
- **SAL**: Communicates with Bluetooth stack to establish connections.
- **Audio Gateway**: Handles audio routing and processing.

### A2DP (Advanced Audio Distribution Profile)
**Connection Flow**:
1. **Device Discovery**: Similar to HFP, but focuses on audio devices.
2. **Connection Establishment**:
    - Prioritizes high-quality audio streaming.
3. **Streaming Setup**:
    - Defines audio codecs for transmission.
    - A2DP sink and source roles defined for devices.

### Component Interactions for A2DP:
- **Media Player**: Sends audio data to A2DP sink.
- **SAL**: Manages Bluetooth streaming protocols.
- **Bluetooth Controller**: Manages the real-time transmission of audio data.

## Detailed Examples
### HFP Example Connection Flow:
1. User activates the hands-free device.
2. Device scans for available Bluetooth devices.
3. User selects the target device.
4. The application requests a connection via SAL.
5. Authentication occurs, followed by RFCOMM connection establishment.
6. Voice audio path is established for call management.

### A2DP Example Connection Flow:
1. A user selects a music streaming device.
2. The device queries available Bluetooth audio sources.
3. The connection process follows similar steps as HFP but centers around audio data handling.
4. Upon connection, audio streams begin based on the chosen audio profile specifications.

## Conclusion
Understanding the architecture and interaction flows of HFP and A2DP is vital for developers aiming to integrate Bluetooth functionality within applications. The SAL acts as a crucial bridge, ensuring smooth communication between devices and efficient management of audio streams.