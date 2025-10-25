# TCOM535 Individual Project – Network Automation and Management

## 1. Objective
The objective of this project is to simulate a network of four VyOS routers running as Docker containers and automate their configuration using Ansible.  
The goal is to demonstrate how network automation can simplify management tasks by adding new static routes automatically and validating routing information before and after the change.

---

## 2. Project Design Overview
- **Topology:** Four VyOS routers connected through Docker networks.
- **Management Plane:** A dedicated Docker network allows Ansible to reach each router via SSH.
- **Data Plane:** Separate inter-router networks provide routing paths for data traffic.
- **Automation:** Ansible is used to:
  - Apply baseline configuration (hostname, SSH, users).
  - Push initial static routes for connectivity.
  - Add a new static route to a router that is not directly connected to another router.
- **Verification:** Routing tables (`show ip route`) are checked before and after configuration changes.

---

## 3. Requirements
To run this project successfully, the following components are needed:
- Docker and Docker Compose installed.
- VyOS image (community version).
- Ansible installed with the `vyos.vyos` collection.
- Python 3 environment.
- SSH key configured for Ansible to access routers.

---

## 4. Project Deliverables
1. **Topology Setup**
   - `docker-compose.yml` (or `containerlab` file) defining 4 VyOS routers and networks.
2. **Automation Files**
   - Ansible inventory: `inventories/hosts.ini`
   - Group variables: `group_vars/routers.yml`
   - Roles: `roles/baseline/` and `roles/routes/`
   - Playbooks:
     - `baseline.yml`
     - `routes_init.yml`
     - `route_change.yml`
     - `verify.yml`
3. **Validation Artifacts**
   - Command outputs: `outputs/before/` and `outputs/after/` folders containing routing information.
4. **Demo Video**
   - Short video showing the automation in action (before/after route validation).


## 5. Expected Outcome
By the end of this project:
- A fully functional 4-router VyOS topology will run in Docker.
- Ansible will automatically configure routers and manage routing changes.
- The project will demonstrate how automation reduces manual network management effort.

