# General Commands

| Command | Description | Mode |
| ---   | --- | --- |
| `?`     | Call for help | All modes |
| `enable` | Privileged exec mode| User EXEC Mode |
| `disable` | User exec mode | Privileged EXEC Mode |
| `configure terminal` | Global configuration mode | Privileged EXEC Mode |
| `end` | Go back to privileged exec mode | All configuration submodes |
| `exit` | Go back to the previous mode | All configuration submodes |
| `copy` | copy file to another file | Privileged EXEC Mode |

# Interface / subconfiguration

| Command | Description | Mode
| ---   | --- | --- |
| `interface` | Configuration of a specific interface | Global Configuration Mode |
| `line` | Configuration of an acces method (console, VTY) | Global Configuration Mode |

# Adressing and interface activation

| Command | Description | Mode |
| ---   | --- | --- |
| `ip address` [ip-address] [subnet-mask] | Assings IPv4 address | Interface Configuration Mode |
| `ipv6 address` [ipv6-address/prefix-length] | Assingns IPv6 address | Interface Configuration Mode |
| `no shutdown` | Activates interface | Interface Configuration Mode |
| `ip default-gateway` [ip-address] | Configure default gateway IP on a switch | Global Configuration Mode |

# Device configuration

| Command | Description | Mode |
| ---   | --- | --- |
| `hostname` [name] | Set the device name | Global Configuration Mode |
| `enable secret` [password] | Set a password for priveleged exec mode | Global Configuration Mode |
| `password` [password] | Set a password for acces via console or SSH | Line Configuration Mode |
| `login` | Enforces the authentication requirement to the line | Line Configuration Mode |
| `service password-encryption` | Encrypts all set passwords | Global Configuration Mode |
| `banner motd` [\$message\$] | Configure a banner | Global Configuration Mode |

# Troubleshooting commands

Output filter can be used in combination with any show command.
To enable the filter command, enter a pipe (|) after the show command folowed by a filtering parameter
Filtering parameters:
- `section` Displays the entire section that starts with the filtering expression
- `include` Includes all output lines that match the filtering expression
- `exclude` Excludes all output lines that match the filtering expression
- `begin` Displays all the output lines from a certain point, starting with the line that matches the filtering expression

| Command | Description | Mode |
| ---   | --- | --- |
| `show ip interface brief` | Overview assigned IPv4 addresses | Privileged EXEC Mode |
| `show ipv6 interface brief` | Overview assigned IPv6 addresses | Privileged EXEC Mode |
| `show ip interface` [interface-id] | IPv4 information of a specific interface | Privileged EXEC Mode |
| `show ipv6 interface` [interface-id] | IPv6 information of a specific interface | Privileged EXEC Mode |
| `show startup-config` | Current running configuration | Privileged EXEC Mode |
| `show running-config` | Current startuo configuration | Privileged EXEC Mode |
| `show flash` | Info about the content of the flash memory | Privileged EXEC Mode |
| `show version` | Status of the system hardware and software | Privileged EXEC Mode |
| `show history` | History of entered commands | Privileged EXEC Mode |
| `show mac-address-table` | Content of the MAC address table | Privileged EXEC Mode |
| `show ip ssh` | Version and configuration details SSH | Privileged EXEC Mode |
| `show ip route` | Content of the IPv4 routing table | Privileged EXEC Mode |
| `show ipv6 route` | Content of the IPv6 routing table | Privileged EXEC Mode |
| `show boot` | Current settings of the IOS startup file | Privileged EXEC Mode |
| `show controllers ethernet-controller phy` | Controls duplex, speed and auto-MDIX settings | Privileged EXEC Mode |
| `show cdp neighbours` | List of directly connected Cisco devices |
| `traceroute` [IP address] | Verify path to destination network | Privileged EXEC Mode |
| `ping` [IP address] | Verify layer 3 connectivity to destination | Privileged EXEC Mode |



# System management and boot settings

| Command | Description | Mode |
| ---   | --- | --- |
| `boot system` [path/filename] | Sets the BOOT environment | Global Configuration Mode |
| `sdm prefer dual-ipv4-and-ipv6 default` | Lets a switch work with IPv6 requiers a reload | Global Configuration Mode |

# Switch port configuration

| Command | Description | Mode |
| ---   | --- | --- |
| `duplex` [auto or full or half] | Configure the duplex mode | Interface Configuration Mode |
| `speed` [auto or 10 or 100 or 1000] | Configure the speed | Interface Configuration Mode |
| `auto mdix` | Automaticly detects cable type | Interface Configuration Mode |

# SSH Configuration

| Step | Command | Description | Mode |
| --- | --- | --- | --- |
| 1 | `show ip ssh` | Check if SSH is supported | Privileged EXEC Mode |
| 2 | `ip domain-name` [domain-name] | Configure the IP domain | Global Configuration Mode |
| 3 | `crypto key generate rsa` | Generate a RSA key pair | Global Configuration Mode |
| 4 | `username` [username] secret [password] | Configures a local user | Global Configuration Mode |
| 5 (VTY Lines) | `transport input ssh` and `login local` | Configures mandatory use of SSH and allows login with the local user | Global Configuration Mode |
| 6 | `ip ssh version 2` | Enables SSH version 2 | Global Configuration Mode |

# Loobback interface on router

| Command | Description | Mode |
| ---   | --- | --- |
| `interface loopback` [number] | Creates and accesses a loopback interface | Global Configuration Mode |
| `ip address` [ip-address] [subnet-mask] | Assign a IPv4 address to the loopback interface | Interface Configuration Mode |

# Routing

| Command | Description | Mode |
| ---   | --- | --- |
| `ip route` [destination IPv4 network] [subnet-mask] [next hop IPv4 address] [distance] | Next-hop IPv4 static route | Global Configuration Mode |
| `ip route` [destination IPv4 network] [subnet-mask] [exit interface] [distance] | Directly connected IPv4 static route | Global Configuration Mode |
| `ip route` [destination IPv4 network] [subnet-mask] [exit interface] [next hop IPv4 address] [distance] | Fully specified IPv4 static route | Global Configuration Mode |
| `ipv6 route` [destination IPv6 network prefix length] [next hop IPv6 addres] [distance] | Next-hop IPv6 static route | Global Configuration Mode |
| `ipv6 route` [destination IPv6 network prefix length] [exit interface] [distance] | Directly connected IPv6 static route | Global Configuration Mode |
| `ipv6 route` [destination IPv6 network prefix length] [exit interface] [next hop IPv6 addres] [distance] | Fully specified IPv6 static route | Global Configuration Mode |
| `ip route 0.0.0.0 0.0.0.0` [next-hop IPv4 address / exit interface] | Default static IPv4 route | Global Configuration Mode |
| `ipv6 route ::/0` [next-hop IPv6 addres / exit interface] | Default static IPv6 route | Global Configuration Mode |
| `ip route` [destination host adress] [255.255.255.255] [next hop IPv4 address / exit interface] [distance] | IPv4 static host route | Global Configuration Mode |
| `ipv6 route` [destination IPv6 address with /128 prefix] [exit interface / next hop IPv6 addres] [distance] | IPv6 static host route | Global Configuration Mode |

