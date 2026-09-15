# NETWORKWALKS-B083-WK2-FOOTPRINTING-NETWORK-SCANNING

# Footprinting & Network Scanning — Kali Linux

## Project Overview

This project covers the fundamentals of **footprinting, information gathering, and network scanning** using Kali Linux.

The objective is to understand how publicly available information about a domain or network can be collected during the reconnaissance phase of a cybersecurity assessment.

The project uses various Kali Linux tools to gather information such as **domain registration details, web technologies, DNS records, HTTP headers, Web Application Firewalls, IP addresses, live hosts, MAC addresses, and network topology**.

All activities are performed within a **controlled and authorized environment** for educational and cybersecurity training purposes.

---

## Objectives

The project aims to:

- Understand the fundamentals of **footprinting and reconnaissance**.
- Gather domain registration information using `whois`.
- Identify web technologies using `whatweb`.
- Resolve domain names to IP addresses using `nslookup`.
- Inspect HTTP response headers using `curl`.
- Detect Web Application Firewalls using `wafw00f`.
- Enumerate DNS records using `dnsrecon`.
- Identify the local IP address and subnet in Kali Linux.
- Discover live hosts within an authorized network.
- Determine the number of active hosts in a subnet.
- Identify the IP addresses of discovered hosts.
- Identify MAC addresses of hosts where available.
- Use **Nmap** for network discovery and scanning.
- Document the results obtained during the reconnaissance and scanning process.

---

## Purpose of the Project

The purpose of this project is to develop practical knowledge of the **reconnaissance and network discovery stages of a cybersecurity assessment**.

Footprinting allows security professionals to collect information about a target before performing further security testing. Network scanning complements this process by identifying devices and systems that are active within an authorized network.

The project provides hands-on experience with commonly used cybersecurity tools available in Kali Linux and helps build a foundation for future activities involving **network security, vulnerability assessment, ethical hacking, and penetration testing**.

---

## Technologies & Tools Used

- **Kali Linux**
- **Nmap** — Network discovery and scanning
- **Whois** — Domain registration and ownership information
- **WhatWeb** — Web technology fingerprinting
- **Nslookup** — DNS queries and IP resolution
- **cURL** — HTTP request and response-header analysis
- **Wafw00f** — Web Application Firewall detection
- **DNSRecon** — DNS record enumeration

---

# Part 1 — Footprinting

## Footprinting Overview

Footprinting is the process of collecting information about a target before performing further security testing.

The information collected during footprinting can include:

- Domain registration information
- IP addresses
- DNS records
- Web technologies
- HTTP response information
- Web Application Firewall information
- Other publicly available network details

The following Kali Linux tools were used for the footprinting exercises.

---

## Task 1 — Domain Registration Information using Whois

The `whois` command was used to obtain domain registration information.

### Command

```bash
whois <target-domain>
```

### Example

```bash
whois example.com
```

### Information Observed

The output can contain information such as:

- Domain registrar
- Registration dates
- Expiration date
- Domain status
- Name servers
- Registrar information

### Result

The `whois` command demonstrated how domain registration information can be collected during the initial reconnaissance stage.

---

## Task 2 — Web Technology Fingerprinting using WhatWeb

`WhatWeb` was used to identify technologies and services associated with a website.

### Command

```bash
whatweb <target-domain>
```

### Example

```bash
whatweb example.com
```

### Information Observed

WhatWeb can identify technologies such as:

- Web servers
- Content Management Systems
- JavaScript frameworks
- Web technologies
- HTTP headers
- Cookies
- Plugins and other web-related components

### Result

The scan provided an overview of the technologies used by the target web application.

---

## Task 3 — Domain to IP Resolution using Nslookup

`nslookup` was used to resolve a domain name to its corresponding IP address.

### Command

```bash
nslookup <target-domain>
```

### Example

```bash
nslookup example.com
```

### Information Observed

The command can provide:

