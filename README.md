PowerShell Automation for Microsoft 365 Engineering
This repository contains a collection of PowerShell scripts I’ve built to support day‑to‑day Microsoft 365 engineering work across Exchange Online, Entra ID, Teams Voice, SharePoint Online, and general governance tasks. These scripts were created to solve real operational problems in production environments and are designed to be simple, readable, and easy to adapt.

Overview
PowerShell is the backbone of Microsoft 365 administration and automation. Whether you’re managing mail flow, auditing identity, cleaning up SharePoint, or generating reports, scripting allows you to scale your work and reduce repetitive tasks.

This repo serves as a central place for the automation I’ve used while supporting:

Higher‑education systems

Regulated financial institutions

Cross‑tenant and migration projects

Governance and compliance initiatives

Each script reflects practical engineering needs — not theoretical examples.

Included Scripts
📬 Exchange Online
Scripts focused on reporting, mailbox management, and operational automation.

Mailbox Size Report  
Exports all mailboxes sorted by size to help identify users approaching quota thresholds.

(More Exchange Online scripts will be added as I continue organizing my automation library.)

Entra ID (Azure AD)
Identity‑focused automation such as group audits, lifecycle tasks, and access reporting.
(Coming soon.)

SharePoint Online
Governance and cleanup automation, including soft‑delete bin cleanup and site audits.
(Coming soon.)

powershell
<# 
Monthly export of users with mailboxes over 40GB.
Connect to Exchange Online first:
Connect-ExchangeOnline
#>

$date = (Get-Date).ToString("dd-MM-yyyy")

Get-EXOMailbox -ResultSize Unlimited |
    Get-EXOMailboxStatistics |
    Select-Object DisplayName, TotalItemSize, Mail |
    Sort-Object TotalItemSize -Descending |
    Export-Csv "C:\exchange_$date.csv" -NoTypeInformation

Write-Host "Mailbox size report completed." -ForegroundColor Green
Purpose of This Repository
This repo exists to:

Document the automation I’ve built across multiple Microsoft 365 environments

Share practical tools that other engineers can use or adapt

Demonstrate my approach to scripting, governance, and operational engineering

Serve as a living portfolio of my PowerShell work

As I continue refining and uploading scripts, this repository will grow into a full collection of Microsoft 365 engineering automation.

Notes
All scripts require appropriate permissions in Microsoft 365.

Some scripts require interactive authentication due to MFA/security policies.

Always test scripts in a non‑production environment before deployment.
