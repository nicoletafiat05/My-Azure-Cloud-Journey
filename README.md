## Azure Cloud Fundamentals

This repository documents my technical journey through the Microsoft Azure ecosystem. Through a series of hands-on labs, I have gained practical experience in deploying, managing, and automating cloud resources—transitioning from IaaS to PaaS, Containers, and Serverless architectures.

## Lab 1: Azure Resource Management & Organization
**Technical Action:** I created a Resource Group named `IntroAzureRG` in the **France Central** region. Within this group, I deployed a Windows Server Virtual Machine (`myVM`). After the deployment, I inspected the Resource Group to see all automatically generated components.

**What I Learned:**
* **Resource Grouping:** I understood that a Resource Group is a logical container. Even though I only "created a VM", Azure automatically added several other resources like a **Network Interface**, **Disk**, and **Public IP address** to the same group.
* **Lifecycle Management:** I practiced the cleanup process. Deleting the `IntroAzureRG` group automatically removed all the resources inside it, which is a crucial skill for cost management in cloud computing.

**Real-World Context:**
It’s like organizing a project in a physical folder. If you move or delete the folder, everything related to that specific project stays together, ensuring you don't leave "forgotten" resources running and generating costs.

<img width="1470" height="956" alt="sarcina 3 -lab1" src="https://github.com/user-attachments/assets/34baefd5-fb87-4790-b82d-42a47b39a21c" />

## Lab 2: Deploying a Web Server on Azure VM (IaaS)

**Technical Action:** In this lab, I deployed a Windows Server 2019 Datacenter VM named `myVM`. I connected via Remote Desktop (RDP) and manually installed the **Internet Information Services (IIS)** web server role. To make the server accessible, I configured the Network Security Group (NSG) to allow inbound traffic on **Port 80 (HTTP)**.

**What I Learned:**
* **Service Configuration:** I learned how to install and manage server roles within a cloud-hosted Windows environment.
* **Network Security Groups (NSG):** I understood that by default, Azure blocks all web traffic. I had to create a specific security rule to open Port 80, which is a fundamental concept in cloud security.
* **Public Accessibility:** I practiced accessing the server using its **Public IP address** from my local browser.

**Real-World Context:**
This is exactly how a company starts hosting a simple website. You rent the "hardware" (VM) from Azure, install the "software" (IIS), and open the "gate" (Port 80) for customers to visit the site.

<img width="1470" height="956" alt="instalare rol de server web-lab2" src="https://github.com/user-attachments/assets/f8888ae4-dc39-47af-8e57-5cc679673356" />
<img width="1470" height="956" alt="server web accesibil prin IP public-lab2" src="https://github.com/user-attachments/assets/20c7b656-944a-4648-ab82-e8d6b1747a4d" />

## Lab 3: Hosting a Web App with Docker Containers (PaaS)

**Technical Action:** I deployed an **Azure App Service** that runs a Docker container. Instead of setting up a full Virtual Machine, I used a pre-configured Docker image (`mcr.microsoft.com/azuredocs/aci-helloworld`) containing a simple "Welcome" web page.

**What I Learned:**
* **PaaS vs. IaaS:** I realized how much faster it is to deploy an app using App Service compared to a VM. Azure handles the underlying infrastructure, allowing me to focus solely on the application code/container.
* **Web App Metrics:** I explored the App Service dashboard and observed how Azure monitors traffic, showing real-time graphs for requests and response times.
* **Container Portability:** I learned that by using Docker, the application is packaged with all its dependencies, ensuring it runs exactly the same way in the cloud as it does locally.

**Real-World Context:**
This is the standard way modern startups launch apps. If you have a website ready in a Docker container, you can have it live and scaling in Azure in under 5 minutes, without ever seeing a Windows or Linux desktop.

<img width="1470" height="956" alt="incercare lab3" src="https://github.com/user-attachments/assets/f5ab7595-eadf-4c14-a9f4-eb49b4564b9f" />

