# Liuer Panel

[![Version](https://img.shields.io/badge/version-2.5.35-blue.svg)](https://github.com/liuer-net/liuer-panel/releases)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)

A lightweight CLI-based web server control panel for Linux servers. Manage websites, databases, SSL, PHP versions, backups, and more — all from your terminal.

## Supported OS

| OS | Version |
|---|---|
| AlmaLinux | 8, 9, 10 |
| Ubuntu | 20.04, 22.04, 24.04 |

## What gets installed

**Default (required):**
- Nginx
- PHP 8.2-FPM
- MariaDB
- Certbot (Let's Encrypt SSL)

**Optional (you choose during install):**
- PHP 5.6 / 7.4 / 8.0 / 8.2 / 8.3 (multi-version, can also add later)
- PostgreSQL
- Redis **or** Memcached (choose one)
- Fail2ban
- phpMyAdmin

## Installation

```bash
curl -fsSL https://raw.githubusercontent.com/liuer-net/liuer-panel/main/liuer-panel.sh -o liuer-panel.sh
bash liuer-panel.sh --install
```

The installer will guide you through three optional sections:

| Section | Selection |
|---|---|
| **PHP versions** | Multi-select (e.g. `2 4` for PHP 7.4 + 8.2) |
| **Database** | Single-select (PostgreSQL or skip) |
| **Cache** | Single-select (Redis or Memcached) |
| **Fail2ban** | Yes / No |
| **phpMyAdmin** | Yes / No |

> PHP 8.2 and MariaDB are always installed by default.  
> Additional PHP versions can be added at any time via `liuer` → **PHP Manager**.

After installation, type `liuer` to open the management menu.

## Usage

```bash
liuer                # Open management menu
liuer update         # Update to latest version
liuer check-update   # Check if a new version is available
liuer version        # Show current version
liuer help           # Show help
```

## Features

### Website Management
- Create PHP / Laravel / WordPress / Static sites
- Auto-generate Nginx config with security headers
- SSL via Let's Encrypt (auto-renewal included) — install/renew anytime per site
- Switch PHP version per site
- Upload & timeout settings per site (`client_max_body_size`, `fastcgi_read_timeout`, `upload_max_filesize`, `memory_limit`, etc.)
- View site details (PHP socket, SSL expiry, DB info, framework detection)
- Lock / Unlock site
- SFTP user management — auto or manual mode

### Database
- MySQL / MariaDB / PostgreSQL support
- Auto-generate database name, user, and password
- Passwords encrypted before storage

### Cache
- Flush Redis / Memcached / PHP Opcache individually or all at once

### Security
- Firewall management (firewalld on AlmaLinux, UFW on Ubuntu)
- Malware scan with ClamAV (per domain or full scan)
- Fail2ban management

### Backup & Restore
- Backup site files + database per domain
- One-command restore

### PHP Manager
- List installed PHP versions
- Install / remove PHP versions
- Restart PHP-FPM

### System
- Start / Stop / Restart / Enable / Disable any service
- View status of all services
- Install extra services (Redis, Memcached, PostgreSQL, Fail2ban, ClamAV, Certbot)
- Hardware & system info (CPU, RAM, disk, network interfaces, uptime)
- Disk benchmark — sequential read/write speed test via `dd`

### Updates
- `liuer update` — pulls latest version from GitHub with auto-rollback on failure
- Update individual services (Nginx, PHP, MySQL/MariaDB, Redis, Memcached)
- Full system package upgrade

## Security Notes

- phpMyAdmin is restricted to `127.0.0.1` only (access via SSH tunnel)
- Destructive actions require typing `CONFIRM` to proceed

## License

MIT
