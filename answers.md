# Cybersecurity & Networking Fundamentals — Answers

> Student: [TAMMU KARTHIKEYA DATTA]  
> Assessment:Minor Project

## Section A — Cybersecurity Fundamentals

### Q1. Explain cybersecurity and the CIA Triad.

**Cybersecurity** is the practice of protecting computers, networks, applications, and data from unauthorized access, damage, theft, or disruption. It is important because people and organizations store sensitive information and depend on digital systems for communication and work.

The **CIA Triad** has three principles:

1. **Confidentiality:** Only authorized people can access information. *Example:* A student's marks file is protected with account permissions so other students cannot read it.
2. **Integrity:** Information remains accurate and is changed only by authorized users. *Example:* Access controls and audit logs help prevent unauthorized changes to bank transactions.
3. **Availability:** Systems and information are accessible when needed. *Example:* Backups and redundant servers help a hospital keep its appointment system available after a hardware failure.

### Q2. Differentiate between vulnerability, threat, risk, and attack.

- **Vulnerability:** A weakness that could be exploited. Example: an unpatched operating system.
- **Threat:** Something capable of exploiting a weakness and causing harm. Example: malware or a malicious attacker.
- **Risk:** The likelihood and impact of harm when a threat exploits a vulnerability. Example: an unpatched office computer may be infected, causing downtime and data loss.
- **Attack:** An actual attempt to exploit a weakness. Example: an attacker sends a malicious file that exploits an outdated application.

**Relationship:** A vulnerability creates an opportunity; a threat may exploit it; an attack is an attempt or action; risk describes the possible likelihood and impact.

### Q3. Explain any five areas of cybersecurity.

1. **Network security:** Protects network traffic and devices using firewalls, segmentation, secure protocols, and monitoring.
2. **Application security:** Reduces software weaknesses through secure coding, testing, updates, and access controls.
3. **Cloud security:** Protects cloud-hosted data, applications, identities, and configurations.
4. **Endpoint security:** Protects laptops, desktops, and phones using updates, antivirus/endpoint detection, and device controls.
5. **Information security:** Protects information from unauthorized disclosure, alteration, or loss through permissions, encryption, backups, and policies.

## Section B — Networking Fundamentals

### Q4. Define a computer network and describe LAN, MAN, WAN, and PAN.

A **computer network** is a group of connected devices that communicate and share data or resources using communication links and agreed protocols. Organizations use networks to share files and printers, access the Internet, communicate, centralize services, and manage systems.

- **PAN (Personal Area Network):** Very short-range network around one person. Example: a phone connected to wireless earbuds using Bluetooth.
- **LAN (Local Area Network):** Covers a small area such as a home, lab, or office. Example: computers connected in a college computer lab.
- **MAN (Metropolitan Area Network):** Connects sites across a town or city. Example: a city-wide network connecting municipal offices.
- **WAN (Wide Area Network):** Connects networks across large geographic areas. Example: a company network connecting offices in different countries; the Internet is the largest familiar example.

### Q5. Explain hub, switch, router, firewall, and access point.

- **Hub:** Repeats incoming data to all its ports. It does not intelligently forward frames to a specific destination.
- **Switch:** Connects devices within a LAN and forwards Ethernet frames based on MAC addresses.
- **Router:** Connects different IP networks and forwards packets using IP addresses and routing information. A home router commonly connects the LAN to the Internet.
- **Firewall:** Applies security rules to allow or block network traffic.
- **Wireless access point (AP):** Allows Wi-Fi devices to connect to a wired LAN.

**Switch vs router:** A switch mainly forwards frames inside a local network using MAC addresses, while a router forwards IP packets between different networks using IP addresses.

### Q6. What happens when a user enters example.com in a browser?

1. The browser checks whether it already has a usable cached result.
2. **DNS** resolves `example.com` to an IP address if a cached answer is not available.
3. The computer checks whether the destination is on its local subnet. For an external destination, it sends traffic to its **default gateway**.
4. The local network sends the frame through a switch or Wi-Fi access point to the router.
5. The router forwards the IP packet toward the destination using routing and usually performs network address translation (NAT) for a private home/office IPv4 connection.
6. The client establishes the needed transport connection. HTTPS typically uses TCP plus TLS, or QUIC over UDP for HTTP/3.
7. The browser sends an HTTP request to the web server.
8. The web server processes the request and returns an HTTP response containing page data.
9. The browser interprets HTML, CSS, and JavaScript and displays the website. Additional resources may require more requests.

**Simple flow diagram:**

