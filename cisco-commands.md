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
| `interface range [interface name] [number] - [number]` | Configuration of a range of interfaces | Global Configuration mode |
| `line` | Configuration of an acces method (console, VTY) | Global Configuration Mode |

# Adressing and interface activation

| Command | Description | Mode |
| ---   | --- | --- |
| `ip address` [ip-address] [subnet-mask] | Assings IPv4 address | Interface Configuration Mode |
| `ipv6 address` [ipv6-address/prefix-length] | Assingns IPv6 address | Interface Configuration Mode |
| `ipv6 addres [ipv6 addres] link-local` | Sets the link-local adress |
| `no shutdown` | Activates interface | Interface Configuration Mode |
| `ip default-gateway` [ip-address] | Configure default gateway IP on a switch | Global Configuration Mode |

# Device configuration

| Command | Description | Mode |
| ---   | --- | --- |
| `hostname` [name] | Set the device name | Global Configuration Mode |
| `enable secret` [password] | Set a password for priveleged exec mode | Global Configuration Mode |
| `password` [password] | Set a password for acces via console or SSH | Line Configuration Mode |
| `login` | Enforces the authentication requirement to the line | Line Configuration Mode |
| `exec-timeout` [minutes] [seconds] | Sets the session to disconect after... | Line Configuration Mode |
| `service password-encryption` | Encrypts all set passwords | Global Configuration Mode |
| `banner motd` [\$message\$] | Configure a banner | Global Configuration Mode |
| `security password min-length` [password lenght] | Configures the system to require a minimum lenght for passwords | Global Configuration mode |
| `ipv6 unicast-routing` | Enables ipv6 routing | Global Configuration Mode |
| `login block for [seconds] attempts [amount of attempts] within [seconds] ` | Sets up a timeout for failed login attempts | Global configuration mode |
| `clock set [time] [month] [day] [year]` | Set up time and date | Privileged EXEC Mode |

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
| `show cdp neighbours` | List of directly connected Cisco devices | Privileged EXEC Mode |
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

# VLAN

## VLAN configuration

| Command | Description | Mode |
| ---   | --- | --- |
| `vlan` [vlan-id] | Create a VLAN with a valid ID number | Global Configuration Mode |
| `no vlan` [vlan-id] | Delete VLAN | Global Configuration Mode |
| `name` [vlan-name] | Give the VLAN a name | VLAN Configuration Mode |
| `switchport mode acces` | Set interface port to acces mode | Interface Configuration Mode |
| `switchport acces vlan` [vlan-id] | Assign the interface port to a VLAN | Interface Configuration Mode |
| `no switchport acces vlan` | Assign the interface port back to VLAN 1 | Interface Configuration Mode |
| `delete vlan.dat` | Delete all VLANs. Reload the switch after doing this | Privileged EXEC MODE |

### Example

`configure terminal`, `interface fa0/18`, `switchport mode acces`, `switchport acces vlan 20`, `end`

## Trunk configuration

| Command | Description | Mode |
| ---   | --- | --- |
| `switchport mode trunk` | Set the port to permanent trunking mode | Interface Configuration Mode |
| `switchport trunk native vlan` [vlan-id] | Set the native VLAN to something other than VLAN 1 | Interface Configuration Mode |
| `no switchport trunk native vlan` | Reset the native VLAN to 1 | Interface Configuration Mode |
| `switchport trunk allowed vlan` [vlan list] | Specify the list of VLANs to be allowed on the trunk link | Interface Configuration Mode |
| `no switchport trunk allowed vlan` | Reset to default | Interface Configuration Mode |
| `switchport mode acces` | RESET interface port to acces mode (default) | Interface Configuration Mode |
| `switchport mode dynamic auto` | Interface will become trunk if the neighboring interface is set to trunk or desirable mode | Interface Configuration Mode |
| `switchport mode dynamic desirable` | Actively seeks to become a trunk by negotiating with other auto or desirable interfaces | Interface Configuration Mode |

### Example

`configure terminal`, `interface fa0/1`, `switchport mode trunk`, `switchport trunk native vlan 99`, `switchport trunk allowed vlan 10,20,30,99`, `end`

## Router configuration

| Command | Description | Mode |
| ---   | --- | --- |
| `interface` [interface id].[subinterface id] | Create a subinterface | Global Configuration mode |
| `description` | Gives the subinterface a description | Sub interface configuration mode |
| `encapsulation dot1q` [vlan id] | Configures the subinterface to respond to 802.1Q traffic | Sub interface configuration mode |
| `encapsulation dot1q` [vlan id] [native] | Set the vlan to something other then 1 | Sub interface configuration mode |
| `ip address` [ip-address] [subnet-mask] | Gives the subinterface a IPv4 adress |Sub interface configuration mode |

