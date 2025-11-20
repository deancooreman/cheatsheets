# General Commands

| Command | Description |
| ---   | --- |
| ?     | Call for help |
| enable | Privileged exec mode|
| disable | User exec mode |
| configure terminal | Global configuration mode |
| end | Go back to privileged exec mode |
| exit | Go back to the previous mode |
| copy | copy file to another file

# Interface / subconfiguration

| Command | Description |
| ---   | --- |
| interface | Configuration of a specific interface |
| line | Configuration of an acces method (console, VTY) |

# Adressing and interface activation

| Command | Description |
| ---   | --- |
| ip address ip-address subnet-mask | Assings IPv4 address |
| ipv6 address ipv6-address/prefix-length | Assingns IPv6 address |
| no shutdown | Activates interface |
| ip default-gateway ip-address | Configure default gateway IP on a switch |

# Device configuration

| Command | Description |
| ---   | --- |
| hostname name | Set the device name |
| enable secret password | Set a password for priveleged exec mode |
| password password | Set a password for acces via console or SSH |
| login | Enforces the authentication requirement to the line |
| service password-encryption | Encrypts all set passwords |
| banner motd \$message\$ | Configure a banner |

# Show commands

| Command | Description |
| ---   | --- |
| show ip interface brief | Overview assigned IPv4 addresses |
| show ipv6 interface brief | Overview assigned IPv6 addresses |
| show ip interface [interface-id] | IPv4 information of a specific interface |
| show ipv6 interface [interface-id] | IPv6 information of a specific interface |
| show startup-config | Current running configuration |
| show running-config | Current startuo configuration |
| show flash | Info about the content of the flash memory |
| show version | Status of the system hardware and software |
| show history | History of entered commands |
| show mac-address-table | Content of the MAC address table |
| show ip ssh | Version and configuration details SSH |
| show ip route | Content of the IPv4 routing table |
| show ipv6 route | Content of the IPv6 routing table |
| show boot | Current settings of the IOS startup file |
| show controllers ethernet-controller phy | Controls duplex, speed and auto-MDIX settings |