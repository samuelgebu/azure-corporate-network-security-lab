# Azure Corporate Network Architecture

```mermaid
flowchart TB
  Internet([Administrator workstation]) -->|RDP 3389 restricted to trusted public IP| MGMT
  subgraph VNET["VNET-CORP-LAB · [REDACTED_IP] (logical overview)"]
    subgraph M["SNET-MANAGEMENT · [REDACTED_IP] · NSG-MANAGEMENT"]
      MGMT["VM-MGMT-01 · [REDACTED_IP]"]
    end
    subgraph S["SNET-SERVERS · [REDACTED_IP] · NSG-SERVERS"]
      SRV["VM-SERVER-01 · [REDACTED_IP]"]
    end
    subgraph A["SNET-APPLICATION · [REDACTED_IP] · NSG-APPLICATION"]
      APP["VM-APP-01 · [REDACTED_IP] · IIS"]
    end
    subgraph D["SNET-DATABASE · [REDACTED_IP] · NSG-DATABASE"]
      DB["VM-DB-01 · private IP to verify · SQL setup pending"]
    end
  end
  MGMT -->|RDP 3389 · verified| SRV
  MGMT -->|HTTP 80 · verified| APP
  MGMT -->|RDP 3389 · configured; verify| DB
  APP -.->|SQL TCP 1433 · planned / not yet verified| DB
```

> Diagram depicts logical traffic paths, not a claim that all services are running. The VNet-wide address space shown is illustrative; verify the actual VNet address space in Azure before publishing.
