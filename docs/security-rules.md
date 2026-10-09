# Network Security Group Rules

These are configured **inbound** NSG rules from the Azure lab; they are not proof that an application is listening.

| NSG | Allow rule | Source | Destination port | Priority |
|---|---|---|---|---|
| NSG-MANAGEMENT | RDP from servers | Servers subnet | TCP 3389 | 100 |
| NSG-MANAGEMENT | Restricted admin RDP | Administrator public IP (redacted) | TCP 3389 | 101 |
| NSG-SERVERS | RDP from management | Management subnet | TCP 3389 | 100 |
| NSG-APPLICATION | Web access | Management subnet | TCP 80/443 | 100 |
| NSG-DATABASE | Planned SQL access | Application subnet | TCP 1433 | 100 |

Each NSG also includes an explicit inbound VNet-deny rule at priority 200. Azure's default rules and effective rules must also be considered when analyzing traffic.

**Validation:** Management-to-Server RDP and Management-to-Application HTTP succeeded; Management-to-Application RDP failed. SQL connectivity is unverified.

**Security:** The restricted administrator public IP is intentionally omitted. For production workloads, prefer Bastion or just-in-time access instead of direct public RDP.