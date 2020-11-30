# 🌈 Regenbogen
🌈 is better than ☁️

This page presents my "personal cloud" of self-hosted applications. It currently runs on a Raspberry Pi 4 and a custom mini-ITX server, backed-up by a 1 Gbit/s LAN network and a 1 Gbit/s FTTH uplink.

## Hosts

**Naming convention:** hosts are named in German after [colors of the rainbow](https://en.wikipedia.org/wiki/ROYGBIV) and the [Rainbow Books series of the US NCSC](https://en.wikipedia.org/wiki/Rainbow_Series).

### Rot

Rot runs network-related applications alongside my ISP router. It mainly serves as a DNS resolver, ad-blocker and as an internet-facing gateway to services hosted on Grün.

- Raspberry Pi 4 4GB
- 32 GB SanDisk Ultra MicroSD card (Class 10, UHS-I, A1)
- Cooler Master Pi Case 40

### Grün

Grün houses my data on a Btrfs RAID1 filesystem and hosts my personal services.

- ASRock J4125-ITX (4 cores @ 2GHz)
- 2x4 GB DDR4-2400 Crucial CT2K4G4SFS824A
- 500 GB Samsung 860 EVO SSD
- 3x8 TB shucked Western Digital Elements (1x WD80EMAZ and 2x WD80EDAZ)
- Fractal Design Node 304
- Be Quiet! Straight Power 11 450W Gold

## Provisioning and configuration management

Hosts are running Arch Linux (ARM) and are provisioned manually:
  - Partitions setup
  - Network configuration
  - User creation and sysadmin software installation

The rest of their configuration is managed through Ansible.

## Software

| Host  | Software                                                                  | Comment                                                                                                                                 |
|------ |-------------------------------------------------------------------------- |---------                                                                                                                                |
| *     | NGINX                                                                     | Reverse HTTP(S) proxy for all web applications                                                                                          |
| *     | Prometheus Node Exporter                                                  | Hardware and OS monitoring                                                                                                              |
| Rot   | [dnscrypt-proxy](https://github.com/DNSCrypt/dnscrypt-proxy)              | DNS resolver with support for [Anonymized DNSCrypt](https://github.com/DNSCrypt/dnscrypt-protocol/blob/master/ANONYMIZED-DNSCRYPT.txt)  |
| Rot   | [AdGuard Home](https://github.com/AdguardTeam/AdGuardHome/)               | Ads & trackers blocking DNS resolver (~PiHole developed in Go), set up to use dnscrypt-proxy as upstream                                |
| Rot   | Wireguard                                                                 |                                                                                                                                         |
| Grün  | [Step Certificates](https://github.com/smallstep/certificates)            | Local certificate authority / PKI used for Client Authentication and local TLS sessions                                                 |
| Grün  | [restic](https://github.com/restic/restic)                                | Some data is backed up in the cloud!                                                                                                    |
| Grün  | Prometheus                                                                |                                                                                                                                         |
| Grün  | Grafana                                                                   |                                                                                                                                         |
| Grün  | [Bitwarden](https://github.com/dani-garcia/bitwarden_rs)                  |                                                                                                                                         |
| Grün  | Gitea                                                                     |                                                                                                                                         |
| Grün  | Transmission                                                              |                                                                                                                                         |
| Grün  | Samba                                                                     |                                                                                                                                         |
