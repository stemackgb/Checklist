# Penetration Testing Checklist

A complete Windows Enumeration checklist once an initial Meterpreter shell has been spawned against the target host.

This guide is written in a methodical step-by-step process, it is recommended not skipping steps.&nbsp;
&nbsp;

&nbsp;
**Check the current logged-in user**
```Windows
getuid
```
&nbsp;

**Check the current process, attached to the shell**
```Windows
getpid
```
&nbsp;

**Check all processes currently running on the target host**

*Checking for third-part AV/Firewalls, other logged in users, system architecture (x86/64)*
```Windows
ps aux
```
&nbsp;

**Gather additional information regarding the system**

*Checking for system architecture (x86/64), Windows Versioning, Domain (if applicable), Language Pack(s) Installed*
```Windows
sysinfo
```
&nbsp;

**At this point we want to spawn a standard-system shell to further enumerate**
```Windows
shell
```
&nbsp;

**Check system time information**
```Windows
net time \\{computer_name}
```
&nbsp;

**Check the local system network configuration**

*Checking active/open network connections against processes*
```Windows
netstat -ano
```
*Checking network interface(s) configuration (IP Address, Subnet, Default Gateway, etc)*
```Windows
ipconfig /all
```
*Check ARP table for IP to MAC address of other known systems*
```Windows
arp
```
*Check route table to other known systems and/or networks*
```Windows
route print
```
&nbsp;

**Check local system users and configuration**

*View current-users privileges on the system*
```Windows
whoami /priv
```
*View current-users groups on the system*
```Windows
whoami /groups
```
*View all local users on the system*
```Windows
net users
```
*View information against a specifc user on the system*
```Windows
net user {username}
```
*View default security information applied to a created user*
```Windows
net accounts
```
&nbsp;

**Check remote computers and domain information**

*View known computers*
```Windows
net view
```
*Attempt to ping the discovered known computers to confirm connectivity*
```Windows
ping {address} -n 1 -v
```
*View domain information (if applicable)*
```Windows
net view /domain
```
&nbsp;

**Check for any remotely connected SMB shares**
```Windows
net share
```
