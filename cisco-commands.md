# Cisco IOS Cheatsheet

---

## Verify Configuration

| Command | Description | Mode |
|---------|-------------|------|
| `show running-config` | Current running configuration | `#` |
| `show startup-config` | Current startup configuration | `#` |
| `show interfaces` | Info about all physical and virtual interfaces including errors | `#` |
| `show ip route` | Shows the IPv4 routing table | `#` |
| `show ipv6 route` | Shows the IPv6 routing table | `#` |
| `show running-config \| section ip route` | Shows config of the static routes | `#` |

---

## Basic Device Configuration

| Command | Description | Mode |
|---------|-------------|------|
| `copy running-config startup-config` | Save the changes | `#` |
| `clock set [time] [month] [day] [year]` | Set up time and date | `#` |
| `hostname [name]` | Set the device name | `config` |
| `enable secret [password]` | Set a password for privileged exec mode | `config` |
| `banner motd $[message]$` | Configure a banner | `config` |
| `security password min-length [length]` | Configures the system to require a minimum length for passwords | `config` |
| `login block-for [seconds] attempts [amount] within [seconds]` | Sets up a timeout for failed login attempts | `config` |
| `service password-encryption` | Encrypts all set passwords | `config` |
| `password [password]` | Set a password for access via console or SSH | `config-line` |
| `login` | Enforces the authentication requirement to the line | `config-line` |
| `exec-timeout [minutes] [seconds]` | Sets the session to disconnect after a timeout | `config-line` |
| `no ip domain-lookup` | Disable DNS lookup to prevent the router from attempting to translate incorrectly entered commands as host names | `config-line` |

---

## Interface Configuration

| Command | Description | Mode |
|---------|-------------|------|
| `interface [interface name]` | Configuration of a specific interface | `config` |
| `interface range [interface name] [number] - [number]` | Configuration of a range of interfaces | `config` |
| `line vty [number] [number]` | Configuration of an access method (console, VTY) | `config` |
| `ip default-gateway [ip-address]` | Configure default gateway IP on a switch | `config` |
| `interface loopback [number]` | Configure a loopback interface on a router | `config` |
| `ipv6 address [ipv6-address] link-local` | Sets the link-local address | `config-if` |
| `ip address [ip-address] [subnet-mask]` | Assigns IPv4 address | `config-if` |
| `ipv6 address [ipv6-address/prefix]` | Assigns IPv6 address | `config-if` |
| `description [description]` | Description of the interface | `config-if` |
| `no shutdown` | Activates interface | `config-if` |

---

## Configure SSH (use in this order)

| Command | Description | Mode |
|---------|-------------|------|
| `ip domain-name [domain-name]` | Configure the IP domain | `config` |
| `crypto key generate rsa` | Generate an RSA key pair (use 1024) | `config` |
| `username [username] secret [password]` | Configures a local user | `config` |
| `line vty 0 15` | Configure the vty lines | `config` |
| `transport input ssh` | Configures mandatory use of SSH | `config-line` |
| `login local` | Allows login with the local user | `config-line` |
| `exit` | Exit to global configuration mode | `config-line` |
| `ip ssh version 2` | Enables SSH version 2 | `config` |

---

## Static Routing

| Command | Description | Mode |
|---------|-------------|------|
| `ip route [dest IPv4 network] [subnet-mask] [next-hop IPv4 address] [distance]` | Next-hop IPv4 static route | `config` |
| `ip route [dest IPv4 network] [subnet-mask] [exit interface] [distance]` | Directly connected IPv4 static route | `config` |
| `ip route [dest IPv4 network] [subnet-mask] [exit interface] [next-hop IPv4 address] [distance]` | Fully specified IPv4 static route | `config` |
| `ip route 0.0.0.0 0.0.0.0 [next-hop IPv4 address / exit interface]` | Default static IPv4 route | `config` |
| `ipv6 unicast-routing` | Enables IPv6 routing | `config` |
| `ipv6 route [dest IPv6 prefix/length] [next-hop IPv6 address] [distance]` | Next-hop IPv6 static route | `config` |
| `ipv6 route [dest IPv6 prefix/length] [exit interface] [distance]` | Directly connected IPv6 static route | `config` |
| `ipv6 route [dest IPv6 prefix/length] [exit interface] [next-hop IPv6 address] [distance]` | Fully specified IPv6 static route | `config` |
| `ipv6 route ::/0 [next-hop IPv6 address / exit interface]` | Default static IPv6 route | `config` |

---

## VLAN Create, Remove, Assign

