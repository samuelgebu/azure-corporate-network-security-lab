# Azure Export Findings

**Source:** Azure PowerShell inventory export supplied by the project author.  
**Resource group:** `RG-CORP-NETWORK-LAB`  
**Region:** South Africa North.

## Confirmed
- VNet `VNET-CORP-LAB` (`10.20.0.0/16`).
- Four /24 subnets: Management, Servers, Application, Database.
- Four matching subnet-level NSGs.
- Three Windows VMs: `VM-MGMT-01`, `VM-SERVER-01`, `VM-APP-01`.
- User-reported validation: Management-to-Server RDP works; Management-to-Application HTTP/IIS works; Management-to-Application RDP is blocked.

## Not confirmed
- `VM-DB-01` was not listed in the supplied export.
- SQL Server installation, service state, and TCP 1433 connectivity were not established.
- VM inventory does not prove the VMs are currently running.

## Privacy
Public administrator IPs, account identifiers and other sensitive values should not be published. Internal RFC 1918 subnet ranges are retained to explain the architecture. Genuine screenshots should be reviewed and redacted before upload.