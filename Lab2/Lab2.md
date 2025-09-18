# Lab 2 - IaaS/PaaS architecture
## Name: Rohan Yogesh Surti (surt0008)
## Scenario: The following application consists of a Web Server written in Flask. A UI front end written in React. A database layer consisting of Postgres.
## PaaS
In PaaS, we don’t use VMs directly. Instead, the React front-end runs as a Web App service (FEsvc, FEsvc1). The Flask backend also runs as a Web App service (MTsvc). The Postgres database is a managed Postgres DB service provided by the cloud. The cloud provider takes care of patching, scaling, and updates.

The diagram shows users sending requests through the Traffic Manager, then through a Firewall, and then to a Load Balancer. The load balancer sends traffic to two front-end services (FEsvc, FEsvc1). These connect to the mid-tier Flask service (MTsvc), which then connects to a managed Postgres database. All of them run inside a virtual network (VNet), with switches linking services.

```mermaid
flowchart TD
    U[User] --> TM[Traffic Manager]
    TM --> FW[Firewall]
    FW --> LB[Load Balancer]
    FW --- NSG
    LB --> FEsvc
    LB --> FEsvc1
    FEsvc --> MTsvc
    FEsvc1 --> MTsvc
    MTsvc --> ManagedPostgresDB

    subgraph VNet[PaaS Azure VNet]
        FEsvc
        FEsvc1
        MTsvc
        ManagedPostgresDB
        SwitchY[Switch]
        SwitchZ[Switch]
        SwitchY --- MTsvc
        SwitchZ --- ManagedPostgresDB
    end
```
## IaaS:
In IaaS, we use virtual machines for everything. The React front-end runs on two VMs (FEVM1 and FEVM2). The Flask backend runs on another VM (MTVM). The Postgres database runs on a separate VM (DBVM). We connect them inside a virtual network, and they are split into different VLANs (front-end, mid-tier, and database). We have to manage the operating systems, updates, and scaling ourselves.

The diagram shows users sending requests through a Traffic Manager, then through a Firewall, and then to a Load Balancer. The load balancer sends traffic to the two front-end VMs. These talk to the mid-tier VM running Flask, which then talks to the Postgres database VM. Switches connect the VMs inside VLANs to keep traffic organized and secure.


```mermaid
flowchart TD
    U[User] --> TM[Traffic Manager]
    TM --> FW[Firewall]
    FW --> LB[Load Balancer]
    FW --- NSG
    LB --> FEVM1
    LB --> FEVM2
    FEVM1 --> MTVM[(Flask)]
    FEVM2 --> MTVM
    MTVM --> DBVM[(Postgres)]

    subgraph VNet[IaaS Cloud Virtual Network]
        subgraph VLAN1[VLAN - FE Layer]
            FEVM1
            FEVM2
        end
        subgraph VLAN2[VLAN - MidTier Layer]
            MTVM
        end
        subgraph VLAN3[VLAN - DB Layer]
            DBVM
        end
        SwitchA[Switch] --- FEVM1
        SwitchA --- FEVM2
        SwitchB[Switch] --- MTVM
        SwitchC[Switch] --- DBVM
    end

```
### On-prem
In an on-premises setup, everything is managed in our own data center. Users’ requests go through Traffic Manager, Firewall, and Load Balancer to front-end servers, then to the mid-tier Flask servers, and finally to the Postgres database server. Physical network switches connect all the layers. We are responsible for everything like servers, operating systems, databases, security, updates, and backups. This gives us full control, but we have to work more and it is harder to scale compared to cloud options.

```mermaid
flowchart TD
    U[User] --> TM[Traffic Manager]
    TM --> FW[Firewall]
    FW --> LB[Load Balancer]
    FW --> NSG
    LB --> FE1[Front-End]
    LB --> FE2[Front-End]
    FE1 --> MT[MidTier]
    FE2 --> MT
    MT --> DB[Postgres Database]

    subgraph VNet[On premises Data center]
            FE1
            FE2
            MT
            DB
        Switch1[Switch] --- FE1
        Switch1 --- FE2
        Switch2[Switch] --- MT
        Switch3[Switch] --- DB
    end

    
```
