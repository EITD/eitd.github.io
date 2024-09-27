---
layout: post
section-type: post
has-comments: true
title: "Network protocol"
category: network
---

## ARP (Address Resolution Protocol)

> Query the **MAC(physical)** address through the **IP** address of the target device.

- When sending data, Host A will look for the target IP address in its **ARP cache table**:
    - If MAC is found, write the target MAC address directly to the frame and send it.
    - If the corresponding IP and MAC address is not found, Host A will send a **broadcast** (ARP request), which means sending an inquiry to all hosts in the same network segment. Host B tells the MAC address to Host A  and Host A updates its ARP cache table.


### MAC and NIC

Also called the physical address embedded with **Network Interface Card** (NIC) used at the Data Link Layer. NIC is a hardware component in the networking device using which a device can connect to the network.

### MAC VS IP

| MAC Address | IP Address |
| --- | --- |
| Media Access Control Address | Internet Protocol Address |
| 6 or 8 Byte hexadecimal number e.g. 00-BB-00-62-C2-02 | 4 (IPv4) or 16 (IPv6) Byte address e.g. 192.168.38.11 |
| Physical Address | Logical Address |
| Operates at Data Link Layer | Operates at Network Layer |
| It is embedded with NIC | It is obtained from the network |
| Helps to identify the device | Helps to identify the device connectivity on the network |

## ICMP (Internet Control Message Protocol)

> Used to send **control messages** in TCP/IP networks and **return error** messages or analyze routes.


## Routing Protocol

> Divide the entire Internet into many small autonomous(自治) systems (**AS**).

- Internal Gateway Protocol (**IGP**)
    
    The routing protocol used **within an AS**, which has nothing to do with what other AS.
    
    - **OSPF** (open shortest path first)
        
        **Backbone area** is the core area of the entire OSPF network, and all other areas are directly connected to it.
        
- External Gateway Protocol (**EGP**)
    
    If the source host and the destination host are not in the same AS, use a protocol to pass the routing information to **another AS**.
    
    - **BGP** (Border Gateway Protocol)
        
        Works between AS and only strives to find a better route that can reach the destination network, **not the best route**.
        

## DHCP (Dynamic Host Setup Protocol)

> Enables network administrators to centrally **manage** and automatically **assign IP** network addresses.


## NAT (Network Address Translation)

> **Overriding** the source IP address or destination IP address when the IP packet passes through the router or firewall.