# PENETRATION TESTING REPORT

## FOOTPRINTING & RECONNAISSANCE PHASE

### W2-PM1 | CYBERSECURITY | NETWORKWALKS

<table>
  <tr>
    <td align="center"><b>Pentester Name<br>(Cybersecurity Professional)</b></td>
    <td><b>Aysən Əliquliyeva</b></td>
  </tr>

  <tr>
    <td align="center"><b>Program/Batch</b></td>
    <td>B082-Networkwalks</td>
  </tr>

  <tr>
    <td align="center"><b>Date</b></td>
    <td>19 August 2026</td>
  </tr>

  <tr>
    <td align="center"><b>Modules Completed</b></td>
    <td>W2-PM1 (Multiple Kali Tools)</td>
  </tr>

  <tr>
    <td align="center"><b>Client/Target</b></td>
    <td>Networkwalks (secured written permission already)</td>
  </tr>

  <tr>
    <td align="center"><b>Permission secured from client?</b></td>
    <td>Yes</td>
  </tr>

  <tr>
    <td align="center"><b>Phases Covered</b></td>
    <td>
      <b>Phase 1:</b> Reconnaissance & Footprinting<br>
      <b>Phase 2-5:</b> In Progress
    </td>
  </tr>
</table>

## 1. Liability Disclaimer

All activities documented in this report were performed strictly for **educational and cybersecurity research purposes**.

The **Footprinting & Reconnaissance with Multiple Kali Tools (W2-PM1)** activities were conducted against `networkwalks.com` within the scope of the assigned cybersecurity training environment.

The **Footprinting & Reconnaissance with theHarvester (W2-PM4)** activity was performed against `microsoft.com` using publicly available information sources as part of a **passive reconnaissance exercise**. No attempt was made to gain unauthorized access, bypass security controls, or modify any data.

The **Network Scanning with Zenmap (W2-PM5)** activities were performed only on **my own local LAN network and devices under my control**.

No unauthorized access, exploitation, or modification of systems was performed during these exercises.

> **⚠️ Important:** The tools and techniques demonstrated in this report must only be used for legitimate educational, research, and authorized security testing purposes. Unauthorized access, scanning, exploitation, or misuse may violate applicable laws and regulations.

All activities were completed as part of assigned cybersecurity training exercises. Any misuse of the techniques described in this report is the sole responsibility of the individual performing such actions.

## 2. Introduction

This report documents three practical cybersecurity activities completed as part of the Week 2 project modules: **Footprinting & Reconnaissance with Multiple Kali Tools (W2-PM1)**, **Footprinting & Reconnaissance with theHarvester (W2-PM4)**, and **Network Scanning with Zenmap (W2-PM5)**.

The first activity focused on gathering publicly available information about `networkwalks.com` using **WHOIS, WhatWeb, Nslookup, Curl, Wafw00f, and DNSRecon**. These tools were used to identify domain registration details, web technologies, IP addresses, HTTP response headers, Web Application Firewall information, and DNS records.

The second activity involved using **theHarvester** against `microsoft.com` to perform passive reconnaissance. Publicly available sources were used to collect information such as email addresses, hosts, and subdomains related to the target organization.

The third activity focused on **local network discovery using Zenmap**, the graphical interface for Nmap. My local IP address and LAN subnet were identified, followed by a Ping Scan of the `192.168.1.0/24` network. The scan identified active hosts, their IP and MAC addresses, and a visual network topology was generated.

All activities were performed within an authorized educational scope. The purpose of these exercises was to understand how reconnaissance and network scanning techniques can be used to gather information about systems and networks before later stages of a penetration testing process.

## 3. Tools Used

The table below lists each tool used in this report and its purpose.

