# Azure Network Architecture

```mermaid
flowchart TB
    Admin[Administrator workstation] -->|Restricted public RDP 3389| MGMT
    subgraph VNET["VNET-CORP-LAB · [REDACTED_IP]"]
        subgraph M["Management · [REDACTED_IP] · NSG-MANAGEMENT"]
            MGMT[VM-MGMT-01]
        end
        subgraph S["Servers · [REDACTED_IP] · NSG-SERVERS"]
            SERVER[VM-SERVER-01]
        end
        subgraph A["Application · [REDACTED_IP] · NSG-APPLICATION"]
            APP[VM-APP-01 · IIS]
        end
        subgraph D["Database · [REDACTED_IP] · NSG-DATABASE"]
            DB["Database VM · NOT FOUND in export"]
        end
    end
    MGMT -->|RDP 3389 · tested| SERVER
    MGMT -->|HTTP 80 · tested| APP
    APP -.->|SQL 1433 · rule only, not tested| DB
```

Solid internal arrows indicate paths tested during the lab. The dashed SQL path indicates a configured NSG rule, not a verified database connection. The database VM is a planned component.