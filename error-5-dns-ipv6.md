# Error #5 – DNS Resolution Fails with IPv6 (nslookup soclab.local Timeout)

## Context (What I Was Doing)  
While testing domain resolution after setting up Active Directory (AD DS) and DNS on the Server 2019 VM, I attempted to validate that the Windows 10 client could query the domain `soclab.local`.  

Although `ping` worked, `nslookup soclab.local` was failing under certain conditions, specifically when the client defaulted to IPv6 (`::1`) instead of IPv4.  

---

## Error Message  
When running:  

nslookup soclab.local

The output returned:  

DNS request timed out.
timeout was 2 seconds.
Server: Unknown
Address: ::1


---

## Error Screenshots  

:DNS services confirmed running on the server VM.  
`01-dns-services.png` (services in server vm.png)  

:Forward Lookup Zones created, showing `soclab.local`.  
`02-forward-zones.png` (forward lookup zones.png)  

:Server VM IP configuration showing loopback DNS (::1) instead of IPv4.  
`03-server-ipconfig.png` (win server ipconfig again.png)  

:Windows 10 client IP configuration pointing to DNS server.  
`04-client-ipconfig.png` (win10 client ipconfig cont.png)  

:Client ping test against soclab.local resolving to IPv4.  
`05-client-ping-domain.png` (win10 client ping server.png)  

:`nslookup` timeout using default (::1) DNS.  
`06-nslookup-timeout.png` (02-nslookup-timeout.png)  

:`nslookup` success forcing IPv4 query against 192.168.100.10.  
`07-nslookup-success.png` (03-nslookup-success-ipv4.png)  

---

## Root Cause  
The DNS server and/or clients were resolving `soclab.local` using the IPv6 loopback (`::1`), which did not respond correctly to queries. This caused `nslookup` to fail even though `ping` worked, since `ping` automatically fell back to IPv4.  

---

## Fix Applied  
- Verified that the **DNS Server** service was running on the domain controller.  
- Forced client DNS configuration to point explicitly to the IPv4 address of the domain controller (`192.168.100.10`).  
- Re-ran `nslookup` with the IPv4 server specified:  

nslookup soclab.local 192.168.100.10


This succeeded, confirming the DNS records were correct.  

---

## Lesson Learned  
- Windows defaults to IPv6 for DNS queries if it’s available, even if IPv6 isn’t configured properly.  
- Always check both IPv4 and IPv6 paths when diagnosing DNS issues.  
- When building a lab, disabling IPv6 on adapters or forcing IPv4 DNS servers avoids unnecessary resolution failures.  


