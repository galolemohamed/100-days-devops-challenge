# Day 09 - MariaDB Troubleshooting 

## Task

The Nautilus application in **Stratos Datacenter** was unable to connect to the database.
The production support team discovered that the **MariaDB service was down on the database server**.

My task was to investigate the issue and restore the database service so the application could reconnect successfully.

---

## Problem

When attempting to start MariaDB, the service failed with the following error:

```
Job for mariadb.service failed because the control process exited with error code.
See "systemctl status mariadb.service" and "journalctl -xeu mariadb.service" for details.
```

This indicated that the service had an **underlying configuration or permission issue** preventing it from starting.

---

## Troubleshooting Steps

### 1. Connect to the Database Server

SSH into the database server.

```bash
ssh peter@stdb01
```

---

### 2. Check MariaDB Service Status

```bash
sudo systemctl status mariadb
```

This confirmed that the service had **failed to start**.

---

### 3. Check Detailed Logs

```bash
sudo journalctl -xeu mariadb.service
```

The logs indicated a problem during the **ExecStartPre phase**, which often relates to **permission issues on the database directory**.

---

### 4. Verify MariaDB Data Directory Ownership

```bash
ls -ld /var/lib/mysql
```

The directory ownership was incorrect.

---

### 5. Fix Directory Permissions

```bash
sudo chown -R mysql:mysql /var/lib/mysql
```

This ensures the MariaDB service has the proper permissions to access its data directory.

---

### 6. Start the MariaDB Service

```bash
sudo systemctl start mariadb
```

---

### 7. Verify the Service is Running

```bash
sudo systemctl status mariadb
```

Expected output:

```
Active: active (running)
```

---

## Result

The MariaDB service started successfully and the **Nautilus application was able to reconnect to the database**.

---

## Key DevOps Lessons

* Always check **service status first**
* Use **journalctl logs** to identify the root cause
* Many service failures are caused by **incorrect file permissions**
* Proper troubleshooting requires **log analysis before making changes**

---

## Commands Summary

```bash
ssh peter@stdb01
sudo systemctl status mariadb
sudo journalctl -xeu mariadb.service
ls -ld /var/lib/mysql
sudo chown -R mysql:mysql /var/lib/mysql
sudo systemctl start mariadb
sudo systemctl status mariadb
```



