# SOC Lab Journal  

Documenting errors, fixes, and lessons learned from building a Proxmox SOC lab for cybersecurity training.  

---

Table of Contents
Steps (Lab Setup & Configuration)

Step 1 – Proxmox Install & Repo Fix

Step 2 – Tailscale Remote Access Setup

Step 3 – vmbr1 Bridge for Isolated Lab Network

Step 4 – Windows Server VirtIO NIC Setup

Errors (Troubleshooting Logs)

Error 1 – Proxmox Package Database Update Failure

Error 2 – VirtIO Driver Missing During Windows Server Setup

Error 3 – VirtIO NIC Driver Missing

Folder Structure
soc-lab-journal/
│── README.md # Table of contents (this file)
│── LICENSE
│── error-1-proxmox-update.md
│── error-2-virtio-driver.md
│── error-3-virtio-nic.md
│── step-2-tailscale-setup.md
│── step-3-vmbr1-setup.md
│── step-4-virtio-nic-setup.md
│
├── Error-1/ # Screenshots for Error 1
│   ├── 01-task-fail.png
│   ├── 02-console-error.png
│   └── ...
│
├── Error-2/ # Screenshots for Error 2
│   ├── 01-no-drives.png
│   ├── 02-browse-drivers.png
│   └── ...
│
├── Error-3/ # Screenshots for Error 3
│   ├── 01-nic-missing.png
│   ├── 02-virtio-mounted.png
│   ├── 03-update-driver.png
│   ├── 04-virtio-contents.png
│   └── 05-driver-installed.png
│
├── Step-2/ # Screenshots for Step 2
│   └── 01-tailscale-setup.png
│
├── Step-3/ # Screenshots for Step 3
│   ├── 01-vmbr1-create.png
│   └── 02-vmbr1-config.png
│
├── Step-4/ # Screenshots for Step 4
│   ├── 01-nic-missing.png
│   ├── 02-virtio-mounted.png
│   ├── 03-update-driver.png
│   ├── 04-virtio-contents.png
│   └── 05-driver-installed.png
│
└── Step-X/ # Future Steps
    └── 01-example.png
