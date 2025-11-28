User Access Lifecycle Manager

A Python-based project that simulates a real-world Identity and Access Management (IAM) workflow for onboarding, transferring, and offboarding users. This mirrors the Joiner–Mover–Leaver processes used by IT, IAM, and Security teams in enterprise environments.

What This Project Does

Assigns permissions to new hires based on role (RBAC)

Updates permissions when users change departments or roles

Revokes all access when users leave the company

Writes a complete audit log of all access actions to a JSON file

This project demonstrates core IAM concepts used in identity systems such as Microsoft Entra ID, Okta, and similar platforms.

How It Works

Each user is defined with:

name

status → Joiner, Mover, or Leaver

role → Engineer, HR, Finance, etc.

The system processes each lifecycle state:

Joiner (New Hire)

Assigns role-appropriate permissions

Logs the provisioning event with a timestamp

Mover (Internal Transfer)

Removes old role permissions

Adds new role permissions

Logs the role change and updated access

Leaver (Offboarding)

Removes all permissions

Logs the deprovisioning event for audit purposes

All access activity is written to access_log.json.

IAM Concepts Demonstrated

Role-Based Access Control (RBAC)

Least privilege

Joiner–Mover–Leaver lifecycle management

User provisioning and deprovisioning

Access change auditing and compliance logging

Basic separation of duties

Zero Trust-aligned access logic (explicit grant and removal)

These are foundational practices in identity engineering and identity governance.

Architecture Overview

This is a simple, text-based outline of how the project operates:

main.py reads the list of users and their lifecycle state

It looks up the correct permissions based on role definitions in roles.py

It uses helper functions in utils.py to generate timestamps and write logs

All access changes are written to access_log.json as a basic audit trail

Project Structure
user-access-lifecycle-manager/
│
├── main.py            # Processes Joiner/Mover/Leaver workflow
├── roles.py           # Role-to-permission definitions (RBAC)
├── utils.py           # Timestamp and logging helpers
├── access_log.json    # Auto-generated audit log
└── README.md

How To Use

Modify the users list in main.py to add or change users.

Run the script:

python3 main.py


Review the access actions in the terminal.

Open access_log.json to audit all changes with timestamps.

Example Log Output
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

Why I Built This

I am developing a deeper understanding of identity fundamentals and access governance by simulating how organizations manage user state changes. This project demonstrates skills relevant to:

IAM Analyst

Identity Engineer

Technical Support Engineer (Identity-focused)

Security Analyst (Identity and Access Control)

It shows practical knowledge of identity workflows, RBAC, access automation, and audit-ready logging.
