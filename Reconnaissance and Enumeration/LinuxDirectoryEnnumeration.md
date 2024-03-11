# Linux Directory Ennumeration

### Explanation
When gaining access to a machine as a guest, exploring directories becomes crucial for several reasons. Firstly, guest accounts often have limited permissions, restricting access to certain areas of the system. By systematically searching directories, one can uncover valuable information within the scope of the guest account's permissions, potentially revealing vulnerabilities or misconfigurations that could be leveraged for further exploitation.

### Common directories to search

- **/etc/**: This directory contains *system-wide configuration files*. Look for files like **passwd, shadow, hosts, sudoers, and services configuration files**.
<br>

- **/var/**: This directory holds variable data files. Common subdirectories to investigate include:
  - **/var/log/**: Contains system log files.
  - **/var/www/**: If the machine is hosting a web server, this directory may contain web-related files.
  - **/var/lib/**: Contains dynamic data libraries, such as package manager databases.
  - **/var/spool/**: Contains mail and print spool directories.
<br>

- **/home/**: This directory contains user home directories where you might find user-specific configuration files and potentially sensitive data.
<br>

- **/root/**: The home directory of the root user, containing system-wide configuration files and sensitive data.
<br>

- **/tmp/** and **/var/tmp/**: Temporary directories where files are often stored temporarily. These can sometimes contain sensitive information or files that haven't been properly secured.
<br>

- **/proc/**: A virtual filesystem that provides information about processes and system resources. You can find details about running processes here.
<br>

- **/opt/**: Optional application software packages can be installed here. Look for custom applications or configurations.
<br>

- **/sbin/** and **/bin/**: These directories contain essential system binaries. Look for SUID/SGID binaries or binaries with unusual permissions that might be exploitable.
<br>

- **/usr/**: This directory contains user applications and utilities. Look for installed software and its configurations.
<br>

- **/etc/sysconfig/** or **/etc/default/**: Depending on the distribution, configuration files for various services may be stored here.
<br>

- **/etc/init.d/** or **/etc/systemd/system/**: Init scripts or systemd service files may contain configurations that could be exploited.
<br>

> **_NOTE:_**  Remember, while exploring these directories, ensure you have appropriate permissions and authorization. Unauthorized access to sensitive files or directories could be illegal and unethical. Always conduct penetration testing responsibly and within legal boundaries.