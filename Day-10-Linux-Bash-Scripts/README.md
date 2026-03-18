# Day 10 - KodeKloud 100 Days Of DevOps Challenge 

## Task Overview
In Day 10, I worked on automating website backups using a Bash script. This task simulates a real-world production scenario where backups are essential for reliability and disaster recovery.

---

##  Objectives
- Create a Bash script to automate backups
- Archive a website directory
- Store the backup locally
- Transfer the backup to a remote storage server
- Configure passwordless SSH authentication

---

##  Script Details

**Script Name:** `blog_backup.sh`

### What the Script Does:
1. Creates a zip archive of the website directory:
`/var/www/html/blog`

2. Saves the archive locally:
`/backup/xfusioncorp_blog.zip`

3. Copies the backup to a remote storage server:
`ststor01:/backup/`


---

## Key Concepts Learned
- Bash scripting automation
- File compression using `zip`
- Secure file transfer using `scp`
- SSH key-based authentication (passwordless login)
- Linux file permissions and directory management

---

## SSH Key Setup (Passwordless Authentication)

To avoid password prompts during file transfer:

`ssh-keygen`
`ssh-copy-id natasha@ststor01`

### Script

```bash

#!/bin/bash

BACKUP_NAME="xfusioncorp_blog.zip"
SOURCE_DIR="/var/www/html/blog"
LOCAL_BACKUP="/backup/$BACKUP_NAME"
REMOTE_USER="natasha"
REMOTE_HOST="ststor01"
REMOTE_DIR="/backup/"

zip -r $LOCAL_BACKUP $SOURCE_DIR
scp $LOCAL_BACKUP $REMOTE_USER@$REMOTE_HOST:$REMOTE_DIR


```

### Outcome

Successfully automated the backup process

Ensured secure, passwordless file transfer

Gained hands-on experience with real-world DevOps tasks

### Reflection

This task reinforced the importance of automation in managing production systems. Even simple scripts can significantly improve efficiency and reliability in DevOps workflows.