| **Tool** | **Purpose** |
|---|---|
| **Kali Linux** | Operating system used to perform the footprinting and reconnaissance activities. |
| **WHOIS** | Used to obtain domain registration details such as registrar information, registration dates, and name servers. |
| **WhatWeb** | Used to fingerprint web technologies such as the web server, CMS, plugins, frameworks, and IP address. |
| **Nslookup** | Used to resolve a domain name to its corresponding IP address using DNS. |
| **Curl (`curl -I`)** | Used to inspect HTTP response headers and identify technical information exposed by the web server. |
| **Wafw00f** | Used to detect whether the target website is protected by a Web Application Firewall (WAF). |
| **DNSRecon** | Used to enumerate DNS records such as NS, MX, TXT, SPF, SRV, and other DNS-related information. |
| **theHarvester** | Used for passive reconnaissance to collect publicly available information such as email addresses, hosts, and subdomains related to a target organization. |
| **Windows** | Operating system used for the local network scanning activity with Zenmap. |
| **Windows CMD** | Used to identify the local IP address, subnet mask, default gateway, and MAC address using commands such as `ipconfig` and `ipconfig /all`. |
| **Zenmap** | Graphical user interface for Nmap used to scan the local LAN subnet, discover active hosts, identify IP and MAC addresses, and generate a network topology. |
| **Nmap** | Network scanning engine used by Zenmap to perform host discovery and Ping Scan operations on the local network. |

## 4. Activities Performed

### 4.1 Footprinting & Reconnaissance

I performed footprinting and reconnaissance activities against `networkwalks.com` using multiple Kali Linux tools. The objective of this activity was to collect publicly available technical information about the target and understand its external infrastructure.

The following tools were used:

- **WHOIS** – to collect domain registration information, registrar details, registration dates, and name servers.
- **WhatWeb** – to fingerprint technologies used by the target website.
- **Nslookup** – to resolve the target domain to its IP address.
- **Curl (`curl -I`)** – to inspect HTTP response headers.
- **Wafw00f** – to detect whether the website was protected by a Web Application Firewall.
- **DNSRecon** – to enumerate DNS records and other DNS-related information.

Using `nslookup`, the domain `networkwalks.com` was resolved to:

`192.232.216.135`

The HTTP response headers collected using Curl returned an **HTTP/2 200** response and exposed technical information related to the web server and WordPress application.

Wafw00f identified the following Web Application Firewall:

`ModSecurity (SpiderLabs)`

DNSRecon provided additional information about the target's DNS infrastructure, including name servers, mail-related records, TXT/SPF records, and service records.

These activities demonstrated how different reconnaissance tools can be combined to create a technical profile of a target using publicly available information.

---

### 4.2 Network Scanning with Zenmap

For the network scanning activity, I used **Zenmap**, the graphical interface for Nmap, to perform host discovery on my own local LAN network.

First, I used the Windows `ipconfig` command to identify my local network configuration.

The following information was identified:

- **Local IPv4 Address:** `192.168.1.67`
- **Subnet Mask:** `255.255.255.0`
- **LAN Subnet:** `192.168.1.0/24`
- **Default Gateway:** `192.168.1.254`

The following subnet was entered as the target in Zenmap:

`192.168.1.0/24`

A Ping Scan was performed using:

`nmap -sn 192.168.1.0/24`

The scan identified **3 live hosts**:

- `192.168.1.64`
- `192.168.1.67`
- `192.168.1.254`

The following MAC addresses were identified:

| **IP Address** | **MAC Address** |
|---|---|
| `192.168.1.64` | `F6:AF:7C:27:0D:82` |
| `192.168.1.67` | `14-B5-CD-15-18-AF` |
| `192.168.1.254` | `EC:A2:A0:0A:62:C0` |

The MAC address of my own computer was verified separately using:

`ipconfig /all`

After completing the scan, I opened the **Topology** section in Zenmap to visually display the discovered devices and saved the topology in PDF format.

This activity demonstrated how network scanning can be used to identify active hosts, IP addresses, MAC addresses, and the basic topology of a local network.

---

### 4.3 Footprinting & Reconnaissance with theHarvester

I performed passive reconnaissance against `microsoft.com` using **theHarvester** in Kali Linux.

The objective of this activity was to gather publicly available information related to the target organization from external data sources.

For the first task, I used **Baidu** as the data source and set the maximum number of results to 1000.

The following command was executed:

`theHarvester -d microsoft.com -l 1000 -b baidu`

In this command:

- `-d` specifies the target domain.
- `-l` specifies the maximum number of results.
- `-b` specifies the data source.

For the second task, I used all supported sources and limited the maximum number of results to 50.

The following command was executed:

`theHarvester -d microsoft.com -l 50 -b all`

theHarvester can collect publicly available information related to a target organization, including:

- Email addresses
- Subdomains
- Hosts
- Employee-related information
- Other publicly exposed infrastructure information

The activity demonstrated how **passive reconnaissance** can be used to gather information from public sources without attempting to gain unauthorized access to the target systems.

