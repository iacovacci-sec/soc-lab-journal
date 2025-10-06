# SOC Lab Journal

Documenting errors, fixes, and lessons learned from building a Proxmox SOC lab for cybersecurity training.

---

## Table of Contents

### Steps (Lab Setup & Configuration)
- [Step 1 – Proxmox Install & Repo Fix](error-1-proxmox-update.md)
- [Step 2 – Tailscale Remote Access Setup](step-2-tailscale-setup.md)
- [Step 3 – vmbr1 Bridge for Isolated Lab Network](step-3-vmbr1-bridge.md)
- [Step 4 – Active Directory Domain Services Setup](step-4-ad-ds-setup.md)
- [Step 5 – Windows 10 Client VM Setup](step-5-win10-client-setup.md)
- [Step 6 – DNS Domain Join](step-6-dns-domain-join.md)
- [Step 7 – AD DS Domain Join](step-7-ad-ds-domain-join.md)
- [Step 8 – Configuring Firewalls](step-8-configuring-firewalls.md)
- [Step 9 – Splunk Server Setup](step-9-splunk-server-setup.md)
- [Step 10 – Splunk HTTPS & Static IP Fix](step-10-splunk-https-static-ip.md)
### Errors (Troubleshooting Logs)
- [Error 1 – Proxmox Package Database Update Failure](error-1-proxmox-update.md)
- [Error 2 – VirtIO Driver Missing During Windows Server Setup](error-2-virtio-driver.md)
- [Error 3 – VirtIO NIC Driver Missing](error-3-virtio-nic.md)
- [Error 4 – VirtIO Driver “No Signed Device Drivers” During Windows 10 Client Setup](error-4-virtio-driver-nosigned.md)
- [Error 5 – DNS Resolution Fails with IPv6 (nslookup Timeout)](error-5-dns-ipv6.md)
- [Error 6 – DNS Resolution Failure](error-6-dns-resolution.md)

---

## Folder Structure

soc-lab-journal/
│── README.md  
│── LICENSE  
│── error-1-proxmox-update.md  
│── error-2-virtio-driver.md  
│── error-3-virtio-nic.md  
│── error-4-virtio-driver-nosigned.md  
│── error-5-dns-ipv6.md  
│── error-6-dns-resolution.md  
│── step-2-tailscale-setup.md  
│── step-3-vmbr1-bridge.md  
│── step-4-ad-ds-setup.md  
│── step-5-win10-client-setup.md  
│── step-6-dns-domain-join.md  
│── step-7-ad-ds-domain-join.md  
│── step-8-configuring-firewalls.md  
│── step-9-splunk-server-setup.md  
│
├── Error-1/  
│   ├── 01-task-fail.png  
│   ├── 02-console-error.png  
│   └── ...  
│
├── Error-2/  
│   ├── 01-no-drives.png  
│   ├── 02-browse-drivers.png  
│   └── ...  
│
├── Error-3/  
│   ├── 01-nic-missing.png  
│   ├── 02-virtio-mounted.png  
│   ├── 03-update-driver.png  
│   ├── 04-virtio-contents.png  
│   └── 05-driver-installed.png  
│
├── Error-4/  
│   └── ...  
│
├── Error-5/  
│   └── ...  
│
├── Error-6/  
│   └── ...  
│
├── Step-2/  
│   └── 01-tailscale-setup.png  
│
├── Step-3/  
│   ├── 01-vmbr1-create.png  
│   └── 02-vmbr1-config.png  
│
├── Step-4/  
│   └── ...  
│
├── Step-5/  
│   └── ...  
│
├── Step-6/  
│   └── ...  
│
├── Step-7/  
│   └── ...  
│
├── Step-8/  
│   └── ...  
│
├── Step-9/  
│   └── ...  
│
└── Step-X/  
    └── 01-example.png  

---

## How to Add a New Entry

1. Create a new markdown file (`step-x-title.md` or `error-x-title.md`).  
2. Add screenshots into a folder (`Step-X/` or `Error-X/`) with numbered filenames.  
3. Link the new markdown file in the **Table of Contents** above using a relative link:  
   - Example: `[Step 10 – Security Onion Deploy](step-10-security-onion-deploy.md)`

---

## Format Templates

### Step Template
```markdown
# Step X – Title

**Context (what I was doing):**
...

**Screenshot:**
![Alt text](Step-X/01-example.png)

**Root Cause (why this step was needed):**
...

**Fix Applied / Action Taken:**
1. ...
2. ...

**Lesson Learned:**
- ...
- ...
Error Template
markdown
Copy code
# Error X – Title

**Context (what I was doing):**
...

**Error Message (short description + screenshot):**
_One-liner here_  
![Alt text](Error-X/01-example.png)

**Root Cause:**
...

**Fix Applied:**
1. ...
2. ...

**Lesson Learned:**
- ...
- ...
Tips for Links & Images
Link to files: [Link text](relative/path/to/file.md)

Link to a folder view: [Open Step-4 screenshots](Step-4/)

Make an image clickable (links to full-size):
[![thumb alt](Step-4/01-nic-missing.png)](Step-4/01-nic-missing.png)

In-page anchors (GitHub auto-generates):
Link to a heading ## Lesson Learned with #lesson-learned after the file, e.g.
[Jump to lessons](error-3-virtio-nic.md#lesson-learned)

