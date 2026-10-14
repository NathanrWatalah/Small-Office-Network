# PROJECT 1: SMALL OFFICE NETWORK

## Cisco Packet Tracer Project Documentation

**Student Name:** Nathan R. Watalah  
**Program:** Information Technology  
**Level:** Sophomore 2, System Administration  
**Project Title:** Small Office Network  
**Software Used:** Cisco Packet Tracer  
**Project Type:** Network Design, Configuration, and Troubleshooting

---

## 1. Introduction

A computer network allows computers and other devices to communicate and share information. Businesses use networks to help employees exchange information, access shared resources, and communicate with other devices.

This project focuses on designing and configuring a small office network using Cisco Packet Tracer. The network consists of one router, one switch, and three computers representing employees in three departments.

The project uses static IPv4 addresses to identify each computer and allow communication between devices on the same network.

## 2. Project Scenario

Imagine a small company with three departments. Each department has one computer, and the company wants all three computers to communicate with one another and reach the router.

The company needs a simple, affordable network that provides reliable communication between its computers.

The proposed network connects all three computers to a central switch. The switch connects to a router, which serves as the default gateway for the computers.

### Network Topology

```text
                  Router
             192.168.10.1
                     |
                     |
                   Switch
              _______|_______
             |       |       |
            PC-1    PC-2    PC-3
           .10      .11     .12
```

## 3. Problem Statement

The company needs a network that allows its employees to communicate between computers and access the router. Without a properly configured network, computers may not communicate because of incorrect IP addresses, subnet masks, gateway settings, or physical connections.

This project solves the problem by creating a network topology, assigning IP addresses, configuring the router, and testing connectivity.

## 4. Project Aim

The main aim of this project is to design, configure, and test a basic small office network using Cisco Packet Tracer.

## 5. Project Objectives

The specific objectives are to:

1. Design a small office network topology.
2. Connect three computers to a network switch.
3. Connect the switch to a router.
4. Configure the router's network interface.
5. Assign static IPv4 addresses to all computers.
6. Configure the correct subnet mask and default gateway.
7. Test communication between computers.
8. Verify communication between computers and the router.
9. Identify and troubleshoot basic network problems.
10. Understand the roles of routers and switches in a network.

## 6. Purpose of the Project

The purpose of this project is to build a foundation in computer networking and system administration.

It introduces the practical steps required to connect devices, assign IP addresses, configure a router, and verify network communication.

It also helps students understand how a small business can connect its computers using basic networking equipment.

## 7. Devices and Software Required

The following devices and software are required.

| Device or software | Quantity | Purpose |
|---|---:|---|
| Cisco router | 1 | Provides the default gateway and routes traffic |
| Cisco switch | 1 | Connects computers within the local network |
| PCs | 3 | Represent computers used by employees |
| Copper straight-through cables | 4 | Connect the router, switch, and PCs |
| Cisco Packet Tracer | 1 | Used to design, configure, and test the network |

All devices are simulated in Cisco Packet Tracer. No physical networking equipment is required.

## 8. Network Design

The network uses a star topology. In this arrangement, each computer connects to a central switch.

The switch receives and forwards Ethernet frames between connected devices. The router provides a gateway for traffic that needs to travel outside the local network.

All three computers belong to the same IPv4 network, so they can communicate directly through the switch.

### Network Address

- Network address: `192.168.10.0/24`
- Subnet mask: `255.255.255.0`
- Default gateway: `192.168.10.1`
- Broadcast address: `192.168.10.255`

The `/24` prefix means the first 24 bits identify the network. This subnet provides 254 usable IPv4 addresses.

## 9. IP Addressing Table

Each device receives a unique IP address.

| Device | Interface | IPv4 address | Subnet mask | Default gateway |
|---|---|---|---|---|
| Router | G0/0 | 192.168.10.1 | 255.255.255.0 | Not applicable |
| PC-1 | FastEthernet | 192.168.10.10 | 255.255.255.0 | 192.168.10.1 |
| PC-2 | FastEthernet | 192.168.10.11 | 255.255.255.0 | 192.168.10.1 |
| PC-3 | FastEthernet | 192.168.10.12 | 255.255.255.0 | 192.168.10.1 |

The router and each computer use addresses from the same network. No two devices use the same IP address.

## 10. Project Implementation

### Step 1: Create the Network Topology

Open Cisco Packet Tracer and add:

- One router.
- One switch.
- Three PCs.

Arrange the devices on the workspace to match the network diagram.

### Step 2: Connect the Devices

Use copper straight-through cables to make the following connections:

| Source device | Source port | Destination device | Destination port |
|---|---|---|---|
| Router | G0/0 | Switch | Fa0/1 |
| PC-1 | FastEthernet0 | Switch | Fa0/2 |
| PC-2 | FastEthernet0 | Switch | Fa0/3 |
| PC-3 | FastEthernet0 | Switch | Fa0/4 |

The exact router interface name may differ depending on the router model selected in Packet Tracer.

Wait for the connection indicators to turn green.

### Step 3: Configure the Router

Select the router, open its CLI, and enter the following commands:

```text
enable
configure terminal
interface gigabitEthernet 0/0
ip address 192.168.10.1 255.255.255.0
no shutdown
exit
end
```

**Explanation of the commands**

- `enable` enters privileged EXEC mode.
- `configure terminal` opens global configuration mode.
- `interface gigabitEthernet 0/0` selects the router interface.
- `ip address` assigns the IPv4 address and subnet mask.
- `no shutdown` enables the interface.
- `exit` leaves the interface configuration.
- `end` returns to privileged EXEC mode.

Save the configuration:

```text
copy running-config startup-config
```

Press Enter if Packet Tracer asks you to confirm the destination filename.

### Step 4: Verify the Router Interface

Enter:

