# SOC Lab Journal  

Documenting errors, fixes, and lessons learned from building a Proxmox SOC lab for cybersecurity training.  

---

## Table of Contents  

### Steps (Lab Setup & Configuration)  
- [Step 1 – Proxmox Install & Repo Fix](error-1-proxmox-update.md)  
- [Step 2 – Tailscale Remote Access Setup](step-2-tailscale-setup.md)  
- [Step 3 – vmbr1 Bridge for Isolated Lab Network](step-3-vmbr1-setup.md)  
- [Step X – Title Here](step-x-title.md)  

### Errors (Troubleshooting Logs)  
- [Error 1 – Proxmox Package Database Update Failure](error-1-proxmox-update.md)  
- [Error X – Title Here](error-x-title.md)  

---

## Folder Structure  



soc-lab-journal/
│── README.md # Table of contents (this file)
│── LICENSE
│── error-1-proxmox-update.md
│── step-2-tailscale-setup.md
│── step-3-vmbr1-setup.md
│
├── Error-1/ # Screenshots for Error 1
│ ├── 01-task-fail.png
│ ├── 02-console-error.png
│ └── ...
│
├── Step-2/ # Screenshots for Step 2
│ └── 01-tailscale-setup.png
│
├── Step-3/ # Screenshots for Step 3
│ ├── 01-vmbr1-create.png
│ └── 02-vmbr1-config.png
│
└── Step-X/ # Future Steps
└── 01-example.png


---

## How to Add a New Entry  

1. Create a new markdown file (`step-x-title.md` or `error-x-title.md`).  
2. Add screenshots into a folder (`Step-X/` or `Error-X/`).  
3. Link the markdown file inside the **Table of Contents** above.  

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
# Error X – Title  

**Context (what I was doing):**  
...

**Error Message:**  


Insert error snippet here

![Alt text](Error-X/01-example.png)  

**Root Cause:**  
...

**Fix Applied:**  
1. ...  
2. ...  

**Lesson Learned:**  
- ...
- ...


---
