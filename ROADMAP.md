# The Linux Engineering Roadmap 2026

> **Master the Kernel, Infrastructure, and the Command Line.**
> A meticulously structured path from fundamental terminal navigation to high-scale production systems engineering.

[![Version](https://img.shields.io/badge/Version-1.0.0-blue.svg)]()
[![License](https://img.shields.io/badge/License-MIT-green.svg)]()
[![Level](https://img.shields.io/badge/Skill-Beginner_to_Expert-orange.svg)]()

---

## 🧭 The Engineering Mindset
Before typing a single command, adopt these industry principles:
* **The Log-First Approach:** If it’s broken, the answer is in the logs. Always.
* **Idempotency:** Write scripts that can run 100 times and yield the same result.
* **Immutable Infrastructure:** Don't treat servers like pets; treat them like cattle (Containerization).
* **Security by Design:** Minimal privilege is the default.

---

## 🥇 Phase 1: The Core Environment (Fundamentals)
*Goal: Develop muscle memory for the Linux Filesystem Hierarchy (FHS).*

### 📂 Navigation & Filesystem Standard
- **Core Commands:** `pwd`, `ls -lah`, `cd -`, `pushd/popd` (The pro's way to jump).
- **Manipulation:** `mkdir -p`, `rm -rf` (use with caution!), `mv`, `cp -rp`.
- **The Tree:** Understanding why `/etc` is for config and `/var` is for data.
- **Paths:** Mastering `.` (current) vs `..` (parent) vs `~` (home).

### 🔐 Permissions & Ownership
- **The rwx Model:** Understanding octal (755) vs symbolic (`u+x`).
- **Identity:** `chmod`, `chown`, `chgrp`.
- **Special Bits:** The dangers and uses of SUID, SGID, and Sticky Bits.

> **💡 Pro-Tip:** Use `tldr <command>` instead of `man` for quick examples when you're in a hurry.

---

## 🥈 Phase 2: Shell Internals & Process Control
*Goal: Understand how the Kernel schedules work and manages resources.*

### ⚡ Shell Execution
- **Pathing:** How `$PATH` determines which binary runs.
- **Environment:** Persisting variables in `.bashrc`, `.zshrc`, or `/etc/environment`.
- **Aliasing:** Creating shortcuts for complex one-liners.

### 🔄 Process Lifecycle
- **Observability:** `ps auxf`, `top`, `htop`, `btop`.
- **Signals:** Sending `SIGTERM (15)` for graceful exits vs `SIGKILL (9)` for forced stops.
- **Priority:** Using `nice` and `renice` to manage CPU "greediness."
- **Job Control:** Moving tasks to the background with `&`, `bg`, and `fg`.

---

## 🥉 Phase 3: The Data Pipeline (Text Processing)
*Goal: High-speed log analysis and data transformation.*

### 🌊 Stream Engineering
- **Redirection:** `>` (overwrite), `>>` (append), `2>&1` (merging error and output streams).
- **Pipes:** Building powerful "one-liners" using `|`.
- **Tee:** Splitting output to both the screen and a file.

### ✂️ The Power Tools
- **The Big Three:** - `grep`: Regex-based searching.
    - `awk`: Field processing (The "Excel" of the command line).
    - `sed`: Non-interactive stream editing.
- **Utility:** `sort -h` (human-readable), `uniq -c`, `cut`, `tail -f` (live log streaming).

---

## 🏗 Phase 4: Modern System Administration
*Goal: Professional-grade service management and governance.*

### 👥 Governance
- **IAM:** `useradd`, `usermod -aG sudo`, managing `/etc/sudoers` via `visudo`.
- **Group Logic:** Creating collaborative directories with shared group access.

### 🔄 Service Orchestration (systemd)
- **Management:** `systemctl enable --now` (start and boot-enable).
- **Deep Inspection:** `journalctl -u <service> -f` for real-time debugging.
- **Customization:** Writing `.service` unit files for your own applications.

---

## 💾 Phase 5: Storage & Filesystems
*Goal: Manage persistence, high availability, and volume scaling.*

### 🏗 Logical Volume Management (LVM)
- **Hierarchy:** Physical Volumes (`pv`) → Volume Groups (`vg`) → Logical Volumes (`lv`).
- **Resizing:** Expanding partitions live without data loss.

### 📂 Filesystem Internals
- **Inodes:** Understanding metadata exhaustion (when disk space is free but you can't save files).
- **Mounting:** `/etc/fstab` configuration for persistent cloud volumes.
- **Swap:** Managing virtual memory for high-load stability.

---

## 🌐 Phase 6: Networking Engineering
*Goal: Debugging the "It's not working" problem (It's usually DNS).*

### 📡 The Stack
- **Modern Suite:** Replacing `ifconfig` with the `ip` route suite (`ip a`, `ip r`, `ip link`).
- **Sockets:** Using `ss -tulpn` to find what's listening on which port.
- **DNS:** `dig`, `nslookup`, and the role of `/etc/resolv.conf`.

### 🛡 Security & Transfer
- **Firewalls:** `nftables` and `firewalld` (or `ufw` for simplicity).
- **SSH:** Hardening `/etc/ssh/sshd_config`, Key-based auth, and `ssh-agent`.
- **Syncing:** Using `rsync -avz` for delta-based file transfers.

---

## 🐳 Phase 7: Containerization (The DevOps Layer)
*Goal: Understanding the primitives of the Cloud.*

### 🏗 The Engine Under the Hood
- **Namespaces:** Process isolation (PID, Network, Mount).
- **Cgroups:** Resource limiting (Memory/CPU throttling).
- **Ulimits:** Setting process limits to prevent "fork bombs."

### 📦 Docker & Runtimes
- **Architecture:** Image layers, storage drivers, and bridge networking.
- **Management:** `docker inspect`, `docker stats`, and volume persistence.

---

## 🧠 Phase 8: Automation (Shell Programming)
*Goal: Stop repeating yourself.*

- **Logic:** Robust `if/else`, `case` statements, and `for/while` loops.
- **Safety:** Using `set -euo pipefail` to make scripts "fail-fast."
- **Functions:** Modularizing code for reusability.
- **Logging:** Writing script outputs to syslog for auditability.

---

## 📈 Mastery Metrics

| Level | Role Equivalent | Skill Milestone |
| :--- | :--- | :--- |
| **L1: Practitioner** | Support Engineer | Can navigate, edit files, and check logs. |
| **L2: Administrator** | SysAdmin | Manages users, systemd, and basic networking. |
| **L3: Engineer** | DevOps / SRE | Troubleshoots kernel, manages LVM, and automates tasks. |
| **L4: Architect** | Systems Architect | Deep kernel tuning, security hardening, and container internals. |

---

## 🧪 The "Break-Fix" Practice Strategy
To reach the top 1%, do not just read. **Do.**

1.  **The Web Stack:** Deploy Nginx + a DB manually. Then automate it.
2.  **The Rescue Mission:** Boot a VM into "Single User Mode" and reset a lost root password.
3.  **The Network Hub:** Set up a Linux machine as a router for other VMs.
4.  **The Log Hunter:** Find the top 10 IP addresses attacking your server from `auth.log` using `awk`.

---

# ⭐ Support the Roadmap
If this guide helped you level up, consider:
- Giving this repo a **Star**
- Forking it to track your progress
- Sharing it with your engineering team

**Maintained by Ajay Dhangar | 2026**
