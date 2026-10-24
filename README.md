# Azure Load Balancer with Two Linux Virtual Machines

## Project Overview

This hands-on Azure project demonstrates how to configure a public Azure Load Balancer to distribute HTTP traffic across two Ubuntu Linux virtual machines running NGINX.

## Objectives

- Create and configure an Azure Load Balancer.
- Configure two Ubuntu Linux virtual machines as backend servers.
- Install and test NGINX on both virtual machines.
- Configure a backend pool, health probe, and load-balancing rule.
- Configure network security rules for HTTP traffic.
- Test traffic through the load balancer's frontend IP address.

## Azure Resources

| Resource | Configuration |
|---|---|
| Resource Group | `RG-MXT` |
| Load Balancer | `LB-ALTHAPH` |
| SKU | Standard |
| Type | Public |
| Region | Central US |
| Backend Pool | `backendpool-althaph` |
| Health Probe | `probe-http-althaph` |
| Load-Balancing Rule | `rule-http-althaph` |
| Backend Servers | `VM1-ALTHAPH-LINUX`, `VM2-ALTHAPH-LINUX` |
| Web Server | NGINX |
| Protocol | HTTP |

## Implementation

1. Created two Ubuntu Linux virtual machines.
2. Installed and verified NGINX on both servers.
3. Created a Standard public Azure Load Balancer.
4. Configured the frontend IP and backend pool.
5. Created an HTTP health probe.
6. Configured the HTTP load-balancing rule.
7. Added the required inbound HTTP network security rules.
8. Tested HTTP connectivity through the frontend IP.
9. Verified backend health in the Azure portal.

## Validation and Results

PowerShell HTTP tests against the load balancer's frontend IP returned responses identifying both backend servers:

- `Hello from VM1-ALTHAPH-LINUX`
- `Hello from VM2-ALTHAPH-LINUX`

The Azure portal's backend health view also showed both backend instances as healthy during testing.

## Skills Practised

- Microsoft Azure Virtual Machines
- Azure Load Balancer
- Azure Virtual Networking
- Network Security Groups
- Ubuntu Linux
- NGINX
- HTTP health probes
- Load-balancing rules
- PowerShell connectivity testing
- Troubleshooting

## Project Evidence

Screenshots documenting the deployment, configuration, testing, and backend health will be provided in the `screenshots/` directory.

## Learning Outcome

This practical strengthened my understanding of Azure load balancing, Linux web server configuration, network security, and connectivity validation in a cloud lab environment.

**Environment:** Azure lab environment  
**Project type:** Hands-on learning project

