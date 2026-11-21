# Azure VM Lab

## Status

Done — WinVM-01 was deployed in the Azure free trial, ran, and was then
stopped (deallocated) to preserve the $200 free credit.

## What This Is

I deployed and configured a Windows virtual machine in Microsoft Azure
as part of building my hands-on cloud infrastructure skills.

## Tools Used

- Microsoft Azure (free trial — $200 credit, spending limit ON)
- Azure Virtual Machines
- Remote Desktop Protocol (RDP)
- Azure Resource Groups
- Azure Virtual Network (auto-configured)
- Azure Cost Management ($1 budget alert)

## What I Built

- Created a Resource Group called AlvinLab-RG in East US 2
- Deployed WinVM-01: Windows Server 2022 Datacenter - x64 Gen2,
  Standard_D2als_v6 (2 vCPU, 4 GiB memory), RDP on port 3389,
  administrator labadmin, public IP 20.119.172.115
- The VM reached Status: Running on Nov 21, 2026, with agent status Ready
- Stopped (deallocated) the VM after practice to preserve the free credit —
  compute charges stop when deallocation completes
- Created a $1 Cost Management budget ("OneDollarBudget") with alerts at
  50% and 100% of actual cost, so spending is watched
- Connected to WinVM-01 by RDP through Azure Bastion Developer (free SKU,
  $0/hour) on Nov 21, 2026 — the desktop showed Server Manager open;
  the VM was stopped (deallocated) again right after, to preserve the
  free credit

## Why Windows Server 2022 (not Windows 11 Pro)

The guide's original spec (Windows 11 Pro, Standard_B1s, East US) cannot
be built under the free-trial-only rules: Windows 11 Pro requires a
subscription with no spending limit plus a licence attestation, and
Standard_B1s is not available in East US or East US 2 for this
subscription. Windows Server 2022 Datacenter is the closest $0
out-of-pocket alternative — still Windows, still RDP, same region family —
and it is free-services eligible. Cost is $125.56/month ($0.1720/hr),
paid only from the $200 free credit, with the spending limit ON, so
nothing comes out of my own pocket.

## Cost

- $125.56/month ($0.1720/hr) while running, paid from the $200 free
  credit only — $0 out of pocket
- Spending limit ON: Azure disables the subscription when the credit is
  exhausted, so there is no bill
- The VM is stopped (deallocated) when not in use

## Why It Matters

Enterprise IT environments rely heavily on virtual machines for
remote administration, testing, and infrastructure management.
This lab demonstrates my ability to provision, configure, and
connect to cloud-based Windows machines — a core skill for
Azure and Microsoft 365 administration roles.

## Screenshots

- winvm-01-overview-screenshot.pdf — WinVM-01 Overview (Status Running,
  AlvinLab-RG, East US 2, Standard_D2als_v6, Windows Server 2022
  Datacenter, public IP 20.119.172.115)
- winvm-01-overview-deallocating-screenshot.pdf — WinVM-01 Overview
  after stopping (Status Deallocating, on its way to Stopped)
- onedollarbudget-screenshot.pdf — Cost Management budget detail for
  OneDollarBudget (evaluated spend $0.00)
- bastion-rdp-summary.pdf — Bastion Developer RDP connection summary for
  WinVM-01 (Step 4B): free Developer SKU, connected Nov 21, 2026, desktop
  shown, VM stopped again after. A summary, not a screenshot, because the
  RDP desktop is a live canvas that does not survive print-to-PDF — the
  print-to-PDF capture came out mostly blank, so this records the
  verified connection details instead. Same approach as the Entra ID
  summaries.

## Next Steps

- ~~Add Azure Bastion for RDP without exposing public IP~~ — Done Nov 21,
  2026 (Bastion Developer, free SKU; see bastion-rdp-summary.pdf)
- Configure NSG rules to restrict access by IP
- Practice VM resizing and snapshotting
- Assign RBAC roles to the Resource Group
