# Azure VM Lab

## Status

In progress — the VM deployment is underway in the Azure free account.
The resource group (AlvinLab-RG) and the VM (WinVM-01) are being created
in the Azure portal; this README will be updated with the real screenshots
once the deployment finishes.

## What This Is

I deployed and configured a Windows 11 Virtual Machine in Microsoft Azure
as part of building my hands-on cloud infrastructure skills.

## Tools Used

- Microsoft Azure (Free Tier)
- Azure Virtual Machines
- Remote Desktop Protocol (RDP)
- Azure Resource Groups
- Azure Virtual Network (auto-configured)

## What I Built

- Created a Resource Group called AlvinLab-RG in East US region
- Deployed a Windows 11 Pro VM (Standard_B1s — free tier)
- Configured Network Security Group to allow RDP on port 3389
- Connected remotely via RDP from my local machine
- Verified connectivity and explored the VM environment

## Why It Matters

Enterprise IT environments rely heavily on virtual machines for
remote administration, testing, and infrastructure management.
This lab demonstrates my ability to provision, configure, and
connect to cloud-based Windows machines — a core skill for
Azure and Microsoft 365 administration roles.

## Screenshots

See the /screenshots folder in this repository.

## Next Steps

- Add Azure Bastion for RDP without exposing public IP
- Configure NSG rules to restrict access by IP
- Practice VM resizing and snapshotting
- Assign RBAC roles to the Resource Group