| Command | Description | Mode |
|---------|-------------|------|
| `delete vlan.dat` | Delete all VLANs — reload the switch after doing this | `#` |
| `vlan [vlan-id]` | Create a VLAN with a valid ID number | `config` |
| `no vlan [vlan-id]` | Delete a VLAN | `config` |
| `interface vlan [vlan-id]` | Enter the VLAN interface config | `config` |
| `name [vlan-name]` | Give the VLAN a name | `config-vlan` |
| `switchport mode access` | Set interface port to access mode | `config-if` |
| `switchport access vlan [vlan-id]` | Assign the interface port to a VLAN | `config-if` |
| `no switchport access vlan` | Assign the interface port back to VLAN 1 | `config-if` |

---

## VLAN Trunk Configuration

| Command | Description | Mode |
|---------|-------------|------|
| `switchport mode trunk` | Set the port to permanent trunking mode | `config-if` |
| `switchport mode dynamic auto` | Interface will become trunk if the neighboring interface is set to trunk or desirable mode | `config-if` |
| `switchport mode dynamic desirable` | Actively seeks to become a trunk by negotiating with other auto or desirable interfaces | `config-if` |
| `switchport mode access` | Reset interface port to access mode (default) | `config-if` |
| `switchport trunk native vlan [vlan-id]` | Set the native VLAN to something other than VLAN 1 | `config-if` |
| `no switchport trunk native vlan` | Reset the native VLAN to 1 | `config-if` |
| `switchport trunk allowed vlan [vlan list]` | Specify the list of VLANs to be allowed on the trunk link | `config-if` |
| `no switchport trunk allowed vlan` | Reset to default | `config-if` |

---

## VLAN Router Configuration

> Don't forget to use `no shutdown` on the main interface.

| Command | Description | Mode |
|---------|-------------|------|
| `interface [interface id].[subinterface id]` | Create a subinterface | `config` |
| `description [description]` | Gives the subinterface a description | `config-if` |
| `encapsulation dot1q [vlan id]` | Configures the subinterface to respond to 802.1Q traffic | `config-if` |
| `no encapsulation dot1q [vlan id]` | Removes the 802.1Q VLAN tagging association | `config-if` |
| `encapsulation dot1q [vlan id] native` | Set the VLAN to something other than 1 | `config-if` |
| `no encapsulation dot1q [vlan id] native` | Disables processing untagged (native) traffic for that VLAN | `config-if` |
| `ip address [ip-address] [subnet-mask]` | Gives the subinterface an IPv4 address | `config-if` |

---

## VLAN Layer 3 Switch Configuration

> When using layer 3 switches, add the default gateway IPs to the VLAN interfaces.

| Command | Description | Mode |
|---------|-------------|------|
| `ip routing` | Globally enables layer 3 routing on the switch | `config` |
| `no switchport` | Converts a layer 2 port to a layer 3 routed port | `config-if` |
| `switchport trunk encapsulation dot1q` | Command needed before a port can be set to trunk mode | `config-if` |

---

## VLAN Troubleshooting

| Command | Description | Mode |
|---------|-------------|------|
| `show vlan brief` | Display VLAN name and its ports, one VLAN per line | `#` |
| `show interfaces trunk` | Shows all trunk connections | `#` |

---

## EtherChannels

> - Speed and duplex mode must be the same on all interfaces
> - All interfaces must be assigned to the same VLAN or set as TRUNK
> - In a trunking EtherChannel, the allowed VLANs must be the same on all interfaces
> - Steps: 1 — Configure a range of interfaces to a channel group, 2 — Configure the port-channel as you would a normal interface

| Command | Description | Mode |
|---------|-------------|------|
| `interface range [interface name] [number] - [number]` | Configuration of a range of interfaces | `config` |
| `channel-group [number] mode active` | Configures LACP EtherChannel (port initiates negotiations) | `config-if` |
| `channel-group [number] mode passive` | Configures LACP EtherChannel (port responds to LACP packets) | `config-if` |
| `channel-group [number] mode auto` | Configures PAgP EtherChannel (port responds to PAgP packets) | `config-if` |
| `channel-group [number] mode desirable` | Configures PAgP EtherChannel (port initiates negotiations) | `config-if` |
| `channel-group [number] mode on` | Configures EtherChannel (both sides must be set to on) | `config-if` |
| `interface port-channel [number]` | Configuration of the port channel | `config` |

---

## Troubleshooting EtherChannels

| Command | Description | Mode |
|---------|-------------|------|
| `show interfaces port-channel` | Displays the general status of the port channel interface | `#` |
| `show etherchannel summary` | Displays one line of information per port channel | `#` |
| `show etherchannel port-channel` | Displays information about a specific port channel interface | `#` |
| `show interfaces etherchannel` | Displays information about the role of a physical member interface | `#` |

---

## Subnetting IPv4

### Subnet Quick Reference

