# Day 2 – Networking Basics for SOC Analysts

## Objective

The objective of today’s task is to understand the basic networking concepts required for SOC Analyst Level 1 roles. Networking is important in cybersecurity because most alerts, logs and incidents include information such as IP addresses, ports, protocols, domains and network traffic.

As a beginner SOC analyst, I need to understand how devices communicate so I can investigate suspicious activity, failed logins, phishing links, malware connections and unusual traffic patterns.

---

## Why Networking is Important for SOC Analysts

Networking helps SOC analysts understand communication between systems. When an alert appears in a SIEM tool, it usually contains details such as:

* Source IP address
* Destination IP address
* Port number
* Protocol
* Domain name
* Time of connection
* User or host information

For example, if there are multiple failed login attempts from an unknown IP address to port 3389, a SOC analyst should understand that port 3389 is commonly used for Remote Desktop Protocol. This helps the analyst decide whether the activity may be suspicious.

Networking knowledge is also useful for checking DNS activity, blocked firewall connections, suspicious outbound traffic, unusual login locations and possible malware communication.

---

## Basic Networking Concepts

## IP Address

An IP address is a unique address used to identify a device on a network. It allows devices to communicate with each other.

Example:

```text
192.168.1.10
```

In SOC work, IP addresses help identify where traffic is coming from and where it is going. Analysts often check whether an IP address is internal, external, trusted or suspicious.

---

## MAC Address

A MAC address is a physical hardware address assigned to a network interface card.

Example:

```text
00:1A:2B:3C:4D:5E
```

MAC addresses are mostly used inside local networks. SOC analysts may find MAC addresses in DHCP logs, endpoint logs or network device logs.

---

## DNS

DNS stands for Domain Name System. It converts domain names into IP addresses.

Example:

```text
google.com → IP address
```

DNS is very important in cybersecurity because phishing websites, malware and command-and-control servers often use suspicious domains. SOC analysts can investigate DNS logs to identify unusual domain lookups.

---

## DHCP

DHCP stands for Dynamic Host Configuration Protocol. It automatically assigns IP addresses to devices on a network.

DHCP logs are useful because they can show which device was using a specific IP address at a specific time.

---

## TCP

TCP stands for Transmission Control Protocol. It is reliable because it checks that data is delivered correctly.

Common services that use TCP include:

```text
HTTP
HTTPS
SSH
FTP
SMTP
```

TCP is commonly used for web browsing, file transfer, email and remote login.

---

## UDP

UDP stands for User Datagram Protocol. It is faster than TCP but does not confirm delivery in the same way.

Common examples of UDP usage include:

```text
DNS
VoIP
Streaming
Gaming
```

SOC analysts should understand UDP because some network scans, DNS activity and suspicious traffic may use UDP.

---

## HTTP and HTTPS

HTTP stands for Hypertext Transfer Protocol. It is used for web communication but does not encrypt data.

Example:

```text
http://example.com
```

HTTPS is the secure version of HTTP. It encrypts communication between the browser and the website.

Example:

```text
https://example.com
```

From a SOC point of view, HTTPS is more secure than HTTP, but suspicious activity can still happen over HTTPS. Analysts still need to check the domain, IP address, certificate, URL pattern and user activity.

---

## Common Ports for SOC Analysts

| Port | Service | Purpose                 |
| ---- | ------- | ----------------------- |
| 21   | FTP     | File transfer           |
| 22   | SSH     | Secure remote login     |
| 25   | SMTP    | Sending email           |
| 53   | DNS     | Domain name resolution  |
| 80   | HTTP    | Web traffic             |
| 110  | POP3    | Email retrieval         |
| 143  | IMAP    | Email retrieval         |
| 443  | HTTPS   | Secure web traffic      |
| 445  | SMB     | Windows file sharing    |
| 3389 | RDP     | Remote Desktop Protocol |

Knowing common ports helps SOC analysts quickly understand what type of service or activity may be involved in an alert.

---

## Firewall

A firewall controls incoming and outgoing network traffic based on security rules.

In SOC investigations, firewall logs can help identify:

* Blocked connections
* Allowed suspicious traffic
* Repeated connection attempts
* Traffic from suspicious IP addresses
* Connections to unusual ports

---

## VPN

A VPN creates an encrypted connection between a user and a network. It is commonly used for secure remote access.

SOC analysts may investigate VPN logs to check unusual login locations, failed login attempts or suspicious access times.

---

## Proxy

A proxy acts as an intermediate server between a user and the internet. It can be used for monitoring, filtering and controlling web traffic.

SOC analysts may check proxy logs to identify suspicious websites, blocked URLs or unusual browsing activity.

---

## NAT

NAT stands for Network Address Translation. It allows multiple internal devices to share one public IP address.

NAT is useful in networks, but analysts may need extra logs to identify the exact internal device behind a public IP connection.

---

## Commands Practised

Today I practised basic networking commands that can help collect network information during investigation.

## Check IP Address

Linux:

```bash
ip a
```

Windows:

```powershell
ipconfig
```

Purpose: This command shows the IP address and network interface details of the system.

---

## Test Network Connectivity

```bash
ping google.com
```

Purpose: This command checks whether the system can reach another host.

---

## Trace Network Route

Linux:

```bash
traceroute google.com
```

Windows:

```powershell
tracert google.com
```

Purpose: This command shows the route packets take to reach a destination.

---

## DNS Lookup

```bash
nslookup google.com
```

Purpose: This command finds the IP address linked to a domain name.

---

## Detailed DNS Lookup

```bash
dig google.com
```

Purpose: This command gives more detailed DNS query information.

---

## SOC Analyst Example

Example alert:

```text
Multiple failed login attempts detected from IP address 185.xx.xx.xx to RDP port 3389.
```

As a SOC analyst, I would investigate:

* Source IP address
* Destination system
* Port number
* Number of failed attempts
* Time of activity
* Whether the IP address is internal or external
* Whether the login later became successful
* Related Windows Event Viewer logs
* Related SIEM alerts

This example shows why networking knowledge is important. Without understanding IP addresses, ports and protocols, it would be difficult to understand the alert properly.

---

## Key Learning Summary

Today I learned the basic networking concepts required for SOC Analyst Level 1 work. I studied IP addresses, MAC addresses, DNS, DHCP, TCP, UDP, HTTP, HTTPS, firewalls, VPNs, proxies, NAT and common ports.

I also practised useful networking commands such as `ip a`, `ipconfig`, `ping`, `traceroute`, `tracert`, `nslookup` and `dig`.

This task helped me understand how networking supports SOC investigations. These concepts will help me analyse logs, alerts, suspicious IP addresses, domains and network traffic more confidently.

---

## Evidence to Add Later

Screenshots can be saved in the `07-screenshots` folder:

```text
day-2-ipconfig.png
day-2-ping.png
day-2-nslookup.png
day-2-traceroute.png
```

---

## Diary Reflection

Today I completed Day 2 of my SOC Analyst Level 1 preparation plan. I focused on networking basics because they are important for analysing security alerts and logs. I learned about IP addresses, DNS, DHCP, TCP, UDP, HTTP, HTTPS, common ports, firewalls, VPNs, proxies and NAT. I also practised basic commands that can help during network investigation. I created this Markdown note as evidence of my learning and prepared it for my GitHub portfolio.

---

## GitHub Commit Message

```text
Day 2: Add networking basics for SOC analysts
```
