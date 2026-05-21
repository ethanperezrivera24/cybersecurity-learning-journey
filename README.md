# Cybersecurity Learning Journal

Documenting my learning journey in cybersecurity
Started: May 2026

## Goals
- Land a Cybersecurity internship (Miami or remote) for Summer 2027
- Earn CompTIA Security+
- Build hands-on skills in log analysis, SIEM, and threat detection
- Long-term: Pen Testing / Red Team

## Current Phase
Phase 0 — Foundation Setup (Setting up VMs, key accounts such as Github, starting a learning log)

## General Progress Log

### 2026-05-19
- Set up Ubuntu VM in VirtualBox
- Configured dynamic display scaling and bidirectional clipboard
- Took baseline snapshot ("Fresh Install") for safe restore point
- Set up learning journal
- Learned: what a hypervisor is; snapshots let you break things safely similar to git version control; how to install ISO files and configure Ubuntu; how to configure a virtual machine

## OverTheWire: Bandit

### Level 0 → 1
**Date:** 2026-05-20
**Objective:** The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game
**Command(s) used:**
```bash
ssh, ls, cat
```
**What I learned:** SSH allows you to remotely connect to a computer or server; Using ls to find a README file containing the pw.

---

### Level 1 → 2
**Date:** 2026-05-20
**Objective:** The password for the next level is stored in a file called - located in the home directory
**Command(s) used:**
```bash
ls, cat
```
**What I learned:** You can't cat directly into files that start with a dash because the dash in Linux is used to select various options for commands. So, to cat into a dashed file, you need to prepend the filename with "./".

---

### Level 2 → 3
**Date:** 2026-05-20
**Objective:** The password for the next level is stored in a file called --spaces in this filename-- located in the home directory
**Command(s) used:**
```bash
ls, cat
```
**What I learned:** When referencing a file with spaces in the name, you must use quotation marks around the filename to show that it's all one input.

---

### Level 3 → 4
**Date:** 2026-05-20
**Objective:** The password for the next level is stored in a hidden file in the inhere directory
**Command(s) used:**
```bash
cd, ls -a, cat
```
**What I learned:** To access files within a directory, you need to cd into that directory. To see hidden files, you add the -a option to the ls command to view all files including hidden ones that begin with a ".".

---

### Level 4 → 5
**Date:** 2026-05-XX
**Objective:** 
**Command(s) used:**
```bash

```
**What I learned:** 

---