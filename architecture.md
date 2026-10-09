# Azure Corporate Network Architecture

```mermaid
flowchart TB
  Internet([Administrator workstation]) -->|RDP 3389 restricted to trusted public IP| MGMT
  subgraph VNET["VNET-CORP-LAB · 10.20.0.0/16 (logical overview)"]
    subgraph M["SNET-MANAGEMENT · 10.20.1.0/24 · NSG-MANAGEMENT"]
      MGMT["VM-MGMT-01 · 10.20.1.4"]
    end
    subgraph S["SNET-SERVERS · 10.20.2.0/24 · NSG-SERVERS"]
      SRV["VM-SERVER-01 · 10.20.2.4"]
    end
    subgraph A["SNET-APPLICATION · 10.20.3.0/24 · NSG-APPLICATION"]
      APP["VM-APP-01 · 10.20.3.4 · IIS"]
    end
    subgraph D["SNET-DATABASE · 10.20.4.0/24 · NSG-DATABASE"]
      DB["VM-DB-01 · private IP to verify · SQL setup pending"]
    end
  end
  MGMT -->|RDP 3389 · verified| SRV
  MGMT -->|HTTP 80 · verified| APP
  MGMT -->|RDP 3389 · configured; verify| DB
  APP -.->|SQL TCP 1433 · planned / not yet verified| DB
```

> Diagram depicts logical traffic paths, not a claim that all services are running. The VNet-wide address space shown is illustrative; verify the actual VNet address space in Azure before publishing.