The collected information can help cybersecurity professionals understand an organization's publicly exposed information and evaluate its external attack surface.

## 5. Risk Analysis / Impact

Based on the information collected during the **footprinting, passive reconnaissance, and network scanning activities**, the following potential security risks and observations were identified.

| # | **Risk / Finding**                                    | **Evidence / Observation**                                                                                                    | **Potential Impact**                                                                                                                                     | **Risk Level** |
| - | ----------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------- |
| 1 | Public domain and infrastructure information exposed  | WHOIS revealed registrar details, registration dates, and HostGator name servers for `networkwalks.com`.                      | Public infrastructure information can assist attackers in building a detailed profile of the target during reconnaissance.                               | 🟡 Low         |
| 2 | Server IP address identifiable                        | Nslookup resolved `networkwalks.com` to `192.232.216.135`.                                                                    | The public server IP can be used to map the target's infrastructure and support further authorized enumeration.                                          | 🟡 Low         |
| 3 | HTTP technical information exposed                    | `curl -I` returned HTTP headers showing **Apache**, WordPress-related information, cookies, and the `/wp-json/` API endpoint. | Technical information may help an attacker fingerprint the web application and identify additional areas for investigation.                              | 🟡 Low         |
| 4 | WAF technology identifiable                           | Wafw00f identified **ModSecurity (SpiderLabs)** protecting `networkwalks.com`.                                                | Identifying the WAF reveals information about the website's defensive architecture and may help an attacker adapt later reconnaissance attempts.         | 🟡 Low         |
| 5 | DNS infrastructure information exposed                | DNSRecon identified name servers, an A record, MX records, TXT/SPF records, SRV records, and other DNS-related information.   | DNS information can help build a broader picture of the organization's externally exposed infrastructure and services.                                   | 🟠 Medium      |
| 6 | Multiple active hosts discovered on the local network | Zenmap identified **3 live hosts**: `192.168.1.64`, `192.168.1.67`, and `192.168.1.254`.                                      | Network discovery can reveal active devices and network structure. Unexpected devices should be verified by the network owner.                           | 🟠 Medium      |
| 7 | MAC address information discoverable                  | Zenmap and `ipconfig /all` identified MAC addresses associated with devices on the local LAN.                                 | MAC address information can help identify devices and network hardware during internal reconnaissance.                                                   | 🟡 Low         |
| 8 | Public email addresses discoverable                   | theHarvester using Baidu identified **6 email addresses** related to `microsoft.com`.                                         | Publicly available email addresses may be used in phishing, social engineering, or credential-targeting campaigns.                                       | 🟠 Medium      |
| 9 | Public hosts and subdomains discoverable              | theHarvester identified **15 hosts** related to `microsoft.com` during passive reconnaissance.                                | Publicly exposed hosts and subdomains increase the visible attack surface and may provide additional targets for further authorized security assessment. | 🟠 Medium      |

**Risk Level Key:** 🔴 Critical | 🟠 Medium | 🟡 Low

> **Note:** The findings above are reconnaissance and network-discovery observations and should not automatically be considered confirmed vulnerabilities. No exploitation or vulnerability validation was performed during these project modules.

The `theHarvester -b all` activity also produced several **missing API key** messages for some external data sources. This is a limitation of the reconnaissance results rather than a vulnerability in the target, because some sources could not be queried successfully.

## 6. Recommendations

Based on the observations from the **footprinting, passive reconnaissance, and network scanning activities**, the following security recommendations are suggested:

1. **Review Publicly Exposed Information**  
   Organizations should regularly review what information about their domains, servers, technologies, and infrastructure is publicly accessible.

2. **Keep Web Technologies Updated**  
   Web servers, CMS platforms, plugins, and other technologies should be regularly updated and checked against current security advisories.

3. **Review HTTP Response Headers**  
   HTTP headers should be reviewed to ensure that unnecessary technical information about the server, framework, or application is not being exposed.

4. **Maintain and Monitor the Web Application Firewall**  
   The WAF should remain properly configured, updated, and monitored to help detect and block malicious web traffic.

5. **Review DNS Records Regularly**  
   DNS records such as NS, MX, TXT, SPF, and SRV records should be periodically reviewed to ensure that only necessary information and services are publicly exposed.