## Lab 4: Deploying Instances with Azure Container Instances (ACI)

**Technical Action:** I deployed a localized Docker container using **Azure Container Instances**. I used the `mcr.microsoft.com/azuredocs/aci-helloworld` image, configured the OS type to **Linux**, and set up a **Fully Qualified Domain Name (FQDN)** so the application could be accessed via a custom web address instead of just an IP.

**What I Learned:**
* **Serverless Containers:** ACI is a "serverless" container solution. I learned that I don't need to manage any virtual machines or app plans; I just provide the container image, and Azure runs it instantly.
* **DNS & FQDN:** I practiced configuring a DNS name label, making the service more professional and easier to access for users.
* **Speed of Deployment:** I observed that ACI is one of the fastest ways to start a workload in the cloud, with the deployment finishing in seconds.

**Real-World Context:**
Think of ACI like a "one-off" rental car. You don't want to buy the car (VM) or sign a long-term lease (App Service); you just need to get from point A to point B right now. It's perfect for simple tasks, automated tests, or small web pages that don't need a complex setup.

<img width="1470" height="956" alt="lab4-verificare implementare" src="https://github.com/user-attachments/assets/b350f4a0-7f25-4732-bcd3-ccbac19ef983" />
<img width="1470" height="956" alt="lab4 finalizare" src="https://github.com/user-attachments/assets/aee1d71b-48ad-45f3-a014-1b0d85663dfe" />

## Lab 5: Virtual Networking & Internal Connectivity

**Technical Action:** I designed and deployed a **Virtual Network (VNet)** named `rețea virtuala1`. Inside this network, I created two Windows Server Virtual Machines (`vm1` and `vm2`). To test the internal communication, I accessed the VMs via RDP, temporarily disabled the Windows Firewalls, and performed a **Ping test** from `vm1` to `vm2` using PowerShell.

**What I Learned:**
* **VNet Fundamentals:** I learned that a Virtual Network acts as a private boundary in the cloud, allowing resources to communicate securely with each other using Private IP addresses.
* **Internal Firewall Management:** I discovered that even if Azure allows traffic at the network level, the OS-level firewall (Windows Firewall) can block ICMP (Ping) packets by default.
* **Connectivity Verification:** Successfully executing the `ping vm2` command from `vm1` confirmed that my virtual topology was correctly configured and that the VMs could "see" each other.

**Real-World Context:**
This lab simulates a corporate environment where a Web Server needs to talk to a Database Server. You wouldn't want this communication to happen over the public internet. Instead, you put them in the same VNet so they can exchange data privately, securely, and with very low latency.

<img width="1470" height="956" alt="lab5-sarcina 3" src="https://github.com/user-attachments/assets/84a34cb2-2eaa-4cf1-9b05-3358bdbba0c6" />

## Lab 6: Azure Blob Storage & Data Monitoring

**Technical Action:** I created a **Storage Account** with Locally-Redundant Storage (LRS) to optimize costs. I practiced creating a **Blob Container** and uploading files (blobs) to the cloud. Additionally, I explored **Azure Storage Insights** to analyze performance metrics, such as end-to-end latency and success rates.

**What I Learned:**
* **Storage Types:** I understood the purpose of a Storage Account as a central hub for Blobs, Files, Queues, and Tables.
* **Redundancy Options:** I learned about LRS (Locally-Redundant Storage) and how it provides data durability by replicating data within a single data center.
* **Cloud Monitoring:** By using the **Insights** blade, I learned how to track the health of my storage, monitoring availability (100% success rate) and average response times.

**Real-World Context:**
This is the "Google Drive" for developers. Companies use Blob Storage to store millions of user profile pictures, video files, or database backups in a way that is incredibly cheap, secure, and accessible from anywhere in the world.

<img width="1470" height="956" alt="lab6" src="https://github.com/user-attachments/assets/eeea3fa4-93b1-4c6a-8dae-f62db30d5ccc" />

## Lab 7: Cloud Databases - Azure SQL Database