- Domain name
- IPv4 address
- IPv6 address, when available
- DNS server information
- DNS resolution details

### Result

The domain was successfully resolved to its associated IP address through DNS lookup.

---

## Task 4 — HTTP Response Headers using cURL

The `curl` utility was used to send an HTTP request and inspect the response headers returned by the web server.

### Command

```bash
curl -I https://<target-domain>
```

### Example

```bash
curl -I https://example.com
```

### Information Observed

HTTP response headers can provide information such as:

- HTTP status code
- Server information
- Content type
- Cookies
- Redirect information
- Security-related headers

### Result

The HTTP response headers were examined to understand how the target web server responds to requests.

---

## Task 5 — Web Application Firewall Detection using Wafw00f

`wafw00f` was used to identify whether a Web Application Firewall (WAF) is present in front of a web application.

### Command

```bash
wafw00f <target-domain>
```

### Example

```bash
wafw00f example.com
```

### Information Observed

The tool attempts to determine:

- Whether a WAF is present
- The type or vendor of the WAF, when identifiable
- Whether the target is protected by a web application firewall

### Result

The WAF detection process provided information about the security layer protecting the web application.

---

## Task 6 — DNS Enumeration using DNSRecon

`dnsrecon` was used to enumerate DNS information associated with a domain.

### Command

```bash
dnsrecon -d <target-domain>
```

### Example

```bash
dnsrecon -d example.com
```

### Information Observed

DNSRecon can identify DNS information such as:

- A records
- AAAA records
- MX records
- NS records
- SOA records
- TXT records
- Other available DNS information

### Result

The DNS enumeration process provided a broader view of the target's DNS infrastructure.

---

# Part 2 — Network Scanning

## Network Scanning Overview

Network scanning is used to identify active systems and understand the structure of a network.

For this section, **Nmap** was used from Kali Linux to perform network discovery and identify hosts within the authorized laboratory subnet.

The scanning activities were performed against the **private virtual network created for the cybersecurity laboratory**.

---

## Task 1 — Install and Verify Nmap

Nmap is commonly available by default in Kali Linux.

The installation can be verified using:

```bash
nmap --version
```

If Nmap is not installed, it can be installed using:

```bash
sudo apt update
sudo apt install nmap
```

### Result

Nmap was successfully installed and verified on Kali Linux.

---

## Task 2 — Find the Local IP Address and LAN Subnet

The local IP address and network configuration were identified using:

```bash
ip addr
```

or:

```bash
ip -4 addr
```

The routing information can also be checked using:

```bash
ip route
```

### Information Identified

The following information was recorded:

- Local IPv4 address
- Network interface
- Subnet mask / CIDR notation
- Default gateway
- Network range

### Example

```text
IP Address: 192.168.56.10
Subnet: 192.168.56.0/24
Gateway: 192.168.56.1
```

> The values above are examples only. The actual values depend on the configured VirtualBox network.

### Result

The local IP address and subnet used by the Kali Linux machine were identified.

---

## Task 3 — Find Live Hosts in the IP Subnet

Nmap was used to perform host discovery across the authorized subnet.

### Command

```bash
nmap -sn <subnet>
```

### Example

```bash
nmap -sn 192.168.56.0/24
```

The `-sn` option performs **host discovery without performing a port scan**.

### Result

Nmap identified the hosts that were responding within the specified subnet.

---

## Task 4 — Determine the Number of Live Hosts

The results from the host discovery scan were examined to determine how many hosts were active.

### Command

```bash
nmap -sn <subnet>
```

### Example

```bash
nmap -sn 192.168.56.0/24
```

The output contains entries similar to:

```text
Nmap scan report for 192.168.56.1
Host is up.

Nmap scan report for 192.168.56.10
Host is up.
```

The number of hosts reported as **up** was recorded.

### Result

The total number of live hosts detected within the authorized subnet was documented.

---

