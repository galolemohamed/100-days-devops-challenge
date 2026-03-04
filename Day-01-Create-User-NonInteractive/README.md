# Day 1 – Create Linux User with Non-Interactive Shell

## Goal
Create a Linux user named `ammar` with a non-interactive shell.

## Steps Taken
```bash
sudo useradd -s /usr/sbin/nologin ammar
getent passwd ammar

## Outcome / Validation

User ammar created successfully

Non-interactive shell verified

su - ammar
# Result: su: Authentication failure / account not available

## Key Learning Points

useradd -s sets the shell for the user

Non-interactive shell is useful for service/system accounts