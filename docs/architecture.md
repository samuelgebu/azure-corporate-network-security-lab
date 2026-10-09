# Azure Network Architecture

```mermaid
flowchart TB
    Admin[Administrator workstation] -->|Restricted public RDP 3389| MGMT
    subgraph VNET["VNET-CORP-LAB · 10.20.0.0/16"]
        subgraph M["Management · 10.20.1.0/24 · NSG-MANAGEMENT"]
            MGMT[VM-MGMT-01]
        end
        subgraph S["Servers · 10.20.2.0/24 · NSG-SERVERS"]
            SERVER[VM-SERVER-01]
        end
        subgraph A["Application · 10.20.3.0/24 · NSG-APPLICATION"]
            APP[VM-APP-01 · IIS]
        end
        subgraph D["Database · 10.20.4.0/24 · NSG-DATABASE"]
            DB["Database VM · NOT FOUND in export"]
        end
    end
    MGMT -->|RDP 3389 · tested| SERVER
    MGMT -->|HTTP 80 · tested| APP
    APP -.->|SQL 1433 · rule only, not tested| DB
```

Solid internal arrows indicate paths tested during the lab. The dashed SQL path indicates a configured NSG rule, not a verified database connection. The database VM is a planned component.