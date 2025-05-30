# Ufw-Configs


## UFW Firewall Configuration Task

This task documents how I configured and tested basic firewall rules using **UFW** (Uncomplicated Firewall) on Linux.

---

## 🎯 Objective
Configure and test firewall rules to allow or block traffic using UFW.

---

## 🧰 Tools Used
- UFW (Linux)
- Telnet (for testing)
- Linux Terminal

---

## 📋 Steps Done (in order)

### 1️⃣ Checked if UFW is installed and running
```bash
sudo ufw status
```

If not installed:
```bash
sudo apt install ufw
```

### 2️⃣ Enable UFW
```bash
sudo ufw enable
```

### 3️⃣ List Current Firewall Rules
```bash
sudo ufw status numbered
```
📸 Screenshot: `screenshots/step-3-ufw-status.png`

### 4️⃣ Block Port 23 (Telnet)
```bash
sudo ufw deny 23
```
📸 Screenshot: `screenshots/step-4-block-port-23.png`

### 5️⃣ Test the Telnet Block
If Telnet is not installed:
```bash
sudo apt install telnet
```

Then test the blocked port:
```bash
telnet localhost 23
```
Expected result: **Connection refused**

📸 Screenshot: `screenshots/step-5-test-telnet.png`

### 6️⃣ Ensure SSH (Port 22) is Allowed
```bash
sudo ufw allow 22
```
📸 Screenshot: `screenshots/step-6-allow-ssh.png`

### 7️⃣ Remove Telnet Rule to Restore Original State
First, list rules with numbers:
```bash
sudo ufw status numbered
```

Then delete the Telnet rule (example shown as rule 2):
```bash
sudo ufw delete 2
```
📸 Screenshot: `screenshots/step-7-restore-state.png`

---

## 🧠 Summary: How Firewall Filters Traffic
* UFW acts as a gatekeeper for network traffic.
* **Allow rules** open access to specific ports/services.
* **Deny rules** block insecure or unwanted access (e.g., Telnet).
* Rules are tested manually to confirm they work.
* Temporary test rules (like Telnet block) should be removed after testing.