### Example

`configure terminal`, `interface G0/0/1.10`, `description default gateway for VLAN 10`, `encapsulation dot1q 10`, `ip address 192.168.10.1 255.255.255.0`, `exit`

## Troubleshooting

| Command | Description | Mode |
| ---   | --- | --- |
| `show vlan brief` | Display VLAN name, and its ports one VLAN per line | Privileged EXEC Mode |
| `show vlan id` [vlan-id] | Display information about the specified VLAN | Privileged EXEC Mode |
| `show vlan name` [vlan-name] | Display information about the specified VLAN | Privileged EXEC Mode |
| `show vlan summary` | Display VLAN summary information | Privileged EXEC Mode |
| `show interface [interface] switchport` | Shows port modus and assigned vlans | Privileged EXEC Mode |
| `show dtp interface` [interface] | Show the current DTP mode | Privileged EXEC Mode |
| `show interfaces trunk` | Shows all trunk connections | Privileged EXEC Mode |

## Layer 3 switch configuration

| Command | Description | Mode |
| ---   | --- | --- |
| `vlan` [vlan-id] | Creates a VLAN and enters VLAN configuration mode | Global Configuration Mode |
| `name` [name] | Gives the VLAN a name | VLAN Configuration Mode |
| `interface vlan` [vlan-id] | Creaste an SVI for the VLAN, acts as the default gateway | Global Configuration Mode |
| `ip address` [IPv4 address] [subnet mask] | Configures the IP addres (default gateway) on the SVI | Interface Configuration Mode |
| `no shutdown` | Activates the SVI |  Interface Configuration Mode |
| `interface` [type/number] | Selects a physical interface to configure | Global Configuration Mode |
| `switchport mode acces` | Sets the port as an acces port | Interface Configuration Mode |
| `switchport acces vlan` [vlan-id] | Assigns the access port to a specific VLAN | Interface Configuration Mode |
| `ip routing` | Globally enables layer 3 routing on the switch | Global Configuration Mode |
| `no switchport` | Converts a layer 2 port to a layer 3 routed port | Interface Configuration Mode |
| `router ospf` [process id] | Enables OSPF routing and enters router configuration mode | Global Configuration Mode |
| `network` [network address] [wildcard mask] [area id] | Advertises a network for OSPF | Router Configuration Mode |

# EtherChannels

## Configuration

| Command | Description | Mode |
| ---   | --- | --- |
| `interface range [interface name] [number] - [number]` | Configuration of a range of interfaces | Global Configuration mode |
| `channel-group [number] mode active` | Configures the range of interfaces to a LACP EhterChannel (port initiates negotiations with other ports) | Interface Configuration Mode |
| `channel-group [number] mode passive` | Configures the range of interfaces to a LACP EhterChannel (port responds to LACP packets) | Interface Configuration Mode |
| `channel-group [number] mode auto` | Configures the range of interfaces to a PAgP EhterChannel (port initiates negotiations with other ports) | Interface Configuration Mode |
| `channel-group [number] mode desirable` | Configures the range of interfaces to a PAgP EhterChannel (port responds to PAgP packets) | Interface Configuration Mode |
| `channel-group [number] mode on` | Configures the range of interfaces to an EtherChannel (both sides need to be set to on to work) | Interface Configuration Mode |
| `interface port-channel [number]` | Configuration of the port channel | Global Configuration Mode |
| `switchport mode trunk` | Set the port to permanent trunking mode | Interface Configuration Mode |
| `switchport trunk allowed vlan` [vlan list] | Specify the list of VLANs to be allowed on the trunk link | Interface Configuration Mode |

## Troubleshooting

| Command | Description | Mode |
| ---   | --- | --- |
| `show interfaces port-channel` | Displays the general status of the port channel interface | Privileged EXEC Mode |
| `show etherchannel summary` | Displays one line of information per port channel | Privileged EXEC Mode |
| `show etherchannel port-channel` | Displays information about a specific port channel interface | Privileged EXEC Mode |
| `show interfaces etherchannel` | Displays information about the role of a physical member interface of the EtherChannel | Privileged EXEC Mode |

# DHCPv4

## Enable / Disable

The DHCPv4 service is enabled by default

| Command | Description | Mode |
| ---   | --- | --- |
| `no service dhcp` | Disable | Global Configuration Mode |
| `service` | Enable | Global Configuration Mode |

## Configuration to use cisco router as DHCP server

