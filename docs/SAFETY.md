# Safety & Legal Guardrails

## Never
- Transmit on any licensed cellular band without a shielded enclosure AND authorization.
- Bridge a VM to wlan0 / enp* / any physical NIC.
- Run exploits outside 10.10.0.0/16.
- Store real PII or real location data.
- Install offensive tools on the CachyOS host.

## Canary
Host-side nftables rule logs any lab→LAN forwarding attempt:
  sudo nft add rule inet filter forward ip saddr 10.10.0.0/16 \
       ip daddr 192.168.0.0/16 drop log prefix "LAB-CANARY "

Review after each session: journalctl -k | grep LAB-CANARY

## RF (Phase 7 gate)
- RTL-SDR receive-only until Phase 7 checklist is signed off.
- HackRF/USRP only inside a Faraday enclosure.
- Local spectrum regulations reviewed before any TX.
