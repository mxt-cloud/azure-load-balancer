# Azure Load Balancer with Two Linux Virtual Machines

A hands-on Microsoft Azure project demonstrating the configuration of a public Azure Load Balancer to distribute HTTP traffic across two Ubuntu Linux virtual machines running NGINX.

**GitHub Repository:** [Azure Load Balancer Project](https://github.com/mxt-cloud/azure-load-balancer)

## Project Overview

This project demonstrates the configuration and testing of an Azure Load Balancer using two backend virtual machines. Each virtual machine runs an NGINX web server with a distinct response message, allowing me to verify that HTTP requests through the load balancer can reach both backend servers.

## Objectives

- Create and configure a public Azure Load Balancer.
- Configure a frontend public IP address.
- Add two Linux virtual machines to a backend pool.
- Configure an HTTP health probe.
- Create an HTTP load-balancing rule.
- Configure inbound HTTP access for both virtual machines.
- Test HTTP connectivity through the load balancer.
- Verify the health of the backend virtual machines.

## Azure Resources Used

| Resource | Configuration |
|---|---|
| Resource Group | `RG-MXT` |
| Load Balancer | `LB-ALTHAPH` |
| Region | Central US |
| SKU | Standard |
| Load Balancer Type | Public |
| Frontend Configuration | `frontend-althaph` |
| Frontend Public IP | `172.169.167.183` |
| Backend Pool | `backendpool-althaph` |
| Health Probe | `probe-http-althaph` |
| Load-Balancing Rule | `rule-http-althaph` |
| Backend VM 1 | `VM1-ALTHAPH-LINUX` |
| Backend VM 2 | `VM2-ALTHAPH-LINUX` |
| Operating System | Ubuntu Linux |
| Web Server | NGINX |
| Protocol | HTTP |
| Port | TCP 80 |

## Project Architecture

The public frontend IP address receives HTTP requests. The Azure Load Balancer uses its load-balancing rule and health probe to direct eligible traffic to healthy backend virtual machines.

Both virtual machines run NGINX and serve different webpage messages, allowing the backend responses to be identified during testing.

## Implementation Steps

### 1. Virtual Machines Running

Prepared two Ubuntu Linux virtual machines to act as backend web servers for the load-balancing configuration.

<img width="959" height="484" alt="Both Azure virtual machines running" src="https://github.com/user-attachments/assets/30e3f00b-368b-437f-ab76-81a58f867227" />

### 2. Azure Load Balancer Deployment

Created the public Standard Azure Load Balancer named `LB-ALTHAPH` in the `RG-MXT` resource group in the Central US region and configured its frontend public IP address.

<img width="959" height="479" alt="Azure Load Balancer deployment and frontend IP" src="https://github.com/user-attachments/assets/52bfffdf-c164-4951-b313-864cbc820403" />

### 3. Backend Pool Configuration

Configured the backend pool and added both Linux virtual machines so the load balancer could direct eligible traffic to either backend server.

<img width="959" height="477" alt="Backend pool containing both virtual machines" src="https://github.com/user-attachments/assets/61daaee0-8be8-47ee-ba62-2ca67fe7c880" />

### 4. HTTP Health Probe Configuration

Created an HTTP health probe to monitor backend availability and help the load balancer determine which backend instances are healthy.

<img width="959" height="474" alt="HTTP health probe configuration" src="https://github.com/user-attachments/assets/5ce5cb43-908f-46e4-9e88-8d19a4f09445" />

### 5. Load-Balancing Rule Configuration

Configured the load-balancing rule to use the frontend IP address, backend pool, and health probe for HTTP traffic on TCP port 80.

<img width="959" height="481" alt="Load-balancing rule configuration" src="https://github.com/user-attachments/assets/54dbc706-9844-4c5c-b91d-db1b866fef78" />

### 6. VM1 Inbound HTTP Security Rule

Configured an inbound Network Security Group (NSG) rule for TCP port 80 to allow HTTP traffic to the first virtual machine.

<img width="959" height="479" alt="VM1 inbound HTTP security rule" src="https://github.com/user-attachments/assets/5525a2bd-9082-4a26-a555-5bce692cd188" />

### 7. VM2 Inbound HTTP Security Rule

Configured an inbound Network Security Group (NSG) rule for TCP port 80 to allow HTTP traffic to the second virtual machine.

<img width="959" height="476" alt="VM2 inbound HTTP security rule" src="https://github.com/user-attachments/assets/aee67460-d1cd-4c2f-8abd-d429f1e0a8c9" />

### 8. HTTP Traffic Testing with PowerShell

Tested the load balancer's frontend public IP address using PowerShell and `curl.exe`. The responses included distinct NGINX messages from both backend virtual machines, confirming that HTTP requests could reach both servers through the load balancer.

Frontend IP: `172.169.167.183`

<img width="959" height="500" alt="HTTP traffic testing with PowerShell" src="https://github.com/user-attachments/assets/d3ed8895-cf00-44b8-a5d1-9cd9e0f36d0c" />

### 9. Backend Health Verification

Verified the backend health view in the Azure portal. Both virtual machines were shown as healthy in the captured screenshot.

<img width="959" height="473" alt="Backend health verification showing both virtual machines healthy" src="https://github.com/user-attachments/assets/e5c002fc-22bb-43ee-bb3f-313110f54149" />

## Testing and Results

The project was validated through the following checks:

- Both Linux virtual machines were running.
- NGINX was configured on the backend servers.
- Both virtual machines were added to the backend pool.
- The HTTP health probe and load-balancing rule were configured.
- Inbound HTTP security rules were configured for both virtual machines.
- HTTP requests to the frontend public IP returned distinct responses from both backend servers during testing.
- The Azure portal showed both backend instances as healthy in the recorded verification screenshot.

## Skills Demonstrated

- Microsoft Azure Virtual Machines
- Azure Load Balancer configuration
- Azure networking and frontend IP configuration
- Backend pool configuration
- Health probes and load-balancing rules
- Network Security Group (NSG) rules
- Ubuntu Linux administration
- NGINX web server configuration
- PowerShell connectivity testing
- Cloud troubleshooting and validation

## Learning Outcome

This practical project provided hands-on experience configuring and testing a public Azure Load Balancer with two Linux backend servers. It strengthened my understanding of frontend and backend configuration, health monitoring, network security rules, and HTTP traffic validation in Microsoft Azure.

## Project Information

- **Project:** Azure Load Balancer with Two Linux Virtual Machines
- **Platform:** Microsoft Azure
- **Region:** Central US
- **Operating System:** Ubuntu Linux
- **Web Server:** NGINX
- **Protocol:** HTTP
- **Port:** TCP 80
- **Author:** Althaph Muxith
