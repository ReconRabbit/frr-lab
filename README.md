# FRR Multi-Subnet Routing Lab (OSPF & SSH Enabled)

This repository contains a pre-configured 2-router network laboratory using FRRouting (FRR) running over isolated Docker networks. OpenSSH is pre-installed on both routers for terminal access.

## Topology Map
* **Router 1 Local Subnet:** 10.1.0.0/24 (Router IP: 10.1.0.11)
* **Router 2 Local Subnet:** 10.2.0.0/24 (Router IP: 10.2.0.12)
* **Transit Backbone Subnet:** 172.30.0.0/24 (R1: 172.30.0.11 | R2: 172.30.0.12)

---

## Student Setup Instructions

Follow these steps exactly to import and launch the lab environment on your machine. **Do not attempt to extract or unzip the downloaded `.tar` files.**

### 1. Clone this Repository
Open a terminal on your computer and clone the tracking infrastructure:
```bash
mkdir frr-lab
Download the docker-compose.yml and the two tar.gz file's in the release pages
```

### 2. Download the Pre-Compiled Router Images and unzip
Navigate to the **Releases** section on the right side of this GitHub page and download both master image files into your project directory:
* `frr-lab-ready-r1.tar.gz`
* `frr-lab-ready-r2.tar.gz`
* 'gunzip frr-lab*'

### 3. Load the Images into Docker
Run the following commands in your terminal to register the master blueprints natively inside your local Docker engine:
```bash
docker load < frr-lab-ready-r1.tar
docker load < frr-lab-ready-r2.tar
```

### 4. Fire Up the Topology
Launch the isolated container network space in detached background mode:
```bash
docker compose up -d
```

### 5. Accessing the Routers
You can now securely shell into either routing container directly from your host machine terminal:
* **Connect to Router 1:** `ssh root@172.30.0.11`
* **Connect to Router 2:** `ssh root@172.30.0.12`
* **Password:** `rootpassword`

Once logged into the Linux prompt via SSH, type **`vtysh`** to access the live FRR dynamic routing configuration command line interface.
