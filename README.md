# Shield V3.0 - Hardcore Focus & DNS Blocker

Shield is a system-level utility for Linux that manages DNS sinkholing via the `/etc/hosts` file. Version 3.0 introduces a deterministic state-based architecture.

## 🚀 Key Features (V3.0)
* **Deterministic State Management:** Uses a permanent base file (`/etc/hosts.base`) to prevent state corruption.
* **Inheritance-Based Blocking:** Focus mode automatically inherits all adult-site blocks from the local cache.
* **Process Tracking:** Uses unique Timer IDs to prevent race conditions from overlapping background timers.
* **File Immutability:** Leverages `chattr +i` to prevent manual bypasses during focus sessions.

## 🛠 Commands
* `sudo shield update`: Builds the offline adult-site cache.
* `sudo shield on`: Activates global protection.
* `sudo shield focus [minutes]`: Initiates a hardcore lock.
* `sudo shield off`: Restores the system to its base state.

