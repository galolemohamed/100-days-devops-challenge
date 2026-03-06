# Day 04 – Script Execution Permissions

## Overview
Today I worked on a Linux file permissions task in the Stratos Datacenter environment. The goal was to ensure that a Bash script created by the system administration team could be executed properly by all users on the server.

During the exercise, I connected to **App Server 1** and inspected the permissions of the script located at `/tmp/xfusioncorp.sh`. The file initially had no permissions assigned, which prevented it from being executed.

## What I Did
First, I verified the current permissions of the script using the `ls -l /tmp/xfusioncorp.sh` command. The output showed that the file had no read, write, or execute permissions.


Since the script needed to be executable by all users, I used `sudo` to modify the file permissions and grant execute access.


`sudo chmod 755 /tmp/xfusioncorp.sh`

This command provided:

Read, write, and execute permissions for the owner

Read and execute permissions for the group

Read and execute permissions for others

After applying the changes, I confirmed the new permissions:
`-rwxr-xr-x 1 root root 40 Mar 6 /tmp/xfusioncorp.sh`

Key Takeaways

Through this task, I strengthened my understanding of Linux file permission management. I learned how execution permissions affect scripts and how to correctly apply permissions so that scripts can run while maintaining proper security practices.