## Task 5 — Identify the IP Addresses of Live Hosts

The Nmap host-discovery results were used to identify the IPv4 addresses of active hosts.

### Command

```bash
nmap -sn <subnet>
```

### Example

```bash
nmap -sn 192.168.56.0/24
```

### Information Recorded

For each live host:

- IP address
- Hostname, when available
- Host availability status

### Result

The IP addresses of the discovered live hosts were recorded from the Nmap scan results.

---

## Task 6 — Identify the MAC Addresses of Live Hosts

Nmap can display MAC addresses when the scan has sufficient network-level access, particularly when scanning hosts on the same local Ethernet network.

### Command

```bash
sudo nmap -sn <subnet>
```

### Example

```bash
sudo nmap -sn 192.168.56.0/24
```

### Example Output

```text
Nmap scan report for 192.168.56.10
Host is up.
MAC Address: XX:XX:XX:XX:XX:XX
```

### Information Recorded

The following information was documented where available:

- IP address
- MAC address
- MAC address vendor

### Result

MAC addresses of locally discoverable hosts were identified using Nmap.

> MAC addresses may not be displayed for every host, especially when the target is not on the same local network segment or when the network configuration prevents their discovery.

---

## Task 7 — Display and Save Network Scan Results

The Nmap results were documented and saved for analysis and reporting.

### Save Nmap Output as Text

```bash
nmap -sn <subnet> -oN nmap-scan.txt
```

### Save Output in XML Format

```bash
nmap -sn <subnet> -oX nmap-scan.xml
```

### Save in All Major Formats

```bash
nmap -sn <subnet> -oA network-scan
```

This creates output files including:

```text
network-scan.nmap
network-scan.xml
network-scan.gnmap
```

### Result

The network discovery results were saved for documentation and further analysis.

---

# Network Scanning Workflow

The overall network scanning process followed these steps:

```text
Identify Local IP
       ↓
Identify Subnet
       ↓
Perform Host Discovery
       ↓
Identify Live Hosts
       ↓
Record IP Addresses
       ↓
Identify MAC Addresses
       ↓
Save Scan Results
       ↓
Document Network Topology
```

---

# Footprinting Workflow

The footprinting process followed this sequence:

```text
Domain
  ↓
Whois
  ↓
Domain Registration Information
  ↓
WhatWeb
  ↓
Web Technology Identification
  ↓
Nslookup
  ↓
IP Address Resolution
  ↓
cURL
  ↓
HTTP Header Analysis
  ↓
Wafw00f
  ↓
WAF Detection
  ↓
DNSRecon
  ↓
DNS Record Enumeration
```

---

# Commands Used

## Footprinting Commands

### Whois

```bash
whois <target-domain>
```

### WhatWeb

```bash
whatweb <target-domain>
```

### Nslookup

```bash
nslookup <target-domain>
```

### cURL

```bash
curl -I https://<target-domain>
```

### Wafw00f

```bash
wafw00f <target-domain>
```

### DNSRecon

```bash
dnsrecon -d <target-domain>
```

---

## Network Scanning Commands

### Display IP Configuration

```bash
ip addr
```

### Display IPv4 Configuration

```bash
ip -4 addr
```

### Display Routing Information

```bash
ip route
```

### Discover Live Hosts

```bash
nmap -sn <subnet>
```

### Discover Hosts with MAC Addresses

```bash
sudo nmap -sn <subnet>
```

### Save Normal Output

```bash
nmap -sn <subnet> -oN nmap-scan.txt
```

### Save Output in Multiple Formats

```bash
nmap -sn <subnet> -oA network-scan
```

---

# Results & Observations

The practical exercises provided experience in collecting information from both **domain-level and network-level sources**.

## Footprinting

The footprinting exercises demonstrated how different tools can provide different types of information about a domain:

