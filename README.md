```
    _    ____   ___  ____    _    ____       ____  _____ ____          _   _   _ _____ ___  
   / \  / ___| / _ \/ ___|  / \  |  _ \     |  _ \| ____| __ )        / \ | | | |_   _/ _ \ 
  / _ \ \___ \| | | \___ \ / _ \ | |_) |____| | | |  _| |  _ \ _____ / _ \| | | | | || | | |
 / ___ \ ___) | |_| |___) / ___ \|  _ <_____| |_| | |___| |_) |_____/ ___ \ |_| | | || |_| |
/_/   \_\____/ \___/|____/_/   \_\_| \_\    |____/|_____|____/     /_/   \_\___/  |_| \___/ 
```

# asosar-deb-auto

A small Debian setup script for installing common administration tools and granting sudo access to a user.

## What It Installs

- `sudo`
- `net-tools`
- `curl`
- `cockpit`

It also creates a sudoers rule for `asosar` by default:

```text
asosar ALL=(ALL:ALL) ALL
```

The script writes this rule to `/etc/sudoers.d/asosar` and validates it with `visudo` instead of editing `/etc/sudoers` directly.

It also configures NetworkManager so Cockpit can manage ifupdown interfaces by setting this in `/etc/NetworkManager/NetworkManager.conf`:

```ini
[ifupdown]
managed=true
```

The original NetworkManager config is backed up to `/etc/NetworkManager/NetworkManager.conf.bak` before editing.

## Usage

On a fresh Debian system, run as `root`:

```bash
su -
bash install.sh
```

To configure sudo for a different user:

```bash
su -
bash install.sh your_username
```

## Download And Run From GitHub

```bash
curl -fsSL https://raw.githubusercontent.com/asosar2195/asosar-deb-auto/main/install.sh -o install.sh
bash install.sh
```
