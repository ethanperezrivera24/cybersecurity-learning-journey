# Cybersecurity Learning Journal

Documenting my learning journey in cybersecurity
Started: May 2026

## Goals
- Land a Cybersecurity internship (Miami or remote) for Summer 2027
- Earn CompTIA Security+
- Build hands-on skills in log analysis, SIEM, and threat detection
- Long-term: Pen Testing / Red Team

## OverTheWire: Bandit

### Level 0
**Objective:** Log into the level with SSH.
**Command(s) used:**
```bash
ssh
```
**What I learned:** ssh, short for Secure Shell Protocol, allows you to remotely connect to a machine through a port. A port is an endpoint that allows your system to know which service should be accessed. The default port for ssh is port 22, and to access a different port you use the -p option.

### Level 0 → 1
**Objective:** The password for the next level is stored in a file called readme located in the home directory.
**Command(s) used:**
```bash
ssh, ls, cat
```
**What I learned:** ssh will land you in the home directory of the user. ls lists the files in the working directory and has two common flags: -l to print in a long list format showing more information, and -a which prints all files, including hidden files. cat reads a file and prints its content in the console.

---

### Level 1 → 2
**Objective:** Get the password from the file called ‘-’.
**Command(s) used:**
```bash
ls, cat
```
**What I learned:** The "-" symbol is the standard option symbol. It's important to avoid starting a filename with that symbol because it has other purposes, such as setting the -p flag in ssh. To read a file that starts with "-", you need to write the path (cat ./-).

---

### Level 2 → 3
**Objective:** The password for the next level is stored in a file called "--spaces in this filename--" located in the home directory.
**Command(s) used:**
```bash
ls, cat
```
**What I learned:** When referencing a file with spaces in the name, you must use quotation marks around the filename to show that it's all one input. It's good practice to underscores when naming files rather than spaces.

---

### Level 3 → 4
**Objective:** The password for the next level is stored in a hidden file in the inhere directory
**Command(s) used:**
```bash
cd, ls -a, cat
```
**What I learned:** cd stands for "change directory", and to access files within a directory, you need to cd into that directory. Hidden files start with ".", and to see hidden files, you add the -a option to the ls command to view all files.

---

### Level 4 → 5
**Objective:** The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command.
**Command(s) used:**
```bash
cd, ls, file, cat
```
**What I learned:** The file command tells you what kind of data is stored within a file (data, image, ASCII). Files that return ASCII are human-readable.

---

### Level 5 → 6
**Objective:** The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties: human-readable; 1033 bytes in size; not executable
**Command(s) used:**
```bash
cd, find, cat
```
**What I learned:** Find is a very powerful search tool for needle-in-a-haystack type problems. You can use options like -type, -size, and various others to narrow down a lengthy search.

---

### Level 6 → 7
**Objective:** The password for the next level is stored somewhere on the server and has all of the following properties: owned by user bandit7; owned by group bandit6; 33 bytes in size
**Command(s) used:**
```bash
find, cat
```
**What I learned:** To search current directory use "." after find, and to search server use "/" after find. To redirect all error messages to trash, you can use 2>/dev/null at the end.

---

### Level 7 → 8
**Objective:** The password for the next level is stored in the file data.txt next to the word millionth
**Command(s) used:**
```bash
ls, cat, grep
```
**What I learned:** Grep works similar to Ctrl + F where it searches for a word inside a document. Grep searches for a phrase within a file and prints that line. Also, you can pipeline commands using " | ", where it uses the output of the first command as the input for the second.

---

### Level 8 → 9
**Objective:** The password for the next level is stored in the file data.txt and is the only line of text that occurs only once
**Command(s) used:**
```bash
cat, sort, uniq
```
**What I learned:** Sort sorts a file alphabetically, which is needed to use uniq since it only reads duplicates if they are next to each other. You can also use the -u option for uniq to only paste unique lines rather than removing dupes.

---

### Level 9 → 10
**Objective:** The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.
**Command(s) used:**
```bash
strings, grep
```
**What I learned:** Strings filters out anything that isn't human-readable, and can be useful when comboed with grep to find human-readable lines with specific phrases.

---

### Level 10 → 11
**Objective:** The password for the next level is stored in the file data.txt, which contains base64 encoded data
**Command(s) used:**
```bash
base64
```
**What I learned:** Base64 is a binary-to-text encoding system (not encryption) to change binary data into ASCII to prevent corruption. Linux has a command base64 that when used with option -d can decode any data encoded in base64. You can tell when something is in base64 if it ends in two equal signs "==".

---

### Level 11 → 12
**Objective:** The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions
**Command(s) used:**
```bash
cat, tr
```
**What I learned:** tr is short for translate, and takes inputs telling it what to switch and what to switch it to.

---

### Level 12 → 13
**Objective:** The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work. Use mkdir with a hard to guess directory name. Or better, use the command “mktemp -d”. Then copy the datafile using cp, and rename it using mv (read the manpages!)
**Command(s) used:**
```bash
mktemp -d, cp, xxd, file, mv, gzip, bzip2, tar, cat
```
**What I learned:** When you don't have access to write in the home directory, it can be useful to make a temporary directory using mktemp -d and copying whatever file you need using cp. To change from hexadecimal to binary or vice-versa you use the xxd command. Files can be compressed in different ways like gzip, bzip2, or tar and there are commands to continuously uncompress the file.

---

### Level 13 → 14
**Objective:** The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. Look at the commands that logged you into previous bandit levels, and find out how to use the key for this level.
If you need help with this level: a hint file can be found in the home directory.
Make sure to read the error messages as they are informative.
**Command(s) used:**
```bash
scp, chmod 700, ssh -i
```
**What I learned:** sshkeys can be used instead of passwords to connect to a remote host. scp is secure copy and you can use it to transfer files remotely to your own device. chmod can be used to change the permissions of a file you are the owner of. ssh -i is used to connect via sshkey, and the sshkey must only have owner permissions to be used.

---

### Level 14 → 15
**Objective:** The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.
**Command(s) used:**
```bash
nc
```
**What I learned:** nc "netcat", is a command that allows you to read/write data over a network connection. 

---
