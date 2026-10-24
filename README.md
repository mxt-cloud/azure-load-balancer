# Azure Load Balancer with Two Linux Virtual Machines

A hands-on Microsoft Azure project demonstrating how to configure a public Azure Load Balancer to distribute HTTP traffic across two Ubuntu Linux virtual machines running NGINX.

## Project Overview

This project demonstrates the configuration and testing of an Azure Load Balancer using two backend virtual machines. Each virtual machine runs an NGINX web server with a different response message, making it possible to verify that requests through the load balancer can reach both backend servers.

## Objectives

- Create and configure an Azure Load Balancer.
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
| Web Server | NGINX |
| Operating System | Ubuntu Linux |
| Protocol | HTTP |
| Port | TCP 80 |

## Project Architecture

The public frontend IP address receives HTTP requests. The Azure Load Balancer uses its load-balancing rule and health probe to direct eligible traffic to healthy backend virtual machines.

Both virtual machines run NGINX and serve different webpage messages so the backend responses can be identified during testing.

## Implementation Steps

### 1. Virtual Machines Running

Two Ubuntu Linux virtual machines were prepared as backend servers for the load-balancing configuration.

<img width="959" height="484" alt="01-virtual-machines png" src="https://github.com/user-attachments/assets/30e3f00b-368b-437f-ab76-81a58f867227" />

### 2. Azure Load Balancer Deployment

Created the public Standard Azure Load Balancer named `LB-ALTHAPH` in the `RG-MXT` resource group and configured its frontend public IP address.

<img width="959" height="479" alt="02-load-balancer-overview png" src="https://github.com/user-attachments/assets/52bfffdf-c164-4951-b313-864cbc820403" />

### 3. Backend Pool Configuration

Configured the backend pool and added both Linux virtual machines so the load balancer could direct eligible traffic to either server.

<img width="959" height="477" alt="03-backend-pool png" src="https://github.com/user-attachments/assets/61daaee0-8be8-47ee-ba62-2ca67fe7c880" />

### 4. HTTP Health Probe Configuration

Created an HTTP health probe to check backend availability and help the load balancer determine which backend instances are healthy.

<img width="959" height="474" alt="04-health-probe png" src="https://github.com/user-attachments/assets/5ce5cb43-908f-46e4-9e88-8d19a4f09445" />

### 5. Load-Balancing Rule Configuration

Configured the load-balancing rule to use the frontend IP address, backend pool, and health probe for HTTP traffic on port 80.

<img width="959" height="481" alt="05-load-balancing-rule png" src="https://github.com/user-attachments/assets/54dbc706-9844-4c5c-b91d-db1b866fef78" />

### 6. VM1 Inbound HTTP Security Rule

Configured an inbound security rule to permit HTTP traffic on TCP port 80 for the first virtual machine.

<img width="959" height="479" alt="06-vm1-http-rule png" src="https://github.com/user-attachments/assets/5525a2bd-9082-4a26-a555-5bce692cd188" />

### 7. VM2 Inbound HTTP Security Rule

Configured an inbound security rule to permit HTTP traffic on TCP port 80 for the second virtual machine.

<img width="959" height="476" alt="07-vm2-http-rule png" src="https://github.com/user-attachments/assets/aee67460-d1cd-4c2f-8abd-d429f1e0a8c9" />

### 8. HTTP Traffic Testing with PowerShell

Tested the frontend public IP address using PowerShell and `curl.exe`. The returned responses included the distinct NGINX messages from both backend virtual machines, confirming that requests could reach both servers.

Frontend IP: `172.169.167.183`

<img width="959" height="500" alt="HTTP traffic testing with PowerShell" src="https://github.com/user-attachments/assets/d3ed8895-cf00-44b8-a5d1-9cd9e0f36d0c" />

### 9. Backend Health Verification

Verified the backend health view in the Azure portal. Both virtual machines were shown as healthy in the captured screenshot.

<img width="959" height="473" alt="09-backend-health png" src="https://github.com/user-attachments/assets/e5c002fc-22bb-43ee-bb3f-313110f54149" />

## Testing and Results

The project was validated through the following checks:

- Both Linux virtual machines were running.
- NGINX was configured on the backend servers.
- Both virtual machines were added to the backend pool.
- The HTTP health probe and load-balancing rule were configured.
- Inbound HTTP access was configured for both backend virtual machines.
- HTTP requests to the frontend public IP returned responses from both backend servers during testing.
- The Azure portal showed both backend instances as healthy in the recorded verification screenshot.

## Skills Demonstrated

- Microsoft Azure Virtual Machines
- Azure Load Balancer
- Azure networking and frontend IP configuration
- Backend pool configuration
- Health probes and load-balancing rules
- Network Security Group inbound rules
- Linux server administration
- NGINX web server configuration
- PowerShell connectivity testing
- Cloud troubleshooting and validation

## Learning Outcome

This practical project provided hands-on experience configuring a public Azure Load Balancer with two Linux backend servers. It strengthened my understanding of frontend and backend configuration, health monitoring, network security rules, and HTTP traffic validation in Microsoft Azure.

## Project Information

**Project:** Azure Load Balancer with Two Linux Virtual Machines  
**Platform:** Microsoft Azure  
**Region:** Central US  
**Web Server:** NGINX  
**Protocol:** HTTP  
**Port:** TCP 80

**Author:** Althaph Muxith  
**Training Batch:** July-B
