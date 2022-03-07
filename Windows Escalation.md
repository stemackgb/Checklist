# Penetration Testing Checklist

A complete Windows Escalation checklist once the initial Enumeration has been completed against the target host.

This guide is written in a methodical step-by-step process, it is recommended not skipping steps.&nbsp;
&nbsp;

**Metasploit Scripts**

*Several Metasploit modules to detect potential privilege escalation routes*
```Windows
multi/recon/local_exploit_suggester
```
```Windows
windows/local/service_permissions
```
```Windows
windows/local/bypass_uac
```
```Windows
post/windows/gather_enum_unattend
```
&nbsp;

**Check for scheduled tasks**

*Query to display all scheduled tasks*
```Windows
schtasks /query
```

*Query to display either Running or Raedy scheduled tasks*
```Windows
schtasks /query | findstr "Running"
schtasks /query | findstr "Ready"
```

*In detail query to display a specific scheduled task and its relevant configuration*
```Windows
schtasks /query /tn {full_task_path} /v /fo list
For Example: > schtasks /query /tn \Microsoft\Windows\Wininet\cachetasks /v /fo list
```
&nbsp;

**Check for system services**

*Query to display all system services*
```Windows
sc queryex type= service
```

*Query to display all services vulnerable to unquoted service paths*
```Windows
wmic service get name,pathname,displayname,startmode | findstr /i auto | findstr /i /v "C:\" | findstr /I /v
```
&nbsp;

**Check for interesting files**

*Query to search for the string **password** in text files*
```Windows
findstr /si password *.txt *.ini *.config
```

*Query to search for the string **password** in the registry tree*
```Windows
REG QUERY HKLM /F "password" /t REG_SZ /S /K
REG QUERY HKCU /F "password" /t REG_SZ /S /K
```

*Other interesting files to check for*
```Windows
C:\unattend.xml
C:\Windows\Panther\Unattend.xml
C:\Windows\Panther\Unattend\Unattend.xml
C:\Windows\system32\syspref.inf
C:\Windows\system32\sysprep\sysprep.inf
```