6. **Reduce Unnecessary Public Email Exposure**  
   Organizations should monitor publicly available email addresses because exposed addresses may become targets for phishing and social engineering attacks.

7. **Monitor Public Subdomains and Hosts**  
   Publicly discoverable subdomains and hosts should be regularly inventoried and reviewed. Unused or outdated services should be removed or secured to reduce the external attack surface.

8. **Perform Regular Internal Network Discovery**  
   Organizations should periodically scan their own authorized networks to identify active devices and maintain awareness of systems connected to the network.

9. **Investigate Unknown Devices**  
   Any unexpected or unauthorized device discovered during internal network scanning should be identified and investigated.

10. **Maintain Updated Network Documentation**  
    IP addresses, MAC addresses, devices, network topology, and other infrastructure information should be documented and kept up to date.

11. **Limit Unnecessary Information Exposure**  
    Organizations should minimize publicly available technical information wherever possible because reconnaissance data can assist attackers in planning later stages of an attack.

12. **Perform Security Testing Only with Authorization**  
    Reconnaissance, scanning, and other cybersecurity testing activities should only be performed against systems and networks where proper authorization and an agreed scope have been established.

## 7. Conclusion

During the Week 2 cybersecurity project activities, I completed practical exercises covering **footprinting, reconnaissance, passive information gathering, and local network scanning**.

In the **W2-PM1 Footprinting & Reconnaissance** activity, I used multiple Kali Linux tools including **WHOIS, WhatWeb, Nslookup, Curl, Wafw00f, and DNSRecon** to collect publicly available information about `networkwalks.com`. These tools helped identify domain registration details, web technologies, IP information, HTTP response headers, Web Application Firewall information, and DNS records.

In the **W2-PM4 theHarvester** activity, I performed passive reconnaissance against `microsoft.com` using publicly available data sources. The exercise demonstrated how email addresses, hosts, and subdomains can be discovered without attempting to gain unauthorized access to the target systems.

In the **W2-PM5 Network Scanning with Zenmap** activity, I identified my local network configuration and performed a Ping Scan against the `192.168.1.0/24` subnet. The scan discovered **3 live hosts**, and I collected their IP and MAC address information. I also generated a visual network topology using Zenmap.

These exercises demonstrated that a significant amount of useful security information can be gathered before any exploitation takes place. Reconnaissance and network discovery help security professionals understand the visible attack surface, identify exposed information, and build a clearer picture of an environment.

I also learned the importance of documenting each step clearly, including the tools used, commands executed, results observed, potential risks, and recommended security improvements.

All activities were performed within an authorized educational scope, and no unauthorized exploitation or access was attempted.

## 8. Evidences Collected

### 8.1 W2-PM1 – Footprinting & Reconnaissance with Multiple Kali Tools

#### WHOIS Domain Information

![WHOIS Result](evidences/w2-pm1/Screenshot%202026-08-19%20161420.png)

#### DNS Resolution with Nslookup

![Nslookup Result](evidences/w2-pm1/Screenshot%202026-08-19%20161926.png)

#### HTTP Response Headers with Curl

![Curl Result](evidences/w2-pm1/Screenshot%202026-08-19%20162300.png)

#### Web Application Firewall Detection with Wafw00f

![Wafw00f Result](evidences/w2-pm1/Screenshot%202026-08-19%20162817.png)

#### DNS Enumeration with DNSRecon

![DNSRecon Result](evidences/w2-pm1/Screenshot%202026-08-19%20163131.png)

---
### 8.2 W2-PM5 – Network Scanning with Zenmap

#### Live Host Discovery with Zenmap

![Zenmap Ping Scan](./evidences/w2-pm5/Screenshot%202026-08-19%20184915.png)

#### Network Topology

![Zenmap Network Topology](./evidences/w2-pm5/Screenshot%202026-08-19%20185206.png)

---
### 8.3 W2-PM4 – Footprinting & Reconnaissance with theHarvester

#### theHarvester Usage and Available Options

![theHarvester Usage](./evidences/w2-pm4/Screenshot%202026-08-19%20190055.png)

#### Passive Reconnaissance Using Baidu

![theHarvester Baidu Result](./evidences/w2-pm4/Screenshot%202026-08-19%20190234.png)

#### Passive Reconnaissance Using All Sources

![theHarvester All Sources](./evidences/w2-pm4/Screenshot%202026-08-19%20190454.png)
