# Port Scanning

### Explanation
Port scanning is a crucial phase in network reconnaissance, where an attacker or a security professional systematically scans a target network to identify open ports on networked devices. A port is a virtual communication endpoint that facilitates network communication between devices.

### Initial Port Scan

```nmap -p- --open -sS --min-rate 5000 -vvv -n -Pn <TARGET_IP>```

- **-p-**: Specifies scanning all ports.
- **--open**: Shows only open ports.
- **-sS**: Uses SYN scan, a stealthy scan method.
- **--min-rate 5000**: Sets the minimum rate of packets sent per second.
- **-vvv**: Enables verbose output to provide detailed information.
- **-n**: Treats targets as IP addresses and does not perform DNS resolution.
- **-Pn**: Treats all hosts as online, skipping host discovery.

This command performs a quick scan of all ports on the target, identifying open ports using a SYN scan method. It's fast and stealthy but may not provide detailed information about the services running on those ports.

#### Output
```
$ nmap -p- --open -sS --min-rate 5000 -vvv -n -Pn <TARGET_IP>

Starting Nmap (https://nmap.org) at 2024-03-07 12:00 UTC
Initiating SYN Stealth Scan at 12:00
Scanning <TARGET_IP> [1000 ports]
Discovered open port 22/tcp on <TARGET_IP>
Discovered open port 80/tcp on <TARGET_IP>
Completed SYN Stealth Scan at 12:01, 3.00s elapsed (1000 total ports)
Nmap scan report for <TARGET_IP>
Host is up, received user-set (0.50s latency).
Scanned at 2024-03-07 12:00:00 UTC for 4s
Not shown: 998 filtered ports
PORT   STATE SERVICE
22/tcp open  ssh
80/tcp open  http

Read data files from: /usr/bin/../share/nmap
Nmap done: 1 IP address (1 host up) scanned in 4.00 seconds
```

### Exhaustive Scan on Open Ports
```nmap -p<OPEN_PORT_1>,<OPEN_PORT_2>,<OPEN_PORT_3>... <TARGET_IP> -sCV```

- **-p<OPEN_PORT_1>,<OPEN_PORT_2>...**: Specifies scanning only the identified open ports.
- **-sCV**: Uses version detection to determine service versions.

This command conducts a more exhaustive scan on the previously identified open ports, using version detection to determine the exact services and their versions running on those ports. This information is crucial for further analysis and vulnerability identification.

#### Output
```
$ nmap -p22,80 <TARGET_IP> -sCV

Starting Nmap (https://nmap.org) at 2024-03-07 12:05 UTC
Nmap scan report for <TARGET_IP>
Host is up, received user-set (0.50s latency).
Scanned at 2024-03-07 12:05:00 UTC for 1s
Not shown: 998 filtered ports
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 7.9p1 Debian 10+deb10u2 (protocol 2.0)
80/tcp open  http    Apache httpd 2.4.38 ((Debian))

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 1.00 seconds
```

### Identifying Filtered Ports
```nmap -p- -sS --min-rate 5000 -vvv -n -Pn <TARGET_IP>```

This command is similar to the initial port scan but without the --open option. It scans all ports, including filtered ones, using a SYN scan method.

#### Output
```
$ nmap -p- -sS --min-rate 5000 -vvv -n -Pn <TARGET_IP>

Starting Nmap (https://nmap.org) at 2024-03-07 12:10 UTC
Initiating SYN Stealth Scan at 12:10
Scanning <TARGET_IP> [1000 ports]
Discovered open port 22/tcp on <TARGET_IP>
Discovered open port 80/tcp on <TARGET_IP>
Completed SYN Stealth Scan at 12:11, 3.00s elapsed (1000 total ports)
Nmap scan report for <TARGET_IP>
Host is up, received user-set (0.50s latency).
Scanned at 2024-03-07 12:10:00 UTC for 4s
Not shown: 998 filtered ports
PORT   STATE SERVICE
22/tcp open  ssh
80/tcp open  http

Read data files from: /usr/bin/../share/nmap
Nmap done: 1 IP address (1 host up) scanned in 4.00 seconds
```