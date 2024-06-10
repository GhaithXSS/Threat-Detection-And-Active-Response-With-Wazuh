# Threat-Detection-And-Active-Response-With-Wazuh
In the modern landscape of cybersecurity, the ability to swiftly detect and respond to threats is paramount. This project, "Threat Detection & Active Response with Wazuh," leverages the powerful open-source security platform Wazuh to create a robust threat detection and response system.

The setup involves an Ubuntu 22.04 server running Wazuh on VirtualBox, a Windows machine acting as the Wazuh agent, and a Kali Linux machine simulating an attacker executing various attack scenarios. This configuration provides a comprehensive environment to monitor, detect, and actively respond to security threats.

## Key Components:

1. Ubuntu 22.04 Server: Hosts the Wazuh server, responsible for monitoring and analyzing data from connected agents.
2. Windows Machine: Functions as the Wazuh agent, sending event data and alerts to the Wazuh server for analysis.
3. Kali Linux Machine: Used to simulate attacks, testing the effectiveness of the threat detection and response mechanisms.
## Project Objectives:

- Threat Detection: Implement real-time monitoring to identify potential security threats.
- Active Response: Configure automated responses to detected threats to mitigate risks.
- Security Analytics: Analyze collected data to gain insights into the security posture of the system.
- Comprehensive Documentation: Provide detailed setup instructions, attack scenarios, and analysis of detection and response effectiveness.

This project demonstrates how Wazuh can be used to enhance security monitoring and response capabilities, offering valuable insights and protection against cyber threats.

## Step 1: Installing Ubuntu 22.04 on VirtualBox

In this step, we set up the Ubuntu 22.04 server on VirtualBox, which will host the Wazuh server. Follow these instructions to install Ubuntu:

**1. Download Ubuntu 22.04 ISO:**

- Obtain the Ubuntu 22.04 ISO from the official Ubuntu website.

**2. Create a New Virtual Machine:**

- Open VirtualBox and click on "New" to create a new virtual machine.
- Name the VM (e.g., "Ubuntu 22.04 Server") and set the type to "Linux" and version to "Ubuntu (64-bit)".
- Allocate memory (RAM) according to your system's capability (at least 2 GB recommended).
- Create a new virtual hard disk and allocate sufficient storage space (at least 20 GB recommended).

**3. Configure the VM:**

- Go to the VM settings and under the "Storage" section, attach the Ubuntu 22.04 ISO to the optical drive.
- Adjust other settings as needed, such as network configuration to ensure the VM can connect to the internet.

**Install Ubuntu:**

- Start the VM and follow the on-screen instructions to install Ubuntu.
- Select your language, keyboard layout, and other preferences.
- Follow the prompts to complete the installation, creating a user account and setting up the system.

After the installation is complete, you will have an Ubuntu 22.04 server running on VirtualBox, ready to host the Wazuh server.

## Step 2: Installing Wazuh on Ubuntu 22.04

With Ubuntu 22.04 installed on VirtualBox, the next step is to set up Wazuh. Wazuh is a powerful open-source security platform that will enable us to monitor and respond to security threats. Follow these instructions to install Wazuh:

**1.Update and Install Dependencies:**

- Open a terminal on your Ubuntu server.
- Update the package list and install necessary dependencies with the following command:

```sudo apt update && sudo apt install curl apt-transport-https unzip wget libcap2-bin software-properties-common lsb-release gnupg2```

![image](https://github.com/GhaithXSS/Threat-Detection-And-Active-Response-With-Wazuh/assets/172057297/3dfcd2c8-2589-4561-aa43-22936d8687df)

**2.Download and Run the Wazuh Installation Script:**

- Download the Wazuh installation script, make it executable, and run it to install Wazuh components:

```curl -sO https://packages.wazuh.com/4.5/wazuh-install.sh && chmod 744 wazuh-install.sh && bash ./wazuh-install.sh -a```

![image](https://github.com/GhaithXSS/Threat-Detection-And-Active-Response-With-Wazuh/assets/172057297/88ae99d4-37ee-48b5-94b1-8ed6e178f3d9)

**3.Installation and Configuration:**

- The script will automatically install and configure the Wazuh server, the Wazuh API, and Filebeat.
- Once the installation is complete, the script will provide the Wazuh admin username and password. Make sure to save these credentials securely, as you will need them to access the Wazuh dashboard.

  ![image](https://github.com/GhaithXSS/Threat-Detection-And-Active-Response-With-Wazuh/assets/172057297/9b417835-0521-49c5-819a-1a63cfde04de)


After completing these steps, Wazuh will be installed and configured on your Ubuntu server. You can now proceed to set up the Wazuh agent on your Windows machine and configure the attack scenario using Kali Linux.