| Command | Description | Mode |
| ---   | --- | --- |
| `ip dhcp excluded-address low-addres [high-addres]` | Exclude IPv4 addresses | Global Configuration mode |
| `ip dhcp pool pool-name` | Creates a pool with a specified name en puts the router in DHCPv4 configuration mode | Global Configuration mode |
| `network [network address] [subnetmask]` | Define the range of the available addresses | DHCPv4 configuration mode |
| `default-router address [address2...address8]` | Specifies the IPv4 address of the default gateway for the DHCPv4 clients | DHCPv4 configuration mode |
| `dns-server address [address2...address8]` | Configures the IPv4 address(es) of the DNS server(s) available to the clients | DHCPv4 configuration mode |
| `domain-name domain` | Defines the domain name for the network pool | DHCPv4 configuration mode |
| `lease {days [hours [minutes]] \| infinite}` | Sets the duration of the lease for the assigned IP address | DHCPv4 configuration mode |
| `netbios-name-server address [address2...address8]` | Configures the NetBIOS WINS server(s) if required for the network | DHCPv4 configuration mode |

## Configuration with external DHCP server

| Command | Description | Mode |
| ---   | --- | --- |
| `ip helper-address [address]` | Relay DHCPv4 broadcast to the DHCPv4 server | Interface Configuration Mode (On the interface receiving the client broadcasts) |

## Configuration Cisco router as a DHCPv4 Client

| Command | Description | Mode |
| ---   | --- | --- |
| `ip address dhcp` | Configures an Ethernet interface as a DHCP client | Interface Configuration Mode |

## Verification

| Command | Description | Mode |
| ---   | --- | --- |
| `show running-config \| section dhcp` | Displays the DHCPv4 commands configured on the router | Privileged EXEC Mode |
| `show ip dhcp binding` | Displays a list of all IPv4 address to MAC address bindings provided | Privileged EXEC Mode |
| `show ip dhcp server statistics` | Displays count information regarding DHCPv4 messages sent and received | Privileged EXEC Mode |

# DHCPv6

## Configuring a stateless DHCPv6 server

| Command | Description | Mode |
| ---   | --- | --- |
| `ipv6 unicast-routing` | Enable IPv6 routing |
| `ipv6 dhcp pool [pool-name]` | Define a DHCPv6 pool |
| `dns-server [dns server ipv6 address]` | Option to add a DNS server |
| `domain-name [name]` | Option to add a domain name |
| `ipv6 dhcp server [pool-name]` | Bind the interface to the pool |
| `ipv6 nd other-config-flag` | Manually change the O flag from 0 to 1 |

## Configure a Stateless DHCPv6 client

| Command | Description | Mode |
| ---   | --- | --- |
| `ipv6 unicast-routing` | Enable IPv6 routing |
| `ipv6 enable` | Create an LLA |
| `ipv6 address autoconfig` | Configure to use SLAAC |
| `show ipv6 interface brief` | Verify that the GUA is assigned |
| `show ipv6 dhcp interface [interface name]` | Verify that the client router received other necessary DHCPv6 information |

## Configuring a statefull DHCPv6 server

| Command | Description | Mode |
| ---   | --- | --- |
| `ipv6 unicast-routing` | Enable IPv6 routing |
| `ipv6 dhcp pool [pool-name]` | Define a DHCPv6 pool |
| `ipv6 dhcp server [pool-name]` | Bind the interface to the pool |
| `ipv6 nd managed-config-flag` | Manually change the M flag from 0 to 1 |
| `ipv6 nd prefix default no-autoconfig` | Manually change the A flag from 1 to 0 |

## Configuring a statefull DHCPv6 client

| Command | Description | Mode |
| ---   | --- | --- |
| `ipv6 unicast-routing` | Enable IPv6 routing |
| `ipv6 enable` | Create an LLA |
| `ipv6 address dhcp` | Configure the router to use DHCPv6 |
| `show ipv6 interface brief` | Verify that the GUA is assigned |
| `show ipv6 dhcp interface [interface name]` | Verify that the client router received other necessary DHCPv6 information |

## DHCPv6 Server Verification Commands

| Command | Description | Mode |
| ---   | --- | --- |
| `show ipv6 dhcp pool` | Verify the name of the DHCPv6 pool and its parameters |
| `show ipv6 dhcp binding` | Displays the IPv6 link-local address of the client and the global unicast address assigned bij the server |

## Configure a DHCPv6 Relay Agent

| Command | Description | Mode |
| ---   | --- | --- |
| `ipv6 dhcp relay destination [DHCPv6 server address] [interface to reach the server]` | If the DHCPv6 server is located on another network than the client, then the IPv6 router can be configured as a DHCPv6 relay agent (egress interface only requiered when the next hop address is an LLA) |

## Verify the DHCPv6 Relay Agent

| Command | Description | Mode |
| ---   | --- | --- |
| `show ipv6 dhcp` | Verify that the DHCPv6 relay agent is operational |
| `show ipv6 dhcp binding` | Verify that the DHCPv6 relay agent is operational |

