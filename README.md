# Azure Corporate Network Infrastructure & Security Lab

**Samuel Gebu | Azure Administration & Cloud Networking Portfolio**

> **Project status:** Network segmentation and security rules configured; three Windows VMs listed in the supplied inventory. Internal RDP and HTTP connectivity were tested. Database VM and SQL connectivity remain pending.

## Project overview

This hands-on Azure lab documents the configuration of a segmented corporate network, subnet-level Network Security Groups (NSGs), Windows virtual machines, and connectivity testing.

The technical details below are based on project information and an Azure inventory export previously supplied by the project author. **The GitHub repository is not a live connection to the Azure subscription.** Screenshots show the configuration views captured at the time, not necessarily current resource state.

## Azure environment

| Component | Configuration |
| --- | --- |
| Resource group | `RG-CORP-NETWORK-LAB` |
| Azure region | South Africa North |
| Virtual network | `VNET-CORP-LAB` — `10.20.0.0/16` |
| Management subnet | `SNET-MANAGEMENT` — `10.20.1.0/24` — `NSG-MANAGEMENT` |
| Servers subnet | `SNET-SERVERS` — `10.20.2.0/24` — `NSG-SERVERS` |
| Application subnet | `SNET-APPLICATION` — `10.20.3.0/24` — `NSG-APPLICATION` |
| Database subnet | `SNET-DATABASE` — `10.20.4.0/24` — `NSG-DATABASE` |

## Virtual machines

| VM | Role | Evidence status |
| --- | --- | --- |
| `VM-MGMT-01` | Administrative access | Listed in supplied inventory |
| `VM-SERVER-01` | Internal Windows server | Listed in supplied inventory |
| `VM-APP-01` | IIS application/web server | Listed in supplied inventory |
| `VM-DB-01` | Planned SQL database | Not found in supplied inventory |

An inventory entry does not establish whether a VM is currently running.

## Network security

Subnet-level NSGs were configured to restrict inbound traffic. Management-to-Server RDP uses TCP 3389. The Application subnet permits HTTP/HTTPS (TCP 80/443) from Management. The Database NSG includes an inbound SQL rule (TCP 1433) from Application, but a working database endpoint has not been verified.

The administrator's public RDP source address is deliberately excluded from published documentation. See [NSG rule documentation](docs/security-rules.md).

## Connectivity testing

| Test | Reported result |
| --- | --- |
| Management → Server, TCP 3389 | Successful |
| Management → Application, TCP 3389 | Blocked |
| Management → Application, HTTP 80 | Successful; IIS page loaded |
| Application → Database, TCP 1433 | Not verified |

These test results were reported during the project and are not live tests performed by GitHub.

## Authentic Azure Portal screenshots

The [screenshots folder](images/screenshots/) is the designated location for **screenshots captured from the author's own Azure Portal session**. The evidence set is intended to document:

1. Resource group
2. Virtual network
3. Subnet configuration
4. Virtual machine configuration
5. Management NSG
6. Server NSG

**Evidence limitations:** Azure Portal configuration screens show settings at capture time. They do not, by themselves, prove that VMs are running, that an application is reachable, or that all connectivity tests passed. Refer to the separate test notes and export findings for those claims.

**Privacy:** Public IP addresses, subscription IDs, account emails, passwords, and tokens should be obscured before publication. Private lab addresses such as `10.20.1.4` are intentionally retained to make the network design understandable.

## Documentation

- [Network security group rules](docs/security-rules.md)
- [Azure inventory export findings and limitations](docs/export-findings.md)
- [Screenshot evidence folder](images/screenshots/)

## Outstanding work

- Deploy and verify the database VM and SQL connectivity, if still in project scope.
- Capture separate evidence of deployed resource state and connectivity tests where needed.
- Consider Azure Bastion or just-in-time access for hardened administration.

---

**Author:** Samuel Gebu

*Portfolio documentation describes the author's lab work and is not a claim of independently verified live Azure access.*
