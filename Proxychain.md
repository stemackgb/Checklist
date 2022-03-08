# Penetration Testing Checklist

A complete guide on configuring Proxychains.

This guide is written in a methodical step-by-step process, it is recommended not skipping steps.&nbsp;
&nbsp;

*Configure route through*
```Windows
route add {host-address} 255.255.255.255 {session-id}
run autoroute -s {host-address}/32
```

*Configure and start SOCKS proxy*
```Windows
use auxillary/server/socks_proxy
options
>> Pick specific version 4/5
run -j
jobs
```

*Edit Proxychains configuration*
```Windows
nano /etc/proxychains.conf
>> Specify version selected in previous step
```

*Run command(s) through Proxychains*
```Windows
nmap -sT {options}
>> Proxychains requires a full TCP connection
```
