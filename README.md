
## Safety

Read [`docs/SAFETY.md`](docs/SAFETY.md) before running anything. Never bridge a VM to `wlan0`/`enp*`. Never transmit on licensed cellular bands. All lab subnets isolated from home network; canary rule triggers on any leak attempt.

## Reproduce

See `journal/` for step-by-step phases. The environment is fully reproducible: `virsh net-define` from `networks/*.xml`, `docker compose up` from `docker/*`, VM disks re-downloadable.

## Reports

- [`journal/2026-11-16-soc-baseline-report.md`](journal/2026-11-16-soc-baseline-report.md) — Wazuh SOC baseline
- [`journal/2026-11-16-vsftpd-backdoor.md`](journal/2026-11-16-vsftpd-backdoor.md) — Metasploitable root via vsftpd/1524

## License

Private lab. Not for redistribution.# CyberLab Pro

A reproducible, isolated cybersecurity research lab on CachyOS (Arch-based), built on KVM/QEMU.

## Status

- **Phase 1 — Virtualization Foundation** ✅ Complete
- **Phase 2 — Red Team** ✅ Complete (Kali + Metasploitable + DVWA + Juice Shop)
- **Phase 3 — Blue Team / SOC** ✅ Complete (Wazuh 4.9, 301 alerts indexed)
- **Phase 4 — Android Security** ⏳ Pending
- **Phase 5 — 5G Core** ⏳ Pending
- **Phase 6 — Location Tracking** ⏳ Pending
- **Phase 7 — SDR Research** ⏳ Pending

> **Note:** Active development paused 2026-11-17 for hardware RAM repair (soldered DIMM failure confirmed via memtester). Backup archived under `backups/`.

## Architecture

Seven isolated libvirt networks:

| Network | Subnet | Purpose |
|---|---|---|
| lab-mgmt | 10.10.10.0/24 | Analyst workstation (Kali, NAT to internet) |
| lab-victim | 10.10.20.0/24 | Vulnerable targets (Metasploitable, DVWA, Juice Shop) |
| lab-soc | 10.10.30.0/24 | Wazuh manager |
| lab-5gcore | 10.10.40.0/24 | Open5GS / UERANSIM |
| lab-app | 10.10.50.0/24 | Traccar + Android emulator |
| lab-cellular | 10.10.60.0/24 | DragonOS / SDR |
| lab-tap | 10.10.70.0/24 | Observability mirror |

## Layout