| Tool | Purpose |
|---|---|
| `whois` | Domain registration information |
| `whatweb` | Web technology fingerprinting |
| `nslookup` | DNS and IP resolution |
| `curl` | HTTP response-header analysis |
| `wafw00f` | WAF detection |
| `dnsrecon` | DNS record enumeration |

## Network Scanning

Nmap was used to:

- Identify the local network range.
- Discover active hosts.
- Determine the number of live hosts.
- Record IP addresses.
- Identify MAC addresses where available.
- Save network discovery results for documentation.

---

# Lab Screenshots

Screenshots documenting the practical work will be added to this section.

## Footprinting

### Whois

![Whois](screenshot-whois.png)

### WhatWeb

![WhatWeb](screenshot-whatweb.png)

### Nslookup

![Nslookup](screenshot-nslookup.png)

### cURL

![cURL](screenshot-curl.png)

### Wafw00f

![Wafw00f](screenshot-wafw00f.png)

### DNSRecon

![DNSRecon](screenshot-dnsrecon.png)

---

## Network Scanning

### Local IP and Subnet

![IP Configuration](screenshot-ip-address.png)

### Nmap Host Discovery

![Nmap Host Discovery](screenshot-nmap-host-discovery.png)

### Live Hosts

![Live Hosts](screenshot-live-hosts.png)

### MAC Address Discovery

![MAC Addresses](screenshot-mac-addresses.png)

### Saved Nmap Results

![Nmap Results](screenshot-nmap-results.png)

### Network Topology

![Network Topology](screenshot-network-topology.png)

---

# What I Learned

This project provided practical experience with the reconnaissance and network discovery stages of a cybersecurity assessment.

### 1. Footprinting

I learned how publicly available information can be collected about a target before performing further security testing.

### 2. Domain Information Gathering

Using `whois`, I learned how domain registration information and DNS-related details can be examined during reconnaissance.

### 3. Web Technology Fingerprinting

Using WhatWeb, I learned how to identify technologies and components associated with a web application.

### 4. DNS Enumeration

Using `nslookup` and DNSRecon, I learned how DNS can be queried to identify domain records, name servers, mail servers, IP addresses, and other available information.

### 5. HTTP Header Analysis

Using cURL, I learned how HTTP response headers can provide useful information about how a web server responds to requests.

### 6. WAF Detection

Using Wafw00f, I learned how security researchers can identify the presence of a Web Application Firewall protecting a web application.

### 7. Network Discovery

Using Nmap, I learned how to identify active systems within an authorized network and determine their IP addresses.

### 8. MAC Address Discovery

I learned how MAC addresses can be obtained during local network discovery when the network environment allows Layer 2 information to be observed.

### 9. Network Topology

The scanning process helped me understand how devices within a network can be identified and represented as part of a basic network topology.

### 10. Documentation

I learned the importance of recording commands, results, screenshots, network information, and observations throughout a cybersecurity assessment.

---

# Security & Ethical Use

All footprinting and network scanning activities in this project are intended for **educational purposes and authorized security testing only**.

Network scanning or reconnaissance against systems without permission may violate organizational policies, laws, or regulations.

The Nmap activities described in this project should only be performed against **networks and systems that you own or have explicit authorization to test**.

---

# Tools & Resources

- **Kali Linux:** https://www.kali.org/
- **Nmap:** https://nmap.org/
- **Whois:** https://www.whois.com/
- **WhatWeb:** https://github.com/urbanadventurer/WhatWeb
- **Wafw00f:** https://github.com/EnableSecurity/wafw00f
- **DNSRecon:** https://github.com/darkoperator/dnsrecon
- **cURL:** https://curl.se/

---

# Author

*Aditya Choubey*  
**Computer Science Student**

[LinkedIn](https://www.linkedin.com/in/adityachby/)

---

## Project Information

**Program Name:** Cybersecurity at Networkwalks  
**Week:** 02  
**Project:** Footprinting & Network Scanning  
**Platform:** Kali Linux  
**Repository:** GitHub