```text
show ip interface brief
```

Check that the configured interface displays the correct IP address and that its status and protocol show `up` when the cable connects to an active switch port.

If the interface remains down, check the cable, switch port, interface name, and router configuration.

### Step 5: Configure PC-1

Select PC-1 and open:

`Desktop → IP Configuration → Static`

Enter:

```text
IP Address:      192.168.10.10
Subnet Mask:     255.255.255.0
Default Gateway: 192.168.10.1
```

### Step 6: Configure PC-2

Open PC-2's IP Configuration window and enter:

```text
IP Address:      192.168.10.11
Subnet Mask:     255.255.255.0
Default Gateway: 192.168.10.1
```

### Step 7: Configure PC-3

Open PC-3's IP Configuration window and enter:

```text
IP Address:      192.168.10.12
Subnet Mask:     255.255.255.0
Default Gateway: 192.168.10.1
```

Confirm that every computer has the correct IP address, subnet mask, and default gateway.

## 11. Network Testing and Verification

Testing confirms whether the network works as intended.

### Test 1: Test PC-1 to the Router

Open PC-1, select Desktop, and open Command Prompt.

Enter:

```text
ping 192.168.10.1
```

Expected result: PC-1 receives replies from the router.

This confirms communication between PC-1 and the router's LAN interface.

### Test 2: Test PC-1 to PC-2

Enter:

```text
ping 192.168.10.11
```

Expected result: PC-1 receives replies from PC-2.

This confirms communication between the two computers.

### Test 3: Test PC-1 to PC-3

Enter:

```text
ping 192.168.10.12
```

Expected result: PC-1 receives replies from PC-3.

### Test 4: Test PC-2 to PC-3

From PC-2, enter:

```text
ping 192.168.10.12
```

Expected result: PC-2 receives replies from PC-3.

### Test 5: Verify the Router Configuration

On the router, enter:

```text
show ip interface brief
show running-config
```

Confirm that the interface has the correct address and is enabled.

**Important:** These are the expected results. Record your actual test results after running the commands in Packet Tracer.

## 12. Troubleshooting

Network problems can result from incorrect configurations or physical connections.

| Problem | Possible cause | Solution |
|---|---|---|
| PC cannot ping the router | Incorrect IP address or gateway | Check the PC's IP configuration |
| PC cannot ping another PC | Incorrect IP address or subnet mask | Verify both PCs' settings |
| Router interface is down | Interface is disabled or cable is disconnected | Enter `no shutdown` and check the connection |
| Network link is not active | Wrong port or cable connection | Check the topology and port connections |
| IP address conflict | Two devices use the same IP address | Assign a unique address to each device |
| Ping fails initially | Address resolution or link initialization is incomplete | Wait briefly and retry the ping |

A good troubleshooting process checks the physical connections first, then the IP configuration, router interface, and connectivity tests.

## 13. Expected Results

When the project is correctly configured:

1. All three computers connect to the switch.
2. The switch connects to the router.
3. Each computer has a unique static IPv4 address.
4. All computers use the correct subnet mask.
5. The router interface is enabled.
6. Each computer can communicate with the other computers.
7. Each computer can reach the router's LAN interface.
8. The network passes the required ping tests.

The project creates a functional local area network for a small office.

## 14. Skills and Knowledge Gained

This project provides practical experience in:

- Cisco Packet Tracer.
- Network topology design.
- IPv4 addressing.
- Subnet masks and network prefixes.
- Static IP configuration.
- Default gateway configuration.
- Router interface configuration.
- Basic switch connectivity.
- Command-line configuration.
- Ping testing.
- Network verification.
- Basic troubleshooting.

These skills provide a foundation for more advanced networking and system administration projects.

## 15. Benefits of the Project

### Educational Benefits

The project connects networking theory with practical configuration. It helps students understand how devices communicate on a local network.

### Technical Benefits

It provides experience assigning IP addresses, enabling router interfaces, and diagnosing basic connectivity problems.

### Career Benefits

The skills are relevant to entry-level IT support, network support, and system administration work.

### Future Development

The network can later support additional computers, a server, DHCP, DNS, VLANs, access control lists, and more advanced security features.

## 16. Limitations

This project demonstrates only a basic local network.

It does not include:

- Internet connectivity.
- DHCP or DNS services.
- VLANs or department-level network separation.
- Wireless access.
- Firewall rules or access control lists.
- Redundant routers or switches.
- A centralized user management server.

These features can be introduced in later projects.

## 17. Future Improvements

The network can be improved by:

1. Adding a DHCP server to assign IP addresses automatically.
2. Adding a DNS server to resolve hostnames.
3. Creating VLANs to separate departments.
4. Configuring ACLs to control traffic between departments.
5. Adding a file server for shared resources.
6. Connecting another office through a second router.
7. Adding security measures to protect network devices.

## 18. Conclusion

The Small Office Network project demonstrates how to design, configure, and test a basic computer network using Cisco Packet Tracer.

The project connects three computers to a switch and router, assigns static IPv4 addresses, configures a default gateway, and verifies connectivity using ping tests.

Through this practical exercise, students develop essential networking skills and prepare for more advanced topics such as VLANs, DHCP, DNS, routing, and network security.

The project serves as a starting point for further study in system administration and computer networking.

## 19. Project Evidence

Add screenshots of your completed work to demonstrate that you configured and tested the network.

Recommended screenshots:

1. Completed network topology.
2. Router interface configuration.
3. Router `show ip interface brief` output.
4. PC-1 IP Configuration.
5. Successful PC-1 to router ping.
6. Successful PC-to-PC ping.
7. Final network topology with active links.

Save the Packet Tracer file as:

`Project1-Small-Office-Network.pkt`

**Project status:** Complete after you configure the devices, run the tests, and capture the evidence.
