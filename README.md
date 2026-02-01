# Ansible Automation (PostgreSQL DBA)

This folder contains beginner-friendly Ansible automation examples focused on
PostgreSQL DBA tasks on Rocky/RHEL-based Linux systems.

## Structure
- `ansible.cfg` - local Ansible configuration (inventory, defaults)
- `inventory/hosts.ini` - inventory of lab servers
- `playbooks/` - playbooks for installing and configuring PostgreSQL

## Playbooks

### install_postgresql17_rocky.yml
Installs and configures PostgreSQL 17 from the official PGDG repository:
- disables default PostgreSQL module (avoids package conflicts)
- installs PostgreSQL 17 packages
- initializes the database cluster
- configures `listen_addresses='*'`
- sets up `pg_hba.conf` for password auth (LAB)
- sets postgres password to `postgres`
- enables and starts the service
- opens firewall port 5432 (if firewalld is running)

> Note: `0.0.0.0/0` in pg_hba.conf is LAB ONLY. Restrict CIDRs in real environments.

## Usage

1) Verify SSH access to the target node(s):
```bash
ansible -m ping dbservers
