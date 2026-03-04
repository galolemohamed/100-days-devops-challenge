# Day 2 – Create Linux User with Expiry Date

## Goal
Create a Linux user named `ammar` with account expiry date **2026-12-07**.

## Steps Taken
```bash
sudo useradd -e 2026-12-07 ammar
sudo chage -l ammar

## Outcome / Validation

User ammar created with expiry 2026-12-07

Verified with sudo chage -l ammar

## Key Learning Points

useradd -e sets account expiration

chage -l confirms expiry