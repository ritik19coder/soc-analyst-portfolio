# Day 3 – Networking Command Practice for SOC Analysts

## Objective

The objective of Day 3 was to practise basic networking commands that are useful for SOC Analyst Level 1 investigations. These commands help collect information about IP configuration, connectivity, DNS resolution, network routes, active connections and basic service discovery.

On Day 2, I studied networking theory. Today, I focused more on practical command usage and screenshot evidence.

---

## Why Command Practice is Important for SOC Analysts

SOC analysts often investigate alerts that include IP addresses, domains, ports, protocols and host details. Basic networking commands help analysts understand whether a system is connected, which DNS records are being resolved, what route traffic is taking and whether there are active network connections.

These commands are useful during:

* Initial alert investigation
* Network troubleshooting
* Suspicious domain analysis
* Failed login investigation
* Malware communication checks
* Basic host investigation
* Evidence collection for reports

---

## Commands Practised

## 1. ipconfig

### Command Used

```powershell
ipconfig
```

### Purpose

The `ipconfig` command shows the IP configuration of a Windows system. It displays details such as the IPv4 address, subnet mask, default gateway and network adapter information.

### SOC Analyst Use

A SOC analyst can use this command to identify the local IP address of a system during investigation. This is useful when checking whether an alert is related to the correct host or network segment.

### Evidence

Screenshot saved as:

```text
07-screenshots/day-3-ipconfig.png
```

---

## 2. ping

### Command Used

```powershell
ping google.com
```

### Purpose

The `ping` command checks whether a system can reach another host over the network. It sends ICMP packets and shows whether replies are received.

### SOC Analyst Use

This command can help confirm basic network connectivity. During investigation, it may be used to check whether a host can reach a domain or IP address. However, some systems block ICMP, so no reply does not always mean the host is offline.

### Evidence

Screenshot saved as:

```text
07-screenshots/day-3-ping.png
```

---

## 3. nslookup

### Command Used

```powershell
nslookup google.com
```

### Purpose

The `nslookup` command is used to query DNS records. It shows which IP address is linked to a domain name.

### SOC Analyst Use

DNS investigation is important in SOC work because phishing websites, malware and command-and-control infrastructure often use suspicious domains. SOC analysts can use DNS information to understand where a domain resolves and whether it may be suspicious.

### Evidence

Screenshot saved as:

```text
07-screenshots/day-3-nslookup.png
```

---

## 4. tracert

### Command Used

```powershell
tracert google.com
```

### Purpose

The `tracert` command shows the path that packets take from the local system to a destination. It displays each hop between the source and destination.

### SOC Analyst Use

This command can help analysts understand the route traffic is taking. It can also be useful during network troubleshooting or when investigating connectivity issues.

### Evidence

Screenshot saved as:

```text
07-screenshots/day-3-tracert.png
```

---

## 5. netstat

### Command Used

```powershell
netstat -ano
```

### Purpose

The `netstat -ano` command shows active network connections, listening ports and process IDs on a Windows system.

### SOC Analyst Use

This command is useful for identifying unusual connections or unexpected listening ports. A SOC analyst can use the process ID shown in the output to investigate which process is responsible for a connection.

### Evidence

Screenshot saved as:

```text
07-screenshots/day-3-netstat.png
```

---

## 6. Nmap Safe Scan

### Command Used

```powershell
nmap -sV scanme.nmap.org
```

### Purpose

The `nmap -sV` command checks open ports and attempts to detect service versions. For this task, I used `scanme.nmap.org`, which is provided by Nmap for legal testing and learning purposes.

### SOC Analyst Use

Nmap helps understand open ports and services on a target. For SOC analysts, this knowledge is useful because open services can increase attack surface and may appear in vulnerability assessment or incident investigation reports.

### Evidence

Screenshot saved as:

```text
07-screenshots/day-3-nmap-scan.png
```

---

## Practical Learning Summary

Today I practised important networking commands used in basic security investigation. I learned how to check IP configuration, test connectivity, resolve domains, trace network routes, view active connections and perform a safe Nmap service scan.

The most useful command from a SOC perspective was `netstat -ano` because it shows active connections and process IDs. This can help during suspicious connection investigation. The `nslookup` command was also useful because DNS investigation is common in phishing and malware analysis.

---

## SOC Investigation Example

Example alert:

```text
Suspicious outbound connection detected from internal host to unknown external IP.
```

As a SOC analyst, I could use the following process:

1. Use `ipconfig` to confirm the local host IP address.
2. Use `netstat -ano` to check active connections and identify the related process ID.
3. Use `nslookup` to investigate any suspicious domain involved.
4. Use `tracert` to understand the network route.
5. Review screenshots and command outputs as evidence.
6. Document findings in an investigation report.

This shows how basic networking commands can support a real SOC investigation.

---

## Screenshots Collected

The following screenshots were collected as evidence:

```text
day-3-ipconfig.png
day-3-ping.png
day-3-nslookup.png
day-3-tracert.png
day-3-netstat.png
day-3-nmap-scan.png
```

Screenshots are stored in the `07-screenshots` folder.

---

## Key Skills Practised

* Windows networking command usage
* DNS lookup
* Connectivity testing
* Route tracing
* Active connection checking
* Basic Nmap service scanning
* SOC-style evidence collection
* Markdown documentation for GitHub

---

## Diary Reflection

Today I completed Day 3 of my SOC Analyst Level 1 preparation plan. I focused on practical networking command usage and collected screenshots as evidence. I practised commands such as `ipconfig`, `ping`, `nslookup`, `tracert`, `netstat -ano` and a safe Nmap scan on `scanme.nmap.org`.

This task helped me understand how networking commands support SOC investigations. I also learned how to document command usage in a professional way for my GitHub portfolio.

---

##
