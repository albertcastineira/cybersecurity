# 💻🔐 Cybersecurity General Guide  

## Introduction
The objective of this guide is to facilitate and remember the phases that must be followed to be able to perform pentesting on any type of machine.  
> **_NOTE:_**  The content of this guide may change at any time.

## Prerequisites
This guide is made assuming that you already have a machine with standard hacking tools such as Kali or Parrot.

## Table of Contents

1. [Introduction](#introduction)
2. [Prerequisites](#prerequisites)
3. [Phases](#phases)
    - [1. Pre-engagement](#1-pre-engagement)
        - [TTL Cheatsheet](#ttl-cheatsheet)
    - [2. Reconnaissance & Scanning](#2-reconnaissance--scanning)
        - [Note on Identifying Filtered Ports](#note-on-identifying-filtered-ports)
    - [3. Enumeration & Vulnerability Analysis](#3-enumeration--vulnerability-analysis)
    - [4. Exploitation](#4-exploitation)
    - [5. Post-exploitation](#5-post-exploitation)
    - [6. Reporting](#6-reporting)

## Phases

### 1. Pre-engagement
Understanding the scope of the penetration test, defining goals and objectives, and obtaining necessary permissions from relevant stakeholders.  
The main goal of this phase is gathering information about the target system, such as its architecture, technology stack, and potential vulnerabilities.  

You always have to check that the machine we want to attack is active using this command ```ping -c 1 <TARGET_IP>```  
Once the command has been executed we can identify what type of machine we are dealing with. If we look at the response, we can see the "ttl".  

#### TTL Cheatsheet
| TTL | O.S.       |
|-----|------------|
| 64  | Linux/Unix |
| 64  | macOS      |
| 128 | Windows    |  

> **_NOTE:_**  It's essential to note that these default TTL values are not definitive indicators of the operating system, as they can be customized by network administrators or overridden by security devices such as firewalls or proxies. Remember that values ​​may vary slightly and are not always exact.

### 2. Reconnaissance & Scanning
This phase involves collecting data about the target system or network using tools such as port scanners, vulnerability scanners, and network mapping tools. The objective is to identify open ports, services running on those ports, and potential weaknesses that can be exploited.  

First of all we will scan all the open ports using ```nmap -p- --open -sS --min-rate 5000 -vvv -n -Pn <TARGET_IP>```  
Once we have all the open ports we should do ```nmap -p<OPEN_PORT_1>,<OPEN_PORT_2><3,4...> <TARGET_IP> -sCV``` to execute an exhaustive scan.  

> **_NOTE:_** You may realize later at some stage that you need to identify filtered ports. In this case we must use  
> ```nmap -p- -sS --min-rate 5000 -vvv -n -Pn <TARGET_IP>```

The results of the exhaustive scan should give us enough information to be able to identify the services exposed on the machine. One of the most essential things in this phase is to recognize the versions of each service. It will be essential when starting the vulnerability identification phase.

### 3. Enumeration & Vulnerability Analysis
This phase involves gathering more detailed information about the target system, such as user accounts, network shares, and system configurations. This information helps in planning and executing further attacks.  

The versions of the exposed services are normally used to identify and search for vulnerabilities through which the system can be attacked. This phase consists of searching, identifying and planning which vulnerabilities are going to be used to compromise the system.  

### 4. Exploitation
Once we have the general information of the system, the exposed services and the corresponding vulnerabilities, it is time to proceed to compromise the machine.  

This phase will be very different on each machine since the versions of the services may vary, the architecture and security of the machine may be different, etc.

### 5. Post-exploitation
After gaining access to the target system, the penetration tester may perform further activities such as privilege escalation, data exfiltration, or lateral movement within the network. The goal is to demonstrate the extent of the security weaknesses and the potential impact of a real-world attack.

List of useful resources when escalating privileges:  
- Exploit Database (Exploit-DB)
- Common Vulnerabilities and Exposures (CVE)
- GitHub
- Security-focused Forums and Communities
- Hacktricks

### 6. Reporting
Finally, the penetration tester documents the findings of the test in a detailed report, including information about the vulnerabilities discovered, the techniques used to exploit them, and recommendations for improving the security posture of the target system. This report is then presented to the relevant stakeholders, along with any necessary remediation steps.
