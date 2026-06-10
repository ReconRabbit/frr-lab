# FRR Multi-Subnet Routing Laboratory (Zero-Setup Deployment)

This repository contains a fully automated, pre-configured 2-router network laboratory built using FRRouting (FRR) and OpenSSH. All software packages, SSH access controls, daemon configurations, and OSPF routing protocols are baked completely inside the standalone container images. 

Students do not need to configure any text files or map local tracking volumes to launch the environment.

## Network Topology Map
* **Router 1 Local Production Subnet:** 10.1.0.0/24 (Router Interface: 10.1.0.11)
* **Router 2 Local Production Subnet:** 10.2.0.0/24 (Router Interface: 10.2.0.12)
* **Transit Backbone Interconnect Subnet:** 172.30.0.0/24 (R1 Link: 172.30.0.11 | R2 Link: 172.30.0.12)

---

## Lab Deployment Instructions

Execute these commands sequentially inside your terminal window to deploy the complete, pre-synchronized routing infrastructure on your host machine.

### 1. Initialize Your Workspace
Create a fresh folder directory for your laboratory profile and switch into it:
```bash
mkdir frr-routing-lab && cd frr-routing-lab
```

### 2. Fetch the Deployment Configuration
Pull down the core multi-network definition layout file:
```bash
Head to the released page and downlaod the docker-compose.yml
```

### 3. Download the Standalone Master Images
Download the pre-compiled standalone container snapshots directly from the laboratory release assets portal:
```bash
Head to the releases page to downlaod the two .tar files
```
*(Note: Do not attempt to extract, unzip, or untar these files using your file manager. Leave them intact as `.tar` files).*

### 4. Register the Blueprints with Docker
Import the snapshot blueprints straight into your local Docker system engine cache database:
```bash
docker load < frr-zero-setup-r1.tar
docker load < frr-zero-setup-r2.tar
```

### 5. Launch the Virtual Topology
Fire up the multi-subnet isolated framework in the background:
```bash
docker compose up -d
```

---

## Verifying and Accessing the Lab

### 1. Confirm Active Execution States
Run a quick process audit to ensure both network routing devices are successfully initialized and running:
```bash
docker ps
```
Both `frr-router1` and `frr-router2` must report an active status state of **`Up`**.

### 2. Access the Routers Over SSH
Both nodes host a live background OpenSSH daemon server. Connect directly from your host shell using the following default administrative credentials:
* **Connect to Router 1:** `ssh root@172.30.0.11`
* **Connect to Router 2:** `ssh root@172.30.0.12`
* **Universal Password:** `rootpassword`

### 3. Access the FRR Routing Core Shell
Once inside a router's secure shell prompt, enter the native FRR interactive configuration console:
```bash
vtysh
```
From here, you can execute network diagnostic inspect strings such as `show ip route` or `show ip ospf neighbor` to analyze live routing state data.
