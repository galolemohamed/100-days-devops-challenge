# SSH Password-less Authentication Setup

## Task

Configure **password-less SSH authentication** from user `thor` on the **jump host** to all application servers using their respective sudo users.

Target servers:

* `stapp01` → user `tony`
* `stapp02` → user `steve`
* `stapp03` → user `banner`

The goal is to allow user **thor** to SSH into these servers **without entering a password**.

---

# Step 1: Switch to the thor User

```bash
sudo su - thor
```

Verify the current user:

```bash
whoami
```

Output:

```
thor
```

---

# Step 2: Check Existing SSH Keys

Check whether SSH keys already exist:

```bash
ls ~/.ssh
```

Expected files:

`id_rsa`
`id_rsa.pub`

If the keys are missing, generate them.

---

# Step 3: Generate SSH Key (if needed)

```bash
ssh-keygen -t rsa
```

Press **Enter** for all prompts to accept the default location and no passphrase.

This generates:


`~/.ssh/id_rsa`
`~/.ssh/id_rsa.pub`

---

# Step 4: Copy SSH Public Key to App Servers

Use `ssh-copy-id` to copy the public key to each server.

### App Server 1

```bash
ssh-copy-id tony@stapp01
```

### App Server 2

```bash
ssh-copy-id steve@stapp02
```

### App Server 3

```bash
ssh-copy-id banner@stapp03
```

You will be prompted for the password **once** for each server.

The command copies the public key into:


`~/.ssh/authorized_keys`

on the remote servers.

---

# Step 5: Test Password-less SSH Login

Test SSH access to each server.

Example:

```bash
ssh tony@stapp01
```

If configured correctly, the login will succeed **without asking for a password**.

Repeat for the remaining servers:

```bash
ssh steve@stapp02
ssh banner@stapp03
```

---

# How It Works

SSH key authentication works using a **public/private key pair**:

* `id_rsa` → private key (kept on the jump host)
* `id_rsa.pub` → public key (copied to remote servers)

The public key is stored in:

`~/.ssh/authorized_keys`

on each server. When SSH login is attempted, the server verifies the private key from the client against the stored public key.

---

# Result

User `thor` on the **jump host** can now connect to all application servers without entering a password:

```
thor@jump-host → stapp01 (tony)
thor@jump-host → stapp02 (steve)
thor@jump-host → stapp03 (banner)
```

This setup improves **automation, security, and efficiency** for remote server management.
