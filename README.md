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

### 2026-05-21
- OverTheWire: Bandit — completed Levels 4 → 10
- Learned: file type identification with `file`, complex searches with `find` (-type, -size, -user, -group), stderr redirection with `2>/dev/null`, text search with `grep`, piping commands with `|`, deduplication with `sort` + `uniq`, extracting human-readable strings with `strings`, and base64 decoding with `base64 -d`
- Key insight: piping chains small single-purpose tools into powerful one-liners

### 2026-05-20
- Started OverTheWire: Bandit — completed Levels 0 → 4
- Updated learning log via push from VS Code
- Learned: SSH remote login, navigating dashed/spaced/hidden filenames in Linux CLI

### 2026-05-19
- Set up Ubuntu VM in VirtualBox
- Configured dynamic display scaling and bidirectional clipboard
- Took baseline snapshot ("Fresh Install") for safe restore point
- Set up learning journal as README.md file
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
**Date:** 2026-05-21
**Objective:** The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.
**Command(s) used:**
```bash
cd, ls, file, cat
```
**What I learned:** The file command tells you what kind of data is stored within a file (data, image, ASCII). Files that return ASCII are human-readable.

---

### Level 5 → 6
**Date:** 2026-05-21
**Objective:** The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties: human-readable; 1033 bytes in size; not executable
**Command(s) used:**
```bash
cd, find, cat
```
**What I learned:** Find is a very powerful search tool for needle-in-a-haystack type problems. You can use options like -type, -size, and various others to narrow down a lengthy search.

---

### Level 6 → 7
**Date:** 2026-05-21
**Objective:** The password for the next level is stored somewhere on the server and has all of the following properties: owned by user bandit7; owned by group bandit6; 33 bytes in size
**Command(s) used:**
```bash
find, cat
```
**What I learned:** To search current directory use "." after find, and to search server use "/" after find. To redirect all error messages to trash, you can use 2>/dev/null at the end.

---

### Level 7 → 8
**Date:** 2026-05-21
**Objective:** The password for the next level is stored in the file data.txt next to the word millionth
**Command(s) used:**
```bash
ls, cat, grep
```
**What I learned:** Grep works similar to Ctrl + F where it searches for a word inside a document. Grep searches for a phrase within a file and prints that line. Also, you can pipeline commands using " | ", where it uses the output of the first command as the input for the second.

---

### Level 8 → 9
**Date:** 2026-05-21
**Objective:** The password for the next level is stored in the file data.txt and is the only line of text that occurs only once
**Command(s) used:**
```bash
cat, sort, uniq
```
**What I learned:** Sort sorts a file alphabetically, which is needed to use uniq since it only reads duplicates if they are next to each other. You can also use the -u option for uniq to only paste unique lines rather than removing dupes.

---

### Level 9 → 10
**Date:** 2026-05-21
**Objective:** The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.
**Command(s) used:**
```bash
strings, grep
```
**What I learned:** Strings filters out anything that isn't human-readable, and can be useful when comboed with grep to find human-readable lines with specific phrases.

---

### Level 10 → 11
**Date:** 2026-05-21
**Objective:** The password for the next level is stored in the file data.txt, which contains base64 encoded data
**Command(s) used:**
```bash
base64
```
**What I learned:** Base64 is a binary-to-text encoding system (not encryption) to change binary data into ASCII to prevent corruption. Linux has a command base64 that when used with option -d can decode any data encoded in base64. You can tell when something is in base64 if it ends in two equal signs "==".

---