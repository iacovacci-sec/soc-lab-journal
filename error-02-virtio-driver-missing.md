# Error #2 – VirtIO Driver Missing During Windows Server Setup

## Context (what I was doing)
While installing Windows Server 2019 as a VM on Proxmox (q35 machine, OVMF UEFI, VirtIO SCSI controller), I selected VirtIO for both the disk and network to maximize performance. During installation, Windows Setup could not detect the virtual hard disk.

## Error Message
Windows installer displayed:

> “No drives were found. Click Load driver to provide a mass storage driver for installation.”

![No Drives](Error-02/02-no-drives.png)

## Root Cause
The Windows Server ISO does not include VirtIO storage/network drivers by default. Because the VM disk was presented as VirtIO SCSI, the installer had no compatible driver to recognize the disk.

## Fix Applied
- Verified VM was configured with VirtIO SCSI + VirtIO NIC in Proxmox.  
  ![Hardware Pre-Fix](Error-02/01-hw-pre-fix.png)  

- Attempted Windows install, hit *no drives detected*.  
  ![No Drives](Error-02/02-no-drives.png)  

- Downloaded the official VirtIO ISO (`virtio-win-0.1.271.iso`) from Fedora.  
  ![VirtIO ISO Download](Error-02/extra-fedora-source.png)  

- Attached the VirtIO ISO as a secondary CD drive in Proxmox.  
  ![VirtIO ISO Attached](Error-02/04-virtio-iso-attached.png)  

- From Windows Setup, loaded drivers from the VirtIO ISO → selected *Red Hat VirtIO SCSI pass-through controller (w10/amd64)*.  
  ![Select Driver](Error-02/05-select-driver.png)  

- After loading the drivers, Windows installation proceeded. However, on first boot the VM failed with PXE-over-IPv6 errors:  
  ![PXE Boot Failure](Error-02/06-boot-failure.png)  

- The issue was caused by Proxmox attempting to boot via IPv6 network instead of the installed disk.  
- **Fix:** Manually unchecked IPv6 in the VM’s network settings, leaving only IPv4 enabled. Once disabled, the VM booted normally from disk.  

- Proxmox occasionally showed the VirtIO ISO as “undefined” in the hardware tab, but installation still succeeded.  
  ![Undefined CD](Error-02/07-hw-undefined.png)  

- Installation completed successfully, VM booted into Windows.  
  ![First Boot Success](Error-02/08-success.png)  

## Lesson Learned
Whenever using VirtIO SCSI or NIC on Windows VMs in Proxmox, **always attach the VirtIO driver ISO** during setup so the installer can detect the disk.  

Additionally, if PXE boot issues appear after install, check NIC settings. **Disabling IPv6** can prevent the VM from attempting unwanted network boots.
