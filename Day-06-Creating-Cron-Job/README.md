# Day 6 – Creating a Cron Job

## Task Overview
The Nautilus system administrators wanted to test automated scheduling before deploying scripts across the app servers in Stratos Datacenter.

The objective was to install the cron service and configure a scheduled task on all application servers.

---

## Objective
- Install the **cronie** package on all Nautilus app servers.
- Start and enable the `crond` service.
- Create a cron job for the **root** user.
- The cron job should run every **5 minutes** and write the text `hello` into `/tmp/cron_text`.

---

## Servers Used
The following application servers were configured:

- `stapp01`
- `stapp02`
- `stapp03`

The same configuration steps were performed on each server.

---

## Implementation Steps

### 1. Install Cronie

Install the cron package on each server.

`sudo yum install cronie -y`

### 2. Start the Cron Service
`sudo systemctl start crond`

### 3. Enable Cron at Boot
`sudo systemctl enable crond`

### 4. Create the Root Cron Job

Edit the root crontab:

`sudo crontab -e`

### 5. Verify the Cron Job
`sudo crontab -l`

### Expected output:

`*/5 * * * * echo hello > /tmp/cron_text`

### 6. Confirm Execution

After a few minutes verify the output file:

`cat /tmp/cron_text`

### Expected output:

`hello`

### Result

Cronie installed successfully on all application servers.

`crond` service started and enabled.

Cron job created for the root user.

The job runs every 5 minutes and writes `hello` into `/tmp/cron_text`.

### Key Concepts Learned

Installing and managing cron services

Creating scheduled tasks using `crontab`

Automating administrative tasks in Linux

Applying the same configuration across multiple servers