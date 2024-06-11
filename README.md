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

## Step 3: Logging into Wazuh

With Wazuh installed on your Ubuntu server, you can now log into the Wazuh dashboard. Follow these instructions to access the dashboard:

**Open a Web Browser:**

- Open your preferred web browser on the machine where you installed Wazuh.
- Navigate to the Wazuh Dashboard:
- In the address bar, type either ```https://localhost``` or ```https://127.0.0.1``` and press Enter.

![image](https://github.com/GhaithXSS/Threat-Detection-And-Active-Response-With-Wazuh/assets/172057297/e6903dc9-f70c-4359-bf18-1ee91d05ace3)

**Handle the Security Warning:**

- You will likely encounter a security warning indicating that the connection is not private. This is because Wazuh uses a self-signed certificate.
- Click on "Advanced" and then "Proceed to localhost (unsafe)" or "Proceed to 127.0.0.1 (unsafe)".

![image](https://github.com/GhaithXSS/Threat-Detection-And-Active-Response-With-Wazuh/assets/172057297/51be1074-9b51-4f44-bd3c-0f7f2629e5e4)

**Log into Wazuh:**

- You will be directed to the Wazuh login page.
- Enter the admin username and password that were provided during the installation process.
- Click "Login" to access the Wazuh dashboard.

![image](https://github.com/GhaithXSS/Threat-Detection-And-Active-Response-With-Wazuh/assets/172057297/6243d1e3-9d09-47e6-8931-b07a368b6604)

- After logging in, you will have access to the Wazuh dashboard where you can configure agents, monitor security events, and manage your security policies.

![image](https://github.com/GhaithXSS/Threat-Detection-And-Active-Response-With-Wazuh/assets/172057297/1dc56b83-fd28-4aea-bb36-4ac150623f03)

## Step 4: Adding a Windows 10 Machine as a Wazuh Agent

Now, we will add a Windows 10 machine as an agent to our Wazuh server. Follow these steps:

**1. Check the IP Address of the Ubuntu Server:**

- Open a terminal on your Ubuntu server.
- Type the command ip a to find the IP address of your server. In this example, the IP address is 192.168.1.100.

![image](https://github.com/GhaithXSS/Threat-Detection-And-Active-Response-With-Wazuh/assets/172057297/30d6c0ec-a447-4175-a779-131077a9bf31)

**2. Navigate to the Agents Section:**

- Click on the arrow next to the Wazuh logo on the dashboard.
- Select "Agents" from the dropdown menu.

**3. Add a New Agent:**

- Click on "Add agent" and choose "Windows" as the operating system.
- Select "Version 7+".

![image](https://github.com/GhaithXSS/Threat-Detection-And-Active-Response-With-Wazuh/assets/172057297/4014297a-cced-42c5-acd0-9a518d4e604d)

- For the Wazuh server address, enter your server's IP address (192.168.1.100).
- Choose a name for the agent, such as windows10.
- The Wazuh dashboard will provide a command to install the Wazuh agent on the Windows machine.
- Copy this command.
  
![image](https://github.com/GhaithXSS/Threat-Detection-And-Active-Response-With-Wazuh/assets/172057297/2b0871e5-a3c3-4d80-af26-555e7d95e484)




**4. Install the Wazuh Agent on Windows 10:**

- Click on the Start menu, type "PowerShell", right-click on "Windows PowerShell", and select "Run as administrator".
- Paste the command copied from the Wazuh dashboard into PowerShell and press Enter to register the agent with the Wazuh server.

![Screenshot (6)](https://github.com/GhaithXSS/Threat-Detection-And-Active-Response-With-Wazuh/assets/172057297/e134792c-c8d3-457e-af70-65b60af0cc11)

**5. Verify Installation:**

- Once the command executes successfully, verify that the agent appears in the Wazuh dashboard under the "Agents" section.

![image](https://github.com/GhaithXSS/Threat-Detection-And-Active-Response-With-Wazuh/assets/172057297/f5a04ca2-2d6f-425e-9d77-08e58a2ee7b5)

After completing these steps, the Windows 10 machine will be connected to the Wazuh server and start sending data, allowing you to monitor it from the Wazuh dashboard.

## Step 5: Viewing Information About the Windows 10 Agent in Wazuh

With the Windows 10 agent successfully added, you can now navigate the Wazuh dashboard to view detailed information and various dashboards related to the agent. Follow these steps:

**View Agent Overview:**

- The agent overview page provides general information about the agent, including its status, IP address, operating system, and connection time.

![image](https://github.com/GhaithXSS/Threat-Detection-And-Active-Response-With-Wazuh/assets/172057297/14f669c9-114e-4bc1-b55b-697ae427adf5)


**Access Agent-Specific Dashboards:**

- Wazuh offers various dashboards to monitor different aspects of the agent's activity. Navigate to these sections to view detailed information:

**Security Events:**

- Go to "Security Events" to view logs and alerts generated by the agent.

![image](https://github.com/GhaithXSS/Threat-Detection-And-Active-Response-With-Wazuh/assets/172057297/727d9f71-0642-4fe5-9e58-7d35525bddc3)

**Vulnerability Detection:**

- Navigate to "Vulnerability Detection" to see if any vulnerabilities have been detected on the Windows 10 agent.

**Integrity Monitoring:**

- Check the "Integrity Monitoring" section to track changes in critical files and directories on the agent.

**Agent Log Data:**

- View detailed log data collected from the agent under the "Logs" section.

![image](https://github.com/GhaithXSS/Threat-Detection-And-Active-Response-With-Wazuh/assets/172057297/555af8a9-9f37-43ee-ae2b-8ce0faf40fef)

By exploring these categories and dashboards, you can gain comprehensive insights into the security posture of the Windows 10 agent and respond to any detected threats effectively.

## Step 6: Setting Up Threat Detection & Active Response

In this step, we will configure Wazuh to not only detect but also actively respond to threats. We will demonstrate this by triggering a failed SSH login attempt and configuring an active response to block repeated failed login attempts.

**1. Test Threat Detection**

**Simulate SSH Login Attempts:**

- Open Command Prompt on a different machine (e.g., your Windows machine or Kali Linux).
- Attempt to SSH into the Wazuh server multiple times using incorrect passwords:
- ```ssh ghaith@192.168.1.100```
- Keep guessing the password multiple times to generate failed login attempts.

![image](https://github.com/GhaithXSS/Threat-Detection-And-Active-Response-With-Wazuh/assets/172057297/78cc01a6-11a6-4bd8-b9ca-fee9bcf0e2d8)

**Check Security Events in Wazuh:**

- Go to the Wazuh dashboard.
- Click on "Security Events" to view the logs.
- Look for logs with the name "sshd authentication failed". These logs confirm that Wazuh is detecting the failed login attempts.

![image](https://github.com/GhaithXSS/Threat-Detection-And-Active-Response-With-Wazuh/assets/172057297/939e6dca-e627-4af3-82a3-267b1e3aefd7)

**Note the Rule ID:**

- Take note of the Rule ID that triggered the log. This Rule ID will be used to configure the active response.

![image](https://github.com/GhaithXSS/Threat-Detection-And-Active-Response-With-Wazuh/assets/172057297/3c7b103e-722d-4736-8901-7338c95ae1e0)

**2. Configure Active Response**

**Navigate to Management Configuration:**

- In the Wazuh dashboard, click on the arrow next to the Wazuh logo.
- Select "Management" and then "Configuration".

**Edit Configuration:**

- Click on "Edit Configuration".
- Navigate to the "Active Response" section.

**Add Active Response Configuration:**

Add the following configuration to the Active Response section. This configuration will block an IP address for 60 seconds after multiple failed SSH login attempts:
`<active-response>
  <disabled>no</disabled>
  <command>firewalld</command>
  <location>localhost</location>
  <rules_id>5710</rules_id> 
  <timeout>60</timeout>
</active-response>`

![image](https://github.com/GhaithXSS/Threat-Detection-And-Active-Response-With-Wazuh/assets/172057297/c212154d-871e-44e2-ad43-055fe69b0bf9)

**Save and Apply Configuration:**

- Save the changes and apply the new configuration.

**3. Test Active Response**

**Simulate SSH Login Attempts Again:**

- Attempt to SSH into the Wazuh server multiple times using incorrect passwords again.
- After several attempts, you should notice that your SSH access is blocked.

![image](https://github.com/GhaithXSS/Threat-Detection-And-Active-Response-With-Wazuh/assets/172057297/84c0364a-cd80-4761-991d-464588c0c2cc)

**Check Security Events for Active Response:**

- Go back to the Wazuh dashboard and check the "Security Events".
- Look for logs indicating "host blocked by firewall active response". These logs confirm that the active response is working and the offending IP has been blocked.

![image](https://github.com/GhaithXSS/Threat-Detection-And-Active-Response-With-Wazuh/assets/172057297/986b83d0-0643-4b26-9338-d61a3f5a1e2c)

**Investigate Further:**

- You can investigate the logs further to get full details of the active response action.

![image](https://github.com/GhaithXSS/Threat-Detection-And-Active-Response-With-Wazuh/assets/172057297/0c957631-c7a8-40ae-abd8-5204111c3c0b)
![image](https://github.com/GhaithXSS/Threat-Detection-And-Active-Response-With-Wazuh/assets/172057297/4fb4a913-b3b5-4e08-b327-f9eeff9da031)

By following these steps, you have successfully set up both threat detection and active response in Wazuh. Repeated failed SSH login attempts are detected, and the offending IP is automatically blocked, demonstrating an effective security measure.

# Conclusion

- This project demonstrates the implementation of a comprehensive cybersecurity solution using Wazuh, Ubuntu, Windows, and Kali Linux. By following these steps, we have successfully installed and configured Wazuh to monitor and protect a network environment. The key highlights of this project include:

- Setting Up the Environment: We began by installing Ubuntu on VirtualBox and configuring it as our Wazuh server. We also set up a Windows 10 machine as a Wazuh agent and used Kali Linux for attack simulations.
- Wazuh Installation and Configuration: We installed Wazuh on the Ubuntu server, configured it to detect threats, and added a Windows agent to the monitoring setup.
- Threat Detection: Through multiple SSH login attempts, we tested Wazuh’s ability to detect potential security threats and identified relevant security events.
- Active Response: By configuring active response in Wazuh, we demonstrated automatic blocking of IP addresses after repeated failed login attempts, effectively mitigating potential brute force attacks.
- The integration of Wazuh in a simulated environment has shown how powerful and versatile this open-source security platform can be. It provides real-time threat detection, alerting, and active response capabilities, making it an invaluable tool for cybersecurity professionals.

**As cyber threats continue to evolve, the importance of robust and responsive security measures cannot be overstated. This project serves as a foundational example of how to set up and utilize Wazuh for enhanced network security. We encourage further exploration and customization of Wazuh’s features to suit specific organizational needs and to stay ahead of emerging threats.**



