# Troubleshooting network services

Always use a bottom-up approach in order to troubleshoot effectively interventions on higher layers will not solve issues if problems on the lower layer aren't fixed first.

## Real time logs

It's always a good idea to open a seperate terminal window and follow the logs in real time

| Command | Description
| --- | --- |
| `sudo journalctl -fl` | Shows the current system journal logs in real time |
| `sudo journalctl -flu` [service] | Shows the logs for a specific service in real time |

## Link Layer

### Step 1: Are cables connected properly?

Physical device:
- Look for blinking lights of the system under test and the network device it is attached to
- Test cables with a cable tester

Virtual machine:
- Check if the network adapter is connected to the right network

### Step 2: Are the network interface up?

| Command | Description |
| ---   | --- |
| `ip -br l` | Check the status of the network interfaces |

- NO-CARRIER means that the cable is not connected
- If anything is down control cables and settings of the netwerk adapter

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

### Is the service running?

| Command | Description |
| ---   | --- |
| `sudo systemctl status [service]` | Checks the status of the service |
| `sudo systemctl start [service]` | Starts the service |
| `sudo systemctl enable [service]` | Starts the service on boot |
| `sudo systemctl enable --now [service]` | Starts the service on boot and also starts it now |

### What port is the service using?

| Command | Description |
| ---   | --- |
| `sudo ss -tlnp` | Shows what ports the services are using |

- Check /etc/services for standard port numbers for well-known network services

### Does the firewall allow traffic on the service?

| Command | Description |
| ---   | --- |
| `sudo firewall-cmd --list-all` | Shows the firewall configuration |
| `sudo firewall-cmd --add-service=[service name] --permanent` | Allow a service |
| `sudo firewall-cmd --reload` | Reloads the firewall |

## Application layer

On this phase, we check whether the application is configured correctly, and whether it is available to clients and responds correctly to requests.

### Checking logs

- Some services write logs to a file in `/var/log`

| Command | Description
| --- | --- |
| `sudo journalctl -fl` | Shows the current system journal logs in real time |
| `sudo journalctl -flu` [service] | Shows the logs for a specific service in real time |
| `tail -f /var/log/[logfile]` | Follows a logfile in real time |

### Validate config file syntax

- Most services have a command that checks the syntax of a configuration file before/without starting the service. Check the manpage for the exact command off each service
- Check the configuration file, somewhere in /etc/, e.g. /etc/httpd/httpd.conf. First, create a backup of the current configuration file(s), and if possible the default one (as created when installing the service)
- After making changes restart the service

| Command | Description
| --- | --- |
| `sudo apachectl configtest` | Validates the syntax of the apache webserver config file |

