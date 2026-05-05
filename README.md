# Shield V3.0 Hardcore Focus & DNS Blocker

Shield is a system-level utility for Linux that manages DNS sinkholing via the `/etc/hosts` file. It blocks adult content system-wide and includes a timed focus mode that locks distracting sites until the timer expires.

## How It Works

Shield maintains three files:

- `/etc/hosts.base` — a clean snapshot of your original hosts file
- `/etc/hosts.adult` — the cached blocklist (Steven Black + your custom sites)
- `/etc/hosts` — the active file Shield writes to

On first run, Shield automatically snapshots your current `/etc/hosts` as the base. All blocking and restoration is done by swapping between these files.

## Requirements

- Linux (Ubuntu / Mint or any `systemd`-based distro)
- `sudo` privileges
- `curl` — for downloading the blocklist
- `e2fsprogs` — for `chattr` (usually pre-installed)
- `resolvectl` — for DNS cache flushing (comes with `systemd-resolved`)

## Installation

```bash
sudo cp shield /usr/local/bin/shield
sudo chmod +x /usr/local/bin/shield
sudo shield update
```

## Commands

| Command | Description |
|---|---|
| `sudo shield update` | Downloads Steven Black's list and builds the offline cache |
| `sudo shield on` | Activates adult content blocking |
| `sudo shield off` | Restores your normal network |
| `sudo shield focus [minutes]` | Locks focus + adult block for N minutes |

## Customization

Open the script and edit the two lists at the top:

```bash
# Extra sites to block on top of Steven Black's list
CUSTOM_BLOCKER=(
    "example-site.com"
)

# Sites to block only during focus mode
FOCUS_SITES=(
    "youtube.com"
    "twitter.com"
)
```

Run `sudo shield update` after changing `CUSTOM_BLOCKER` to rebuild the cache.

## Notes

- Focus mode locks `/etc/hosts` with `chattr +i` — it cannot be manually edited until the timer expires or the system reboots.
- Run `sudo shield update` periodically to keep the blocklist fresh.
- `STATE_FILE` and `TIMER_FILE` live in `/tmp` and do not persist across reboots by design.
