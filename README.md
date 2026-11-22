# Azure VM Lab

## Status

Done — WinVM-01 was deployed in the Azure free trial, ran, and was then
stopped (deallocated). The whole resource group AlvinLab-RG was deleted
Nov 22, 2026, after the work was documented here, so nothing bills the
card after the $200 credit expires Dec 21, 2026.

## What This Is

I deployed and configured a Windows virtual machine in Microsoft Azure
as part of building my hands-on cloud infrastructure skills.

## Tools Used

- Microsoft Azure (free trial — $200 credit; upgraded to pay-as-you-go Nov 21, 2026 for the Front Door labs, spending limit removed)
- Azure Virtual Machines
- Remote Desktop Protocol (RDP)
- Azure Resource Groups
- Azure Virtual Network (auto-configured)
- Azure Cost Management ($1 budget alert)

## What I Built

- Created a Resource Group called AlvinLab-RG in East US 2. Outcome: the group is live and holds WinVM-01, its network, NSG, snapshot and budget.
- Deployed WinVM-01: Windows Server 2022 Datacenter - x64 Gen2,
  Standard_D2als_v6 (2 vCPU, 4 GiB memory), RDP on port 3389,
  administrator labadmin, public IP 20.119.172.115
- The VM reached Status: Running on Nov 21, 2026, with agent status Ready
- Stopped (deallocated) the VM after practice to preserve the free credit —
  compute charges stop when deallocation completes
- Created a $1 Cost Management budget ("OneDollarBudget") with alerts at
  50% and 100% of actual cost, so spending is watched. Outcome: the budget is live with both alerts; evaluated spend $0.00.
- Connected to WinVM-01 by RDP through Azure Bastion Developer (free SKU,
  $0/hour) on Nov 21, 2026 — the desktop showed Server Manager open;
  the VM was stopped (deallocated) again right after, to preserve the
  free credit
- Restricted RDP access with an NSG rule: the inbound RDP rule (priority
  300, TCP 3389) in NSG WinVM-01-nsg now allows only a single home public
  IP (/32) instead of Any, so the VM's public RDP port is not open to the
  internet. Bastion access was not touched.
- Created a snapshot of the VM's OS disk
  (WinVM-01-osdisk-snapshot-20261121, 127 GiB, Standard HDD
  zone-redundant, Incremental, Succeeded) on Nov 21, 2026, as a restore
  point before further changes.
- Assigned the Reader role on resource group AlvinLab-RG to test user
  Alex Rivera (Entra ID), demonstrating RBAC scoping to a resource group. Outcome: Alex Rivera can read AlvinLab-RG but cannot change it.
- Practiced VM resizing: resized WinVM-01 from Standard_D2als_v6 to
  Standard_D2ls_v6 (2 vCPU, 4 GiB, same D-Series v6 family) and back to
  Standard_D2als_v6, confirming both resizes succeeded. The first choice,
  Standard_D2s_v3, and the v4/v5 D-series sizes were all unavailable for
  this subscription in East US 2 ("NotAvailableForSubscription"), so the
  resize used D2ls_v6, the available size in the same family. The VM stayed
  stopped (deallocated) throughout.

## Why Windows Server 2022 (not Windows 11 Pro)

The guide's original spec (Windows 11 Pro, Standard_B1s, East US) cannot
be built under the free-trial-only rules: Windows 11 Pro requires a
subscription with no spending limit plus a licence attestation, and
Standard_B1s is not available in East US or East US 2 for this
subscription. Windows Server 2022 Datacenter is the closest $0
out-of-pocket alternative — still Windows, still RDP, same region family —
and it is free-services eligible. Cost is $125.56/month ($0.1720/hr),
paid only from the $200 free credit, $0 out of pocket.

## Cost

- $125.56/month ($0.1720/hr) while running, paid from the $200 free
  credit only — $0 out of pocket
- Spending limit removed: the subscription was upgraded to pay-as-you-go Nov 21, 2026 (for the Front Door labs), so the credit is used first and anything beyond it would bill the card — the VM stays stopped (deallocated) when not in use, so nothing bills
- Deleted Nov 22, 2026: the whole resource group AlvinLab-RG (VM, OS disk,
snapshot, public IP, vnet, NSG, NIC, Bastion host) was deleted after
documentation, so the $0.12/day storage/IP/snapshot accrual has stopped
and nothing can bill the card after the credit expires Dec 21, 2026.

## Why It Matters

Enterprise IT environments rely heavily on virtual machines for
remote administration, testing, and infrastructure management.
This lab demonstrates my ability to provision, configure, and
connect to cloud-based Windows machines — a core skill for
Azure and Microsoft 365 administration roles.

## Screenshots

- [winvm-01-overview-screenshot.pdf](winvm-01-overview-screenshot.pdf) — WinVM-01 Overview (Status Running,
  AlvinLab-RG, East US 2, Standard_D2als_v6, Windows Server 2022
  Datacenter, public IP 20.119.172.115)
- [winvm-01-overview-deallocating-screenshot.pdf](winvm-01-overview-deallocating-screenshot.pdf) — WinVM-01 Overview
  after stopping (Status Deallocating, on its way to Stopped)
- [onedollarbudget-screenshot.pdf](onedollarbudget-screenshot.pdf) — Cost Management budget detail for
  OneDollarBudget (evaluated spend $0.00)
- [bastion-rdp-summary.pdf](bastion-rdp-summary.pdf) — Bastion Developer RDP connection summary for
  WinVM-01 (Step 4B): free Developer SKU, connected Nov 21, 2026, desktop
  shown, VM stopped again after. A summary, not a screenshot, because the
  RDP desktop is a live canvas that does not survive print-to-PDF — the
  print-to-PDF capture came out mostly blank, so this records the
  verified connection details instead. Same approach as the Entra ID
  summaries.

## Next Steps

- ~~Add Azure Bastion for RDP without exposing public IP~~ — Done Nov 21,
  2026 (Bastion Developer, free SKU; see [bastion-rdp-summary.pdf](bastion-rdp-summary.pdf))
- ~~Configure NSG rules to restrict access by IP~~ — Done Nov 21, 2026
  (RDP rule now allows only a single home IP /32, not Any)
- ~~Practice VM resizing and snapshotting~~ — Done Nov 21, 2026.
  Snapshot WinVM-01-osdisk-snapshot-20261121 (127 GiB) created; resize
  practiced D2als_v6 to D2ls_v6 and back to D2als_v6 (D2s_v3 and the v4/v5
  D-series sizes were unavailable for this subscription in East US 2).
- ~~Assign RBAC roles to the Resource Group~~ — Done Nov 21, 2026 (Reader
  role on AlvinLab-RG assigned to test user Alex Rivera)
