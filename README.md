# Linux Net-Tools: NetSpy & Shield

A collection of custom Bash scripts for local network reconnaissance and system-level DNS traffic blocking.

##  Shield v1.0 (DNS Sinkhole)
A lightweight command-line utility to toggle a system-wide DNS blocklist by manipulating the `/etc/hosts` file.

**Features:**
* Blocks designated domains system-wide.
* Flushes DNS cache automatically via `systemd-resolved`.
* Easy toggle (`on`/`off`) for rapid deployment.

## Requirements
* Linux environment (Tested on Linux Mint/Ubuntu)
* Root (`sudo`) privileges
