# Error #04 – VirtIO Driver “No Signed Device Drivers” During Windows 10 Client Setup

## Context (What I Was Doing)
While installing a Windows 10 Client VM on Proxmox (q35 machine, OVMF UEFI, VirtIO SCSI controller), I selected VirtIO for both the disk and network. During Windows Setup, the installer rejected the VirtIO drivers.

## Error Message
Windows installer displayed:

> “No signed device drivers were found. Make sure that the installation media contains the correct drivers, and then click OK.”

![No Signed Drivers](Error-04/03-no-signed-drivers-found.png)

## Root Cause
The Windows 10 ISO does not include VirtIO drivers by default. When I first attempted to load them, I browsed the wrong location on the VirtIO ISO, causing Setup to report the drivers as “unsigned.”

## Fix Applied
- Created the Windows 10 Client VM in Proxmox with VirtIO SCSI + VirtIO NIC.  
  ![VM Config Confirm](Error-04/01-confirm-windows-10-VM.png)

- Started Windows Setup and selected the OS edition.  
  ![OS Selection](Error-04/02-choose-correct-OS.png)

- Hit the error when trying to load drivers.  
  ![Error No Signed Drivers](Error-04/03-no-signed-drivers-found.png)

- Attached the official VirtIO ISO (`virtio-win-0.1.271.iso`) as a secondary CD drive in Proxmox.  
- From Windows Setup, manually browsed into the VirtIO ISO:  
  ![Browse Drivers](Error-04/04-browse-drivers.png)  

  - For disk: `viostor\w10\amd64`  
  - For network: `NetKVM\w10\amd64`  

- Installation continued successfully. After first boot, Device Manager showed missing devices (Ethernet + PCI).  
  ![Device Manager Missing](Error-04/05-device-manager.png)

- Installed VirtIO NIC driver → NIC detected as **Red Hat VirtIO Ethernet Adapter**.  
  ![Device Manager NIC Fixed](Error-04/06-device-manager-nic.png)

- Installed VirtIO Balloon driver under System devices.  
  ![VirtIO Balloon Driver](Error-04/07-virtio-balloon.png)

- VM fully added and operational as a Windows 10 Client.  
  ![Windows 10 Client Added](Error-04/08-windows-10-client-added.png)

## Lesson Learned
Windows 10, like Server 2019, does not ship with VirtIO drivers. The error “No signed device drivers were found” occurs if:  
- The wrong path is browsed, or  
- The VirtIO ISO is missing.  

**Fix:** Always attach the VirtIO ISO and load the correct OS-specific driver folder (`w10\amd64`). After install, update remaining devices (NIC, Balloon, etc.) from the VirtIO ISO to ensure full functionality.