**Technical Action:** I deployed an **Azure SQL Database** (PaaS) and configured a logical SQL server. To ensure security, I managed the **Server-level firewall settings** by adding my client IP address to allow a connection. I then used the built-in **Query Editor** to create a table and insert sample data using SQL commands.

**What I Learned:**
* **PaaS Database Benefits:** I understood that Azure handles patching, backups, and scaling, allowing me to focus only on the data and queries.
* **Cloud Security (Firewalls):** I learned that cloud databases are "secure by default" and won't allow any connection unless a specific firewall rule is created for the source IP.
* **SQL in the Portal:** I practiced running SQL queries directly from the Azure browser interface without needing local software like SSMS.

**Real-World Context:**
This is the heart of almost every app (like an online shop or a banking app). Instead of maintaining a physical server with SQL Server installed, you use Azure SQL to store user accounts, orders, and products safely and with 99.99% availability.

<img width="1470" height="956" alt="lab 7-testarea bazei de date" src="https://github.com/user-attachments/assets/7a2f0d3f-eccc-45aa-bb94-d27c37a346b8" />

## Lab 8: IoT Connectivity with Azure IoT Hub

**Tehnical Action:** I deployed an **Azure IoT Hub** and connected a simulated **Raspberry Pi** device to it. I used an online simulator real-time sensor data (temperature and humidity) to the cloud. I then monitored the message telemetry and device connectivity directly from the IoT Hub dashboard in the Azure Portal.

**What I Learned:**
* **IoT Telemetry:** I understood how physical devices (or simulators) send data packets to the cloud for processing.
* **Device Identity:** I learned how to authenticate a specific device to a Hub using connection strings.
* **Real-time Monitoring:** I practiced analyzing "Device-to-Cloud" messages and observed how metrics change in the portal as the device sends data.

**Real-World Context:**
This is the foundation of "Smart" everything—from smart factories to home automation. Imagine thousands of sensors in a warehouse sending temperature data to Azure; IoT Hub is the "gateway" that collects all that data securely so you can take action if a room gets too hot.


<img width="1470" height="956" alt="lab 8-sarcina 3" src="https://github.com/user-attachments/assets/600fedfb-5655-41f6-a81b-d18e4ac25e2e" />

## Lab 9: Infrastructure Automation with ARM Templates

**Technical Action:** In the final lab, I shifted from manual resource creation to **Infrastructure as Code (IaC)**. I used an **Azure QuickStart Template** to deploy a Windows Virtual Machine automatically. I explored the GitHub library of ARM (Azure Resource Manager) templates and deployed a standardized environment directly through the Azure Portal.

**What I Learned:**
* **Automation (IaC):** I understood that templates eliminate human error and ensure consistency. If I need 100 identical servers, I can use a template instead of repeating the manual steps 100 times.
* **JSON Structure:** I learned that Azure resources can be defined in JSON files, allowing infrastructure to be versioned and managed like software code.
* **Deployment Monitoring:** I practiced monitoring the deployment progress and verified the successful creation of resources through the **Activity Log**.

**Real-World Context:**
In a professional DevOps environment, nobody clicks buttons in the portal to create servers. Instead, engineers use templates (ARM or Bicep). This lab showed me how companies can "re-create" their entire data center in minutes if something goes wrong, simply by running a script.


<img width="1470" height="956" alt="lab 9-sarcina 1" src="https://github.com/user-attachments/assets/b5e34849-8666-4962-b515-5cc36c0ba207" />

## Final Skills Acquired
* **Cloud Infrastructure (IaaS):** Virtual Machines, Networking (VNET/NSG).
* **Modern Hosting (PaaS & Containers):** Azure App Service, Docker, ACI.
* **Serverless Computing:** Azure Functions.
* **Data Management:** Azure Storage, Blob containers.
* **IoT & Monitoring:** IoT Hub, Azure Monitor, Insights.
* **Automation:** ARM Templates (IaC).

















