# Day 3 Networking Command Practice for SOC Analysts

## Objective

The objective of this exercise was to practise basic networking commands used during entry-level security investigations. The commands help an analyst confirm connectivity, resolve domains, trace network paths and review active connections.

## Environment and Scope

- Environment: Kali Linux lab machine
- Activity: Basic network troubleshooting and evidence collection
- Scope: Benign commands and public services only
- Privacy rule: Local gateway details, household-network scans and unnecessary device information are excluded from the public portfolio

## Commands Practised

### Ping

~~~bash
ping google.com
~~~

**ping** sends ICMP echo requests to test whether a destination responds and to measure approximate round-trip time.

**SOC relevance:** It can support initial connectivity checks, although a failed response does not prove that a host is offline because ICMP may be blocked.

**Evidence:** [Ping output](../07-screenshots/day-3-ping.png)

### Nslookup

~~~bash
nslookup google.com
~~~

**nslookup** queries DNS and shows the addresses returned for a domain.

**SOC relevance:** DNS data can help an analyst investigate suspicious domains, phishing infrastructure and possible command-and-control activity. A DNS result alone does not establish that a domain is malicious.

**Evidence:** [DNS lookup output](../07-screenshots/day-3-nslookup.png)

### Traceroute

~~~bash
traceroute google.com
~~~

**traceroute** displays the network hops observed between the source system and a destination.

**SOC relevance:** It can support route and connectivity troubleshooting. Missing hops may occur when intermediate devices do not return responses.

The local first-hop gateway has been redacted from the public screenshot.

**Evidence:** [Traceroute output](../07-screenshots/day-3-traceroute.png)

### Traceroute Help

~~~bash
traceroute
~~~

Running the command without the required destination displays its usage and available options. Reviewing built-in help is a useful way to verify syntax before collecting evidence.

**Evidence:** [Traceroute command help](../07-screenshots/day-3-traceroute-help.png)

### Netstat

~~~bash
netstat
~~~

**netstat** displays active network connections. Depending on the options and permissions used, it can also display listening services, addresses, ports and process information.

**SOC relevance:** Active connections can provide an initial lead during host investigation, but they must be correlated with process, user, time and destination evidence. On modern Linux systems, **ss** is commonly used as an alternative.

**Evidence:** [Netstat output](../07-screenshots/day-3-netstat.png)

## Nmap Evidence Status

An earlier screenshot displayed a scan of a private household subnet and did not match the public target described in the original note. It has been excluded from the proposed portfolio update.

A new Nmap exercise will be completed later against an isolated lab system or another target that explicitly permits scanning. The final evidence will document the authorised target, command, result, interpretation and limitations.

## Example Investigation Use

Example alert:

~~~text
Suspicious outbound connection detected from an internal host to an unfamiliar destination.
~~~

An entry-level investigation could include:

1. Confirm the affected host and its assigned network details.
2. Review active connections and identify the related process where possible.
3. Resolve any associated domain and record the returned DNS information.
4. Compare the destination, time and user activity with expected behaviour.
5. Preserve relevant evidence and document any uncertainty.
6. Escalate when the evidence indicates malicious activity or the scope remains unclear.

These commands support initial triage, but they do not replace SIEM, EDR, firewall, DNS or proxy-log evidence.

## Skills Demonstrated

- Basic Linux network troubleshooting
- DNS resolution checks
- Connectivity and route analysis
- Active-connection review
- Evidence collection and redaction
- Ethical documentation of lab activity

## Learning Summary

This exercise connected basic networking commands with SOC investigation tasks. The most important lesson was that command output needs context: a reachable host is not automatically trustworthy, an unfamiliar connection is not automatically malicious and a DNS result must be validated against other evidence.
