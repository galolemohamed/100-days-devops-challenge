# Day 5 – SELinux Installation and Permanent Disablement

## What is SELinux?

**SELinux (Security-Enhanced Linux)** is a Linux security module that provides an additional layer of access control.  
It enforces security policies that restrict how processes and users interact with files and system resources.

SELinux operates in three modes:

| Mode | Description |
|-----|-------------|
| Enforcing | Security policies are actively enforced |
| Permissive | Violations are logged but not blocked |
| Disabled | SELinux is turned off completely |

---

## Solution Steps

### 1. Connect to App Server 1

`ssh tony@appserver1`

Switch to the root user:
`sudo su -`

### 2. Install Required SELinux Packages
`yum install -y selinux-policy selinux-policy-targeted`

### 3. Permanently Disable SELinux

Edit the SELinux configuration file:
`vi /etc/selinux/config`

Locate the following line:

`SELINUX=enforcing`
Modify it to:

`SELINUX=disabled`

Final configuration:

`SELINUX=disabled`
`SELINUXTYPE=targeted`

Reboot.

### Verification

To confirm the configuration change:
`cat /etc/selinux/config`
Expected output:
`SELINUX=disabled`

### Key Takeaways

SELinux adds mandatory access control to Linux systems.

Configuration changes for SELinux require editing `/etc/selinux/config`.

Changes to the SELinux mode take effect only after a reboot.

### Tools Used

Linux Terminal

SSH

vi editor

SELinux configuration