| Subnets | 1 | 2 | 4 | 8 | 16 | 32 | 64 | 128 | 256 |
|---------|---|---|---|---|----|----|----|-----|-----|
| **Hosts** | 256 | 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |
| **Mask** | /24 | /25 | /26 | /27 | /28 | /29 | /30 | /31 | /32 |

### Example — Divide 192.168.4.0/24 into 3 subnets

> 3 is not possible, so use 4 subnets with 64 hosts each (/26).

| Network ID | Subnet Mask | Host ID Range | Usable Hosts | Broadcast ID |
|------------|-------------|---------------|--------------|--------------|
| 192.168.4.0 | 255.255.255.192 (/26) | 192.168.4.1 – 192.168.4.62 | 62 | 192.168.4.63 |
| 192.168.4.64 | 255.255.255.192 (/26) | 192.168.4.65 – 192.168.4.126 | 62 | 192.168.4.127 |
| 192.168.4.128 | 255.255.255.192 (/26) | 192.168.4.129 – 192.168.4.190 | 62 | 192.168.4.191 |
| 192.168.4.192 | 255.255.255.192 (/26) | 192.168.4.193 – 192.168.4.254 | 62 | 192.168.4.255 |

### VLSM Example — 4 networks needing 100, 50, 10, and 2 hosts (192.168.1.0/24)

| Hosts Needed | Block Size | Mask | Network Range |
|---|---|---|---|
| 100 | 128 | /25 | 192.168.1.0 – 192.168.1.127 |
| 50 | 64 | /26 | 192.168.1.128 – 192.168.1.191 |
| 10 | 16 | /28 | 192.168.1.192 – 192.168.1.207 |
| 2 | 4 | /30 | 192.168.1.208 – 192.168.1.211 |

### IPv6 Subnetting Example — Divide 2001:db8:abcd::/48 into 4

- 2001:db8:abcd:0001::/64
- 2001:db8:abcd:0002::/64
- 2001:db8:abcd:0003::/64
- 2001:db8:abcd:0004::/64

---

## DHCPv4 Server

| Command | Description | Mode |
|---------|-------------|------|
| `no service dhcp` | Disables DHCPv4 on the router (DHCP is enabled by default) | `#` |
| `service dhcp` | Enables DHCPv4 on the router | `#` |
| `ip dhcp excluded-address [low-address] [high-address]` | Excludes IP addresses (e.g. gateways, servers) | `config` |
| `ip dhcp pool [pool-name]` | Creates a pool and enters DHCPv4 configuration mode | `config` |
| `network [network-address] [subnetmask]` | Define the range of available addresses | `dhcp-config` |
| `default-router [router ip address]` | Specifies the IPv4 address of the default gateway | `dhcp-config` |
| `dns-server [address]` | Specifies the IPv4 address of the DNS server | `dhcp-config` |
| `domain-name [domain name]` | Defines the domain name of the pool | `dhcp-config` |
| `lease {days [hours [minutes]] \| infinite}` | Sets the duration of the lease for the assigned IP address | `dhcp-config` |

---

## DHCPv4 Relay Agent

> Use on the interface receiving the client broadcast.

| Command | Description | Mode |
|---------|-------------|------|
| `ip helper-address [address]` | Relay DHCPv4 broadcast to the DHCPv4 server | `config-if` |

---

## DHCPv4 Client

> For routers or switches to request an IP address on an interface.

| Command | Description | Mode |
|---------|-------------|------|
| `ip address dhcp` | Configures an Ethernet interface as a DHCP client | `config-if` |
| `no shutdown` | Activate the interface | `config-if` |

---

## DHCPv4 Troubleshooting

| Command | Description | Mode |
|---------|-------------|------|
| `show running-config \| section dhcp` | Displays the DHCPv4 commands configured on the router | `#` |
| `show ip dhcp binding` | Displays a list of all IPv4 address to MAC address bindings | `#` |
| `show ip dhcp server statistics` | Displays count information regarding DHCPv4 messages sent and received | `#` |

---

## DHCPv6 SLAAC

| Command | Description | Mode |
|---------|-------------|------|
| `ipv6 unicast-routing` | Enable IPv6 routing | `config` |

---

## DHCPv6 Server — Stateless

| Command | Description | Mode |
|---------|-------------|------|
| `ipv6 unicast-routing` | Enable IPv6 routing | `config` |
| `ipv6 dhcp pool [pool-name]` | Define a DHCPv6 pool | `config` |
| `dns-server [dns server ipv6 address]` | Option to add a DNS server | `dhcp-config` |
| `domain-name [name]` | Option to add a domain name | `dhcp-config` |
| `interface [interface name]` | Interface that the clients use | `config` |
| `ipv6 dhcp server [pool-name]` | Bind the interface to the pool | `config-if` |
| `ipv6 nd other-config-flag` | Manually change O flag from 0 to 1 (ask DNS to DHCPv6) | `config-if` |

