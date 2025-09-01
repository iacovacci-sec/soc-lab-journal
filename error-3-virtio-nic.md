# Error #3 – VirtIO NIC Driver Missing

## Context (What I Was Doing)
While configuring the Windows Server 2019 VM (**Win-Server-AD**) on Proxmox with a VirtIO network adapter, Device Manager showed the NIC was not recognized. The VM had no working network connectivity.

## Error Message
Device Manager displayed the NIC under **Other devices** as *Ethernet Controller* with a yellow exclamation mark.

First, in Device Manager, the NIC showed as missing:  
![NIC Missing](Error-3/01-nic-missing.png)

## Root Cause
Windows Server installation media does not ship with VirtIO drivers. Since the VM network interface was configured as a **Red Hat VirtIO Ethernet Adapter**, the OS could not automatically load a driver.

## Fix Applied
I mounted the VirtIO ISO (`virtio-win-0.1.271.iso`) in Proxmox as a secondary CD drive:  
![VirtIO ISO Mounted](Error-3/02-virtio-mounted.png)

Next, I opened Device Manager → *Right-click NIC → Update Driver → Browse*:  
![Update Driver](Error-3/03-update-driver.png)

Then, I navigated to the VirtIO ISO contents and selected the appropriate driver:  
![VirtIO ISO Contents](Error-3/04-virtio-contents.png)

Finally, the Red Hat VirtIO Ethernet Adapter driver installed successfully:  
![Driver Installed](Error-3/05-driver-installed.png)

At this point, the NIC appeared correctly under *Network adapters* without warnings.

## Lesson Learned
When using VirtIO hardware for Windows VMs in Proxmox, VirtIO drivers must be installed manually from the ISO. Always keep the VirtIO ISO mounted during installation/configuration to resolve missing device driver errors quickly.
