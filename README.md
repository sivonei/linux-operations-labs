# Linux Operations Labs

A collection of Linux troubleshooting labs focused on
problem identification and operational best practices.

---

## Labs

<details>
<summary>Lab 01 — systemd service failures (deploy / change)</summary>

### Scenario
A service fails to start or crashes after a deploy or system change.

### Goal
Identify which service failed and determine the root cause
using systemd and journal logs.

### Troubleshooting Flow
1. systemctl is-system-running
2. systemctl --failed
3. systemctl status &lt;service&gt;
4. journalctl -u &lt;service&gt; --since "10 min ago"
5. systemctl cat &lt;service&gt;
6. journalctl -xe (if needed)

### Notes
- Do not restart services before checking logs
- Focus on identification, not correction

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
