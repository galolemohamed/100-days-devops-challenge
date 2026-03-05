# Day 03: Disable SSH Root Login

## Objective
The goal of this task is to enhance server security by **disabling SSH login for the root user**. This prevents direct root access over SSH, reducing the risk of unauthorized access.

## Steps Completed
1. Accessed the target server via SSH.
2. Edited the SSH configuration file `/etc/ssh/sshd_config`.
3. Set the directive `PermitRootLogin no` to disable root login.
4. Restarted the SSH service to apply changes.
5. Verified that root login is no longer allowed.

## Screenshots
1. **app1-ssh-config-file-root-permit-set-to-yes.jpg** – Original configuration allowing root login.  
2. **app1-ssh-config-file-root-permit-set-to-no.jpg** – Modified configuration disabling root login.  
3. **ssh-disabled.jpg** – Verification that root login is now disabled.  

## Notes
- Always use a non-root user with sudo privileges for SSH access.
- Editing `sshd_config` requires administrative permissions.
- Restart SSH carefully to avoid locking yourself out.
