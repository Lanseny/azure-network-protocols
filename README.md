<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>
<p>
  ##PART1
<h2>Actions and Observations</h2>
<h2>Part 1: Configuring Network Security Groups (NSGs) in Azure</h2>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<h2>Step 1: Create a Network Security Group</h2>

1. **Log in to the Azure Portal:**
   - Navigate to [Azure Portal](https://portal.azure.com) and log in with your credentials.

2. **Navigate to NSGs:**
   - In the left-hand menu, select **All services** > **Networking** > **Network security groups**.

3. **Create a New NSG:**
   - Click on **+ Add**.
   - Fill in the required details:
     - **Name**: Enter a name for the NSG.
     - **Subscription**: Select your Azure subscription.
     - **Resource group**: Select an existing resource group or create a new one.
     - **Location**: Choose the location closest to your resources.

4. **Create the NSG:**
   - Click **Review + create** and then **Create** to deploy the NSG.
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<h2>Step 2: Configure Inbound and Outbound Security Rules</h2>

1. **Select the NSG:**
   - Once the NSG is created, navigate to it by selecting **Resource groups**, then the specific resource group, and finally the NSG you just created.

2. **Add Inbound Security Rule:**
   - Click on **Inbound security rules** > **+ Add**.
   - Configure the inbound rule:
     - **Source**: Any or specify an IP range.
     - **Source port ranges**: * (all ports) or specify a range.
     - **Destination**: Any or specify a destination IP.
     - **Destination port ranges**: Specify the port range (e.g., 80 for HTTP).
     - **Protocol**: TCP, UDP, or Any.
     - **Action**: Allow or Deny.
     - **Priority**: Set a priority number (lower numbers have higher priority).
     - **Name**: Enter a name for the rule.
   - Click **Add** to create the rule.

3. **Add Outbound Security Rule:**
   - Click on **Outbound security rules** > **+ Add**.
   - Configure the outbound rule with similar settings to the inbound rule.
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<h2>Step 3: Associate NSG with Subnet or Network Interface</h2>

1. **Associate with a Subnet:**
   - Go to the **Settings** section of the NSG.
   - Click **Subnets** > **+ Associate**.
   - Select the virtual network and subnet you want to associate with the NSG.

2. **Associate with a Network Interface:**
   - Go to **Settings** > **Network interfaces** > **+ Associate**.
   - Select the network interface you want to associate with the NSG.

<h2>Part 2: Inspecting Network Protocols</h2>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<h2>Step 1: Install Network Monitoring Tools</h2>

1. **Wireshark:**
   - Download and install [Wireshark](https://www.wireshark.org/), a popular network protocol analyzer.
   - Launch Wireshark and select the network interface to start capturing packets.

2. **Azure Network Watcher:**
   - In the Azure Portal, navigate to **All services** > **Networking** > **Network Watcher**.
   - Enable Network Watcher for your region if it's not already enabled.
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<h2> Step 2: Capture Network Traffic</h2>

1. **Capture Traffic with Wireshark:**
   - Start a capture session in Wireshark by selecting the desired network interface.
   - Analyze the captured packets to inspect the network protocols in use (e.g., TCP, UDP, HTTP).

2. **Capture Traffic with Azure Network Watcher:**
   - Navigate to **Network Watcher** > **Packet capture**.
   - Click **+ Add** to create a new packet capture.
   - Fill in the required details:
     - **Target virtual machine**: Select the VM you want to capture traffic from.
     - **Name**: Enter a name for the packet capture session.
     - **Storage account**: Select a storage account to save the capture file.
     - **Time limit**: Set the duration for the capture.
     - **Filters**: Specify any filters (e.g., IP addresses, ports).
   - Click **OK** to start the capture.
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<h2>Step 3: Analyze Captured Data</h2>

1. **Analyze with Wireshark:**
   - Use Wireshark's interface to filter and analyze the captured data.
   - Apply filters (e.g., `http`, `tcp.port == 80`) to focus on specific protocols or traffic types.
   - Examine packet details to understand the communication patterns and identify any issues.

2. **Analyze with Azure Network Watcher:**
   - After the capture session completes, download the capture file from the specified storage account.
   - Open the capture file in Wireshark or another packet analysis tool.
   - Analyze the traffic to identify anomalies, performance issues, or security concerns.

<h2>Conclusion<h2>

By following these steps, you have configured Network Security Groups (NSGs) in Azure to control inbound and outbound traffic to your resources. Additionally, you have used network monitoring tools like Wireshark and Azure Network Watcher to capture and analyze network protocols. This comprehensive guide demonstrates your ability to secure and monitor network traffic in a cloud environment, showcasing your expertise in network security management.



