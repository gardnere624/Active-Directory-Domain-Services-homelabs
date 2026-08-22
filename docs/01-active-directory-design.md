# Active Directory Domain Design

## Objective

Build a Windows Active Directory domain that centrally manages users, administrative accounts, security groups, servers, and workstations.

The environment was designed to simulate a small organization with separate Finance, IT, and Production departments.

## Lab Environment

| System | Purpose |
|---|---|
| DC01 | Domain controller running Active Directory Domain Services and DNS |
| MGMT01 | Administrative workstation with RSAT |
| PC01 | Domain-joined Windows client used for testing |
| Proxmox | Virtualization platform hosting the lab |
| home.lab | Active Directory domain |

## Server Roles

### DC01

DC01 provides:

- Active Directory Domain Services
- Domain authentication
- Centralized directory management
- DNS name resolution for the domain
- Group Policy processing

### MGMT01

MGMT01 is a dedicated administrative workstation used to manage the domain remotely with:

- Active Directory Users and Computers
- Group Policy Management
- DNS Manager
- Other RSAT management tools

### PC01

PC01 is a domain-joined Windows workstation used to:

- Test domain user authentication
- Validate Group Policy
- Test security-group permissions
- Simulate an employee computer

## Organizational Unit Design

The following OU structure was created:

```text
home.lab
├── Accounts
│   ├── Admin
│   ├── Finance
│   ├── IT
│   └── Production
├── Groups
├── Servers
└── Workstations