```text
User enters example.com
          |
       Browser
          |
      DNS lookup
          |
   Destination IP found
          |
PC / Wi-Fi or Switch
          |
 Default Gateway / Router
          |
       Internet
          |
   Web Server for site
          |
   HTTP(S) response
          |
 Browser displays page
```

DNS finds an IP address; it does not itself deliver the web page. TCP/IP and related protocols carry the communication.

## Section C — IP Addressing

### Q7. Differentiate IPv4 and IPv6.

- **IPv4:** Uses 32-bit addresses, usually written as four decimal octets separated by dots. Example: `192.168.1.10`. It provides about 4.3 billion possible addresses before reserved ranges are considered.
- **IPv6:** Uses 128-bit addresses, written as hexadecimal groups separated by colons. Example: `2001:db8::10` (a documentation example address).

IPv6 was introduced mainly to provide a vastly larger address space and also supports improvements in address configuration and protocol design. IPv4 and IPv6 can coexist during transition; IPv6 is not simply an extension of an IPv4 address.

### Q8. Identify the IPv4 class and whether each address is private/public.

| IP address | Traditional class | Private/Public | Explanation |
|---|---|---|---|
| `10.10.10.5` | Class A | Private | `10.0.0.0/8` is private |
| `172.16.5.20` | Class B | Private | `172.16.0.0/12` is private (`172.16` through `172.31`) |
| `192.168.1.50` | Class C | Private | `192.168.0.0/16` is private |
| `8.8.8.8` | Class A | Public | Not in the RFC 1918 private ranges; it is a publicly routable Google DNS address |

**Note:** Class A/B/C is the older classful system. Modern networks generally use CIDR prefixes instead of address classes.

### Q9. For 192.168.20.45/24, identify network, host portion, mask, broadcast, and usable range.

Given IP: `192.168.20.45/24`

1. **Prefix:** `/24` means 24 network bits and 8 host bits.
2. **Subnet mask:** `/24` = `255.255.255.0`.
3. **Network address:** The first 24 bits identify the network; the host octet is set to 0 → `192.168.20.0`.
4. **Host portion:** Last octet is `45` (binary `00101101`) → host ID 45 in this subnet.
5. **Broadcast address:** Set all 8 host bits to 1 → `192.168.20.255`.
6. **Usable host range:** `192.168.20.1` through `192.168.20.254`.
7. **Usable host count:** \(2^8 - 2 = 254\), excluding the network and broadcast addresses.

## Section D — Subnetting & Calculations

### Q10. Calculate details for 192.168.10.0/26.

Given parent network: `192.168.10.0/24`; required subnet: `/26`.

1. **Subnet mask:** `/26` = `255.255.255.192`.
2. **Bits borrowed from /24:** `26 − 24 = 2` bits.
3. **Number of /26 subnets from a /24:** \(2^2 = 4\).
4. **Host bits per /26:** `32 − 26 = 6`.
5. **Usable hosts per subnet:** \(2^6 − 2 = 62\).
6. **Block size:** `256 − 192 = 64` in the last octet.

The four /26 subnets within `192.168.10.0/24` are:

| Subnet | Network address | First usable | Last usable | Broadcast |
|---|---|---|---|---|
| 1 | `192.168.10.0/26` | `192.168.10.1` | `192.168.10.62` | `192.168.10.63` |
| 2 | `192.168.10.64/26` | `192.168.10.65` | `192.168.10.126` | `192.168.10.127` |
| 3 | `192.168.10.128/26` | `192.168.10.129` | `192.168.10.190` | `192.168.10.191` |
| 4 | `192.168.10.192/26` | `192.168.10.193` | `192.168.10.254` | `192.168.10.255` |

If the question means the subnet starting at `192.168.10.0/26`, its network is `192.168.10.0`, first usable is `.1`, last usable is `.62`, and broadcast is `.63`.

### Q11. Design subnets for IT (50), HR (30), Finance (20), Management (10).

Use **VLSM** (Variable Length Subnet Masking), assigning the largest network first. Each subnet must fit the requested hosts plus network and broadcast addresses.

- IT needs 50 hosts: 6 host bits give \(2^6 - 2 = 62\) usable addresses → `/26`.
- HR needs 30 hosts: 5 host bits give \(2^5 - 2 = 30\) usable addresses → `/27`.
- Finance needs 20 hosts: 5 host bits are needed → `/27` (30 usable).
- Management needs 10 hosts: 4 host bits give \(2^4 - 2 = 14\) usable addresses → `/28`.

Allocation from `192.168.10.0/24`, with no overlap:

