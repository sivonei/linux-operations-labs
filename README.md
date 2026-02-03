# Linux Operations Labs

A collection of Linux troubleshooting labs focused on
problem identification and operational best practices.

---

## Labs

<details>
<summary>Lab 01 — Systemd Troubleshooting / systemd service failures </summary>

### Scenario

A service fails to start, crashes, or enters a restart loop after a deploy
or system change (configuration update, package upgrade, or restart).

### Goal

Identify which service failed and determine the root cause
using systemd state and journal logs, before attempting any fix.

### Troubleshooting Flow

1.1- Check overall system state

```bash
systemctl is-system-running
```

Purpose: Confirms whether systemd considers the system healthy or degraded.
Use this to determine if the issue is isolated or system-wide.

---

1.2- List failed units

```bash
systemctl --failed
```

Purpose: Shows failed units managed by systemd.
Focus on `.service` units and investigate dependency-related failures first.

---

1.3- Inspect service status

```bash
systemctl status <service>
```

Purpose: Displays service state, exit code, and recent log entries.
Often reveals the failure reason without requiring full journal output.

Example:

```bash
systemctl status nginx
```

---

1.4- Read service-specific logs

```bash
journalctl -u <service> --since "10 min ago"
```

Purpose: Reads recent logs for the service and helps identify the first fatal error.
Always filter by time to reduce noise.

Example:

```bash
journalctl -u nginx --since "10 min ago"
```

---

1.5- Inspect the unit definition

```bash
systemctl cat <service>
```

Purpose: Shows how the service is defined (ExecStart, User, WorkingDirectory, dependencies).
Useful to detect misconfigurations introduced during deploys or changes.

Example:

```bash
systemctl cat nginx
```

---

1.6- Escalate to system-wide logs (if needed)

```bash
journalctl -xe
```

Purpose: Use only when service-level logs are insufficient or when the failure involves
other subsystems (network, mount, permissions, SELinux/AppArmor).

---

### Notes

* Never restart a service before reviewing its status and logs
* Restarting may hide the original failure evidence
* This lab focuses on identification, not correction


</details>

<details>
<summary>Lab 02 — Disk, inode, deleted-open files</summary>

(placeholder)

</details>

<details>
<summary>Lab 03 — DNS / resolution / routing</summary>

(placeholder)

</details>

<details>
<summary>Lab 04 — Permissions / ACL</summary>

(placeholder)

</details>

<details>
<summary>Lab 05 — Performance (CPU / Memory / I/O)</summary>

(placeholder)

</details>

<details>
<summary>Lab 06 — TLS / Certificate expiration</summary>

(placeholder)

</details>
