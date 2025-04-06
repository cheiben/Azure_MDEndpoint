# MDE Device Management Laboratory

## Overview
This laboratory provides hands-on experience with Microsoft Defender for Endpoint (MDE) device management features. You will learn how to onboard a virtual machine to MDE, perform device isolation, and collect investigation packages.

## Prerequisites
- Microsoft Azure account with permissions to create virtual machines
- Access to Microsoft Defender for Endpoint portal
- Basic understanding of Windows operating systems

## Lab Components

### Part 1: Onboarding VM to Microsoft Defender for Endpoint

#### Objectives
- Create a Windows virtual machine
- Onboard the VM to Microsoft Defender for Endpoint

#### Steps
1. Create a Windows Virtual Machine in Azure
2. Log into the MDE Portal: https://security.microsoft.com/
3. Browse to the **Onboarding Page**:
   - Navigate to Settings → Endpoints → Device Management → Onboarding
   - Note: Since you aren't an admin, the onboarding packages have been pre-staged for you:
     - [Windows 10/11 MDE Package](https://sacyberrange00.blob.core.windows.net/mde-agents/Windows-10-and-11-GatewayWindowsDefenderATPOnboardingPackage.zip)
     - [Windows Server 2019/2022 Package](https://sacyberrange00.blob.core.windows.net/mde-agents/Windows-Server-2019-and-2022-GatewayWindowsDefenderATPOnboardingPackage.zip)
     - [Linux (Ubuntu) Server (Python) Package](https://sacyberrange00.blob.core.windows.net/mde-agents/Linux-Server-GatewayWindowsDefenderATPOnboardingPackage.zip)
4. Log into your virtual machine and download the appropriate MDE package
   - Right-click the package and select "Run as Administrator"
5. Verify successful onboarding:
   - Return to the MDE Portal
   - Navigate to Assets → Devices
   - Confirm your device appears in the list

**Note:** Keep this VM for subsequent labs. You may power it off rather than delete it to avoid repeating the onboarding process.

### Part 2: Device Isolation

#### Objectives
- Learn how to isolate a device from the network
- Observe the effects of device isolation

#### Steps
1. Login to your virtual machine
2. Turn off Windows Firewall:
   - Run `wf.msc` and disable the firewall
3. Configure your VM's Network Security Group (NSG):
   - Allow ALL traffic inbound (or at minimum allow ICMP)
4. Start a perpetual ping to your device's public IP address
   - This will be used to verify isolation effects
5. In the MDE Portal (https://security.microsoft.com/):
   - Navigate to Assets → Devices
   - Search for and select your device
6. Initiate device isolation:
   - Click the three dots (⋮) in the upper right
   - Select "Isolate device"
7. Observe the ping requests stop responding
   - This confirms the device is isolated from the network
   - Only security-related traffic is now permitted
8. When testing is complete, release the device from isolation
   - Note: This feature can be integrated into Automated Detection responses

### Part 3: Creating an Investigation Package

#### Objectives
- Learn how to collect forensic data from a device
- Examine the contents of an investigation package

#### Steps
1. In the MDE Portal (https://security.microsoft.com/):
   - Navigate to Assets → Devices
   - Search for and select your device
2. Collect an investigation package:
   - Click the three dots (⋮) in the upper right
   - Select "Collect Investigation Package"
   - Enter a comment (visible to other users) and confirm
3. Monitor collection progress:
   - Click the three dots (⋮) in the upper right
   - Select "Action Center"
   - The status of your investigation package will be displayed
4. When collection is complete:
   - Refresh the Action Center until the status shows completed
   - Download the investigation package
5. Examine the contents:
   - Unzip the investigation package
   - Review the forensic data collected from the device

## Conclusion
After completing this laboratory, you should be familiar with basic MDE device management operations including onboarding, isolation, and forensic data collection.
