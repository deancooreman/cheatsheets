# Nmap Cheatsheet

## Target Specification
| Command | Description |
| :--- | :--- |
| `nmap 192.168.1.1` | Scan a single IP |
| `nmap 192.168.1.1 192.168.1.2` | Scan specific multiple IPs |
| `nmap 192.168.1.1-254` | Scan a range of IPs |
| `nmap 192.168.1.0/24` | Scan a full CIDR subnet |
| `nmap scanme.nmap.org` | Scan a domain name |
| `nmap -iL targets.txt` | Scan targets listed in a text file |
| `nmap --exclude 192.168.1.5` | Exclude specific hosts from a scan |

## Host Discovery
| Command | Description |
| :--- | :--- |
| `nmap -sn` | **Ping Scan:** Disable port scan. Only determine if hosts are up. |
| `nmap -Pn` | **No Ping:** Treat all hosts as online; skip discovery phase. |
| `nmap -PS22,80,443` | TCP SYN Ping to specific ports. |
| `nmap -PA22,80,443` | TCP ACK Ping to specific ports. |
| `nmap -PU` | UDP Ping. |
| `nmap -PR` | ARP Ping (most reliable on local networks). |
| `nmap -n` | Never do reverse DNS resolution (speeds up scan). |

## Scan Techniques
| Command | Description |
| :--- | :--- |
| `nmap -sS` | **TCP SYN Scan:** Default stealth scan. Doesn't complete 3-way handshake. |
| `nmap -sT` | **TCP Connect Scan:** Completes the connection (useful if no raw socket access). |
| `nmap -sU` | **UDP Scan:** Scans UDP ports (slow, but necessary). |
| `nmap -sA` | **ACK Scan:** Maps firewall rules (doesn't determine open/closed status). |
| `nmap -sV` | **Service Versioning:** Probes open ports to determine service/version info. |
| `nmap -sC` | **Default Scripts:** Run default NSE scripts. |

## Port Specification
| Command | Description |
| :--- | :--- |
| `nmap -p 80` | Scan port 80. |
| `nmap -p 1-1024` | Scan port range 1 to 1024. |
| `nmap -p 80,443,8080` | Scan specific ports. |
| `nmap -p-` | Scan all 65,535 ports. |
| `nmap -F` | Fast scan (Top 100 ports). |
| `nmap --top-ports 1000` | Scan the most common X ports based on Nmap database. |

## OS and Service Detection
| Command | Description |
| :--- | :--- |
| `nmap -O` | Enable OS detection. |
| `nmap -sV` | Probe open ports to determine service/version info. |
| `nmap -A` | **Aggressive scan:** Enables OS detection, version detection, script scanning, and traceroute. |
| `nmap --osscan-guess` | Guess OS more aggressively if no perfect match is found. |

## Timing and Performance
| Command | Description |
| :--- | :--- |
| `nmap -T0` | **Paranoid:** Intended to bypass IDS (Intrusion Detection Systems). |
| `nmap -T1` | **Sneaky:** Very slow. |
| `nmap -T2` | **Polite:** Consumes less bandwidth; slower than default. |
| `nmap -T3` | **Normal:** Default scan speed. |
| `nmap -T4` | **Aggressive:** Faster; assumes a stable and fast network. |
| `nmap -T5` | **Insane:** Fastest; likely to trigger alarms or drop packets. |

## Output Formats
| Command | Description |
| :--- | :--- |
| `nmap -oN scan.txt` | Normal output to a text file. |
| `nmap -oX scan.xml` | XML output (best for importing into other tools). |
| `nmap -oG scan.grep` | Grepable output. |
| `nmap -oA base_filename` | Output in all three formats (Normal, XML, Grepable). |
| `nmap -v` | Increase verbosity (use `-vv` for more detail). |

## Nmap Scripting Engine (NSE)
| Category | Description |
| :--- | :--- |
| `nmap --script default` | Run default set of scripts. |
| `nmap --script discovery` | Retrieve info from network services (e.g., SMB shares). |
| `nmap --script safe` | Run scripts that are not intrusive. |
| `nmap --script vuln` | Check for known vulnerabilities. |
| `nmap --script exploit` | Attempt to exploit known vulnerabilities. |

## Useful Examples
* **Full Network Inventory:**
  `nmap -sn 192.168.1.0/24`
* **Common Vulnerability Check:**
  `nmap -sV --script vuln 192.168.1.100`
* **Fast Top Port Scan with OS Detection:**
  `nmap -T4 -F -O 192.168.1.1`
* **Scan for Web Server vulnerabilities:**
  `nmap --script http-enum,http-title -p 80,443 192.168.1.1`
* **Bypass Firewalls using Fragmented Packets:**
  `nmap -f 192.168.1.1`