---

## DHCPv6 Server — Statefull

| Command | Description | Mode |
|---------|-------------|------|
| `ipv6 unicast-routing` | Enable IPv6 routing | `config` |
| `ipv6 dhcp pool [pool-name]` | Define a DHCPv6 pool | `config` |
| `address prefix [address]/[prefix]` | Define the address and prefix | `dhcp-config` |
| `dns-server [dns server ipv6 address]` | Option to add a DNS server | `dhcp-config` |
| `interface [interface name]` | Interface that the clients use | `config` |
| `ipv6 dhcp server [pool-name]` | Bind the interface to the pool | `config-if` |
| `ipv6 nd managed-config-flag` | Manually change M flag from 0 to 1 (get everything from DHCPv6) | `config-if` |
| `ipv6 nd prefix default no-autoconfig` | Manually change A flag from 1 to 0 (disable SLAAC) | `config-if` |

---

## DHCPv6 Relay Agent

> Use on the interface connected to the clients.

| Command | Description | Mode |
|---------|-------------|------|
| `ipv6 dhcp relay destination [DHCPv6 server address]` | Use when DHCPv6 server is on a different network than the client | `config-if` |
| `ipv6 dhcp relay destination [DHCPv6 server address] [interface to reach server]` | Use when the next hop address is a Link-Local Address (LLA) | `config-if` |

---

## DHCPv6 Client

| Command | Description | Mode |
|---------|-------------|------|
| `ipv6 unicast-routing` | Enable IPv6 routing | `config` |
| `ipv6 enable` | Create a Link-Local Address (LLA) | `config-if` |
| `ipv6 address dhcp` | Configure the router to use Stateful DHCPv6 | `config-if` |
| `ipv6 address autoconfig` | Configure the router to use SLAAC / Stateless | `config-if` |

---

## DHCPv6 Troubleshooting

| Command | Description | Mode |
|---------|-------------|------|
| `show ipv6 interface brief` | Verify that the GUA is assigned | `#` |
| `show ipv6 dhcp` | Verify that the DHCPv6 relay agent is operational | `#` |
| `show ipv6 dhcp binding` | Verify that the DHCPv6 relay agent is operational | `#` |

---

## FHRP (HSRP)

> The router interface itself also needs an IP address and subnet mask.

| Command | Description | Mode |
|---------|-------------|------|
| `interface [interface name]` | Interface to use | `config` |
| `standby version 2` | Sets the HSRP version to 2 | `config-if` |
| `standby [group] ip [address]` | Assigns the virtual IP address that clients will use as their default gateway | `config-if` |
| `standby [group] priority [value]` | Sets the router's priority (default 100, range 0–255); highest value becomes Active | `config-if` |
| `standby [group] preempt` | Allows this router to forcefully take back the Active role if it comes online with a higher priority | `config-if` |
| `show standby brief` | Show FHRP info | `#` |

---

## Factory Reset Switch

| Command | Description | Mode |
|---------|-------------|------|
| `erase startup-config` | Delete the startup config | `#` |
| `delete vlan.dat` | Delete the VLAN file (switches only) | `#` |
| `reload` | Restart the device | `#` |

---

## CIDR / Subnet Mask Reference

| CIDR | Subnet Mask | Total Hosts | Usable Hosts |
|------|-------------|-------------|--------------|
| /32 | 255.255.255.255 | 1 | 1 (Host/Loopback) |
| /31 | 255.255.255.254 | 2 | 2 (Point-to-Point) |
| /30 | 255.255.255.252 | 4 | 2 (Router-link) |
| /29 | 255.255.255.248 | 8 | 6 |
| /28 | 255.255.255.240 | 16 | 14 |
| /27 | 255.255.255.224 | 32 | 30 |
| /26 | 255.255.255.192 | 64 | 62 |
| /25 | 255.255.255.128 | 128 | 126 |
| /24 | 255.255.255.0 | 256 | 254 |
| /23 | 255.255.254.0 | 512 | 510 |
| /22 | 255.255.252.0 | 1,024 | 1,022 |
| /21 | 255.255.248.0 | 2,048 | 2,046 |
| /20 | 255.255.240.0 | 4,096 | 4,094 |
| /19 | 255.255.224.0 | 8,192 | 8,190 |
| /18 | 255.255.192.0 | 16,384 | 16,382 |
| /17 | 255.255.128.0 | 32,768 | 32,766 |
| /16 | 255.255.0.0 | 65,536 | 65,534 |
| /14 | 255.252.0.0 | 262,144 | 262,140 |
| /12 | 255.240.0.0 | 1,048,576 | 1,048,572 |
| /10 | 255.192.0.0 | 4,194,304 | 4,194,300 |
| /8 | 255.0.0.0 | 16,777,216 | 16,777,212 |
