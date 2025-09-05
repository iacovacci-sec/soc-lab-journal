Step 7 – Windows 10 Client Domain Login
Context (what I was doing)

After configuring DNS and domain join in Step 6, the next step was to validate that a domain user could successfully authenticate on the Windows 10 client using Active Directory. This was the first real test of the authentication chain between the domain controller (Server 2019 AD DS) and the client.

## Actions Taken  

1. **Verified Server IP/DNS Configuration**  
   - Confirmed the domain controller had a static IP (`192.168.100.10`) and loopback DNS (`127.0.0.1`) with suffix `soclabs.local`.  
   ![Server IP Config](Step-7/01-server-ipconfig.png)  

2. **Checked Client Visibility of Domain Resources**  
   - From the Windows 10 Client, verified network discovery and saw the domain controller hostname appear.  
   ![Client Network View](Step-7/02-client-network-view.png)  

3. **Reviewed Client Specifications Before Join**  
   - Validated system name (`DESKTOP-K68H5O3`) and OS version prior to joining domain.  
   ![Client Specs](Step-7/03-client-specs.png)  

4. **Created and Prepared Domain User**  
   - In ADUC, confirmed domain user `moevacci` was created and configured for login.  
   ![AD DS Users](Step-7/04-ad-ds-users.png)  

5. **Attempted Domain Login on Client**  
   - At the Windows 10 login screen, attempted to log in using `SOCLAB\moevacci`.  
   ![Client Domain Login](Step-7/05-client-domain-login.png)  

6. **Validated User Properties in AD**  
   - Confirmed account details for `moevacci@soclabs.local`.  
   ![User Properties](Step-7/06-user-properties.png)  

7. **Connectivity Tests (Ping & nslookup)**  
   - Pinging `soclabs.local` worked consistently.  
   - `nslookup` showed timeouts initially, but eventually resolved correctly to the DC’s IP.  
   ![DNS Tests](Step-7/07-dns-tests.png)  

8. **Verified Proxmox Isolated Network (vmbr1)**  
   - Confirmed both server and client were running inside the `vmbr1` isolated lab network.  
   ![Proxmox vmbr1 Config](Step-7/08-vmbr1-config.png)  

Result

Windows 10 Client successfully attempted domain login with SOCLAB\moevacci.

Authentication path between server and client validated end-to-end.

DNS resolution confirmed functional, though intermittent timeouts (linked to Error 5 – DNS IPv6).

Lab isolation via vmbr1 confirmed intact.

Lesson Learned

A successful ping doesn’t always mean DNS is fully working — nslookup highlighted hidden issues.

Clients rely entirely on the DC for DNS resolution; misconfiguration here will break logins.

Testing logon at the client side is the most conclusive way to confirm AD setup is working.

Auxiliary Screenshots

aux-01-server-events.png – AD DS/Server Manager showing domain service warnings and replication errors after promotion.
