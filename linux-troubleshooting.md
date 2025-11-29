# Troubleshooting network services

Always use a bottom-up approach in order to troubleshoot effectively interventions on higher layers will not solve issues if problems on the lower layer aren't fixed first.

## Real time logs

It's always a good idea to open a seperate terminal window and follow the logs in real time

| Command | Description
| --- | --- |
| `sudo journalctl -fl` | Shows the current system journal logs in real time |
| `sudo journalctl -flu` [service] | Shows the logs for a specific service in real time |

## Link Layer

### Step 1

Are cables connected properly?

Physical device:
- Look for blinking lights of the system under test and the network device it is attached to
- Test cables with a cable tester

Virtual machine:
- Check if the network adapter is connected to the right network

### Step 2

Are the network interface up?

| Command | Description |
| ---   | --- |
| `ip -br l` | Check the status of the network interfaces |

NO-CARRIER means that the cable is not connected
If anything is down control cables and settings of the netwerk adapter

## Internet Layer

Local network configuration of the system under test:
- IP address and subnet mask
- Default gateway
- DNS servers

Routing within the LAN:
- Can you ping the default gateway and DNS servers?
- Can you ping another system on the same network?
- Does the DNS server respond to queries?

### Step 1: Checking local configuration

Check the IP address:
- IP addres?
  - If not DHCP server down?
  - Static IP address correct?
- Correct subnet?
  - Check the configuration of the network interface

| Command | Description |
| ---   | --- |
| `ip addres` | Detailed information about all network interfaces |
| `ip -br a` | Short summary of the network interfaces |
| `nmcli device status` | Shows the status of the interfaces |
| `sudo nmcli connection modify '[connection]' ipv4.addresses [IPv4 address/subnetmask]` | Changes the IPv4 addres |
| `sudo nmcli connection down '[connection]'` | Shuts a connection down |
| `sudo nmcli connection up '[connection]'` | Activates a connection |

Check the default gateway:

| Command | Description |
| ---   | --- |
| `ip route` | Show the routing table |
| `sudo ip route add default via [gateway-ip] dev [interface]` | Sets up the default gateway (in VM's this is through the NAT adaper with IP 10.0.2.2) |

Check the DNS configuration:
- The DNS server in virtualbox is the one provided by the NAT interface: 10.0.2.3

| Command | Description |
| ---   | --- |
| `cat /etc/resolv.conf` | Shows the DNS IP address |
| `resolvectl dns` | Shows the DNS IP address |
| `sudo nmcli connection modify [interface] ipv4.dns "[DNS IP]"` | Sets up the DNS server |
| `sudo nmcli connection down '[connection]'` | Shuts a connection down |
| `sudo nmcli connection up '[connection]'` | Activates a connection |

### Step 2: Routing within the LAN

Test connectivity:
- Ping between hosts within the LAN
- Ping the default gateway
- Ping the DNS server

## Transport layer

