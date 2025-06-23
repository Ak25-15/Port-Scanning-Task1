# 🔍 Nmap Network Scan Report

This repository contains the results and analysis of a detailed Nmap scan conducted on a local network segment (`10.0.2.0/24`) on **June 23, 2025**. The objective was to identify active hosts, open ports, services, and operating systems for potential enumeration and analysis.

---

## 📋 Scan Summary

- **Scan Tool:** [Nmap 7.95](https://nmap.org)
- **Scan Date:** 2025-06-23
- **Subnet Scanned:** 10.0.2.0/24
- **Live Hosts Detected:** 3
- **Scan Types Used:**
  - Basic SYN scan
  - Service/version detection (`-sV`)
  - OS detection (`-O`)
  - Aggressive scan (`-A`)
  - Specific ports probe (`22, 80, 443`)

---

## 🖥️ Hosts Summary

### 🟢 10.0.2.2 — Likely Windows Host
- **Open Ports:**
  - `135/tcp` - Microsoft Windows RPC
  - `445/tcp` - SMB (Microsoft-ds)
  - `3580/tcp` - NI LabVIEW Service Locator
  - `8080/tcp` - Embedthis HTTP Server
- **Service Detection:**
  - NI Service Locator 1.0.0
  - Embedthis HTTP lib httpd
- **OS Guess:**
  - Possibly running on **VirtualBox/QEMU/Slirp**
  - Detected OS: Windows (Microsoft CPE)
- **Security Note:** SMB signing is enabled but not required

---

### 🟢 10.0.2.3 — Likely DNS Server or Router
- **Open Port:**
  - `53/tcp` - DNSMasq 2.52
- **Service Detection:**
  - DNS version info exposed via `dns-nsid`
- **OS Guess:**
  - Possibly running on **VirtualBox/QEMU/Slirp**, or embedded systems (printer/router)
- **Security Note:** Only port 53 open, others filtered by firewall (likely air-gapped)

---

### 🟢 10.0.2.15 — Linux Host (SSH Server)
- **Open Port:**
  - `22/tcp` - OpenSSH 9.9p2 (Debian)
- **OS Detection:**
  - Linux kernel versions `2.6.32 - 6.2`
  - High confidence in OS as general-purpose Linux
- **Security Note:** HTTP/HTTPS explicitly closed

---

## 🔐 Security Insights

| Host       | OS Detected | Notable Security Info                           |
|------------|-------------|--------------------------------------------------|
| 10.0.2.2   | Windows (Virtual) | SMB signing enabled (not required), redirects |
| 10.0.2.3   | DNSMasq on Embedded | Only DNS exposed, likely hardened |
| 10.0.2.15  | Linux (Debian) | Minimal exposure, SSH only                     |

---

## 🛠️ Commands Used

nmap -sS 10.0.2.0/24
nmap -sV 10.0.2.0/24
nmap -O 10.0.2.0/24
nmap -p 22,80,443 10.0.2.0/24
nmap -A 10.0.2.0/24

---
## 📌 Conclusion

This scan provided insight into the topology and services of a virtualized lab network. Results suggest a mix of emulated Windows and Linux systems with selective service exposure, likely for controlled testing purposes.

---
## ⚠️ Disclaimer

This repository is intended for **educational and research purposes only**. Do not perform unauthorized scans on systems you do not own or have explicit permission to assess.

## 📄 License

This project is open-source under the MIT License.