| Department | Network / CIDR | Subnet mask | Usable range | Broadcast | Usable hosts |
|---|---|---|---|---|---:|
| IT (50) | `192.168.10.0/26` | `255.255.255.192` | `192.168.10.1–192.168.10.62` | `192.168.10.63` | 62 |
| HR (30) | `192.168.10.64/27` | `255.255.255.224` | `192.168.10.65–192.168.10.94` | `192.168.10.95` | 30 |
| Finance (20) | `192.168.10.96/27` | `255.255.255.224` | `192.168.10.97–192.168.10.126` | `192.168.10.127` | 30 |
| Management (10) | `192.168.10.128/28` | `255.255.255.240` | `192.168.10.129–192.168.10.142` | `192.168.10.143` | 14 |

The allocations do not overlap and all fit inside `192.168.10.0/24`. The remaining range can be reserved for future use. The HR subnet has exactly 30 usable addresses, so it has no spare host capacity if all 30 are required.

## Section E — Scenario-Based Questions

### Q12. Design a basic network for 45 employees, 5 servers, and 10 network devices.

**Network type:** A LAN within the company building, with an Internet/WAN connection through the ISP.

**Suggested devices and roles:**
- Business-grade router: connects the LAN to the ISP and routes traffic between networks.
- Managed switches with sufficient ports: connect 45 employee endpoints, 5 servers, and 10 network devices. The actual port count should also include access points, uplinks, printers, and spare capacity.
- Firewall: filters inbound/outbound traffic and enforces company security policies; it may be integrated with the router.
- Wireless access points: provide Wi-Fi with secure authentication.
- Servers: host company applications, files, authentication, or other services.
- Ethernet cabling, patch panel, UPS, and network monitoring as appropriate.

**Basic logical design:**

```text
                  Internet / ISP
                       |
                 Router + Firewall
                       |
                 Core / Main Switch
              _________|___________
             |         |           |
        User switches  Servers   Wi-Fi APs
             |         |           |
       Employee PCs  5 servers  Laptops/phones
```

Use separate VLANs or subnets for employees, servers, guests, and management where appropriate. Apply least-privilege access rules, strong Wi-Fi encryption, patching, backups, and logging.

**How an employee reaches a website:** The employee's device resolves the website name using DNS, determines that the destination is outside its local subnet, and sends the packet to its default gateway. The router/firewall applies routing and security rules, then forwards permitted traffic toward the ISP. The web server replies and the response returns through the network to the employee's browser.

### Q13. Local communication works, but a user at 192.168.1.25/24 cannot access an external website. Give troubleshooting steps in order.

1. **Check physical/Wi-Fi connection:** Confirm the network adapter is connected and has no obvious link issue.
2. **Check IP configuration:** On Windows, run `ipconfig /all`. Verify the address is `192.168.1.25`, subnet mask is `255.255.255.0`, and the default gateway and DNS server are configured correctly for the network.
3. **Test the local TCP/IP stack:** Run `ping 127.0.0.1`. If this fails, investigate the local TCP/IP stack.
4. **Test the local network:** Ping another known local device. The scenario says local communication works, which suggests local connectivity is at least partly functioning.
5. **Test the default gateway:** Run `ping <default-gateway-IP>`. If it fails, inspect the gateway address, VLAN, Wi-Fi/LAN connection, and router interface. Note that some routers block ping, so a failed ping alone is not conclusive.
6. **Test external IP connectivity:** Try `ping 8.8.8.8` or use `tracert 8.8.8.8`. If local gateway access works but external connectivity fails, inspect the router's WAN link, routes, ISP connection, and firewall rules. Some destinations block ICMP, so use more than one test.
7. **Test DNS:** Run `nslookup example.com`. If external IP connectivity works but name resolution fails, verify the configured DNS server, try an approved alternate DNS server, and clear the local cache with `ipconfig /flushdns` if appropriate.
8. **Test web access:** Try `https://example.com` and check browser proxy settings, system date/time, TLS errors, and endpoint firewall/security software.
9. **Check router/firewall role:** Confirm the router has a working WAN connection, a valid default route, correct NAT where needed for private IPv4, and no rule blocking the user.
10. **Document findings:** Record command outputs and the first point of failure, make one change at a time, and retest.

**Reasoning:** Since local communication works, the fault may be in the default gateway, router/WAN, DNS, firewall, proxy, or website-specific connection rather than basic local addressing. Test in order to narrow down the cause rather than changing settings randomly.

## Conclusion

This project covers essential cybersecurity principles, network types and devices, Internet communication, IPv4/IPv6 addressing, CIDR and subnet calculations, a basic company network design, and systematic IP troubleshooting. These concepts help build and maintain networks that are reliable, organized, and secure.
