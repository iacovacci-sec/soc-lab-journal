# SOC Lab Journal

Documenting errors, fixes, and lessons learned from building a Proxmox SOC lab for cybersecurity training.

---

## Table of Contents

### Steps (Lab Setup & Configuration)
- [Step 1 – Proxmox Install & Repo Fix](error-1-proxmox-update.md)
- [Step 2 – Tailscale Remote Access Setup](step-2-tailscale-setup.md)
- [Step 3 – vmbr1 Bridge for Isolated Lab Network](step-3-vmbr1-setup.md)
- [Step 4 – Windows Server VirtIO NIC Setup](step-4-virtio-nic-setup.md)

### Errors (Troubleshooting Logs)
- [Error 1 – Proxmox Package Database Update Failure](error-1-proxmox-update.md)
- [Error 2 – VirtIO Driver Missing During Windows Server Setup](error-2-virtio-driver.md)
- [Error 3 – VirtIO NIC Driver Missing](error-3-virtio-nic.md)

---

## Folder Structure

soc-lab-journal/
│── README.md
│── LICENSE
│── error-1-proxmox-update.md
│── error-2-virtio-driver.md
│── error-3-virtio-nic.md
│── step-2-tailscale-setup.md
│── step-3-vmbr1-setup.md
│── step-4-virtio-nic-setup.md
│
├── Error-1/
│ ├── 01-task-fail.png
│ ├── 02-console-error.png
│ └── ...
│
├── Error-2/
│ ├── 01-no-drives.png
│ ├── 02-browse-drivers.png
│ └── ...
│
├── Error-3/
│ ├── 01-nic-missing.png
│ ├── 02-virtio-mounted.png
│ ├── 03-update-driver.png
│ ├── 04-virtio-contents.png
│ └── 05-driver-installed.png
│
├── Step-2/
│ └── 01-tailscale-setup.png
│
├── Step-3/
│ ├── 01-vmbr1-create.png
│ └── 02-vmbr1-config.png
│
├── Step-4/
│ ├── 01-nic-missing.png
│ ├── 02-virtio-mounted.png
│ ├── 03-update-driver.png
│ ├── 04-virtio-contents.png
│ └── 05-driver-installed.png
│
└── Step-X/
└── 01-example.png


---

## How to Add a New Entry

1. Create a new markdown file (`step-x-title.md` or `error-x-title.md`).
2. Add screenshots into a folder (`Step-X/` or `Error-X/`) with numbered filenames.
3. Link the new markdown file in the **Table of Contents** above using a relative link:
   - Example: `[Step 5 – Security Onion Deploy](step-5-security-onion-deploy.md)`

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
Link to a heading ## Lesson Learned with [#lesson-learned] after the file, e.g.
[Jump to lessons](error-3-virtio-nic.md#lesson-learned)


