# Day 08 – Ansible Installation (DevOps 100 Days Challenge)

## Task

During the DevOps team meeting, the Nautilus team decided to start testing **Ansible** for automation and configuration management.

The task was to **install Ansible version 4.7.0 on the Jump Host using `pip3` only**, and ensure the **Ansible binary is available globally so all users on the system can run Ansible commands**.

---

# Environment

* Controller Node: **Jump Host**
* Package Manager: **pip3**
* Target Version: **Ansible 4.7.0**

---

# Step 1 – Verify Python and pip3

First, confirm that Python3 and pip3 are installed on the system.

```bash
python3 --version
pip3 --version
```

If pip3 is not installed, install it:

```bash
sudo yum install -y python3-pip
```


---

# Step 2 – Install Ansible 4.7.0 using pip3

Install the required version of Ansible using pip3:

```bash
sudo pip3 install ansible==4.7.0
```

This installs Ansible globally on the system.

---

# Step 3 – Verify Ansible Installation

Check whether Ansible is installed successfully:

```bash
ansible --version
```

Expected output should display something similar to:

```
ansible [core 2.11.x]
ansible 4.7.0
```

---

# Step 4 – Verify Global Availability

Ensure the Ansible binary is accessible system-wide:

```bash
which ansible
```

Expected output:

```
/usr/local/bin/ansible
```

Since `/usr/local/bin` is part of the system PATH, **all users on the server can run Ansible commands**.

---

# Step 5 – Test with Another User

Switch to another user to confirm global access:

```bash
su - thor
ansible --version
```

If the version is displayed successfully, Ansible is available globally.

---

# Result

* Ansible **version 4.7.0** successfully installed using **pip3**.
* Installation performed on the **Jump Host (Ansible Controller)**.
* The **Ansible binary is globally accessible** to all users on the system.



