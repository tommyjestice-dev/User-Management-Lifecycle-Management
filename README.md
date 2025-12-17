# User Access Lifecycle Manager

A Python-based project that simulates a real-world Identity and Access Management (IAM) workflow for onboarding, transferring, and offboarding users. This mirrors the Joiner–Mover–Leaver processes used by IT, IAM, and Security teams in enterprise environments.

## What This Project Does

- Assigns permissions to new hires based on role (RBAC)
- Updates permissions when users change departments or roles
- Revokes all access when users leave the company
- Writes a complete audit log of all access actions to a JSON file

This project demonstrates core IAM concepts used in identity systems such as Microsoft Entra ID, Okta, and similar platforms.

## How It Works

Each user is defined with:
- `name`
- `status` → Joiner, Mover, or Leaver
- `role` → Engineer, HR, Finance, etc.

### Joiner (New Hire)
- Assigns role-appropriate permissions
- Logs the provisioning event with a timestamp

### Mover (Internal Transfer)
- Removes old role permissions
- Adds new role permissions
- Logs the role change and updated access

### Leaver (Offboarding)
- Removes all permissions
- Logs the deprovisioning event for compliance

All access activity is written to `access_log.json`.

## IAM Concepts Demonstrated

- Role-Based Access Control (RBAC)
- Least privilege
- Joiner–Mover–Leaver lifecycle management
- Provisioning and deprovisioning
- Access change auditing
- Separation of duties
- Zero Trust–aligned access logic

## Architecture Overview

A simple breakdown of how the components interact:

- `main.py` reads the list of users and their lifecycle state
- It checks role-based permissions in `roles.py`
- It uses helper functions in `utils.py` for timestamps and logging
- All changes are written to `access_log.json`

## Project Structure

- main.py — Processes Joiner/Mover/Leaver workflow  
- roles.py — Role-to-permission definitions (RBAC)  
- utils.py — Timestamp and logging helpers  
- access_log.json — Auto-generated audit log  
- README.md  

## How To Use

1. Modify the `users` list in `main.py` to add or adjust users.
2. Run the script:

python3 main.py

3. View terminal output for processed changes.
4. Open `access_log.json` to review all logged events.

## Example Log Output

[
  {
    "name": "Tommy",
    "status": "Joiner",
    "role": "Engineer",
    "permissions": [
      "access_repo",
      "deploy_code"
    ],
    "timestamp": "2025-07-16, 21:41:24"
  }
]

## Why I Built This

This project strengthens my understanding of identity lifecycle management and IAM fundamentals. It demonstrates practical skills relevant to roles such as:

- IAM Analyst
- Identity Engineer
- Technical Support Engineer (Identity-focused)
- Security Analyst (Identity and Access Control)

It reflects my ability to automate identity workflows, implement RBAC logic, and produce audit-ready access logs.
