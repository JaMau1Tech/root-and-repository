# Operating System Security

## Status

✅ Completed

---

## Overview

This room introduced operating system security concepts, including the importance of protecting sensitive data, understanding common security weaknesses, and using SSH to access a remote Linux system. The hands-on lab demonstrated how weak passwords and poor security practices can lead to unauthorized access and privilege escalation.

---

## Learning Objectives

- Understand why operating systems need security
- Explain the CIA Triad
- Recognize weak passwords
- Understand authentication methods
- Understand the principle of least privilege
- Identify risks from weak file permissions
- Understand how malware can impact systems
- Use SSH to access a remote Linux system
- Practice switching users and escalating privileges

---

## Key Concepts Learned

- Operating System Security
- Confidentiality
- Integrity
- Availability
- CIA Triad
- Authentication
- Weak Passwords
- Least Privilege
- File Permissions
- Malware
- Trojan Horse
- Ransomware
- SSH
- Root Account
- Privilege Escalation
- Command History

---

## Skills Practiced

- Understanding operating system security risks
- Identifying weak password behavior
- Connecting to a remote Linux system with SSH
- Verifying the current user
- Listing files
- Reading files
- Reviewing command history
- Switching users
- Accessing the root account
- Retrieving a protected flag
- Technical documentation

---

## Commands Used

```bash
ssh sammie@MACHINE_IP
whoami
ls
cat draft.md
su - johnny
history
su - root
cat flag.txt
```

---

## Lab / Hands-On

### Task 1 – Introduction

1. Reviewed the purpose of operating system security.
2. Learned that operating systems manage access between hardware, software, and users.
3. Reviewed the CIA Triad:
   - Confidentiality
   - Integrity
   - Availability

---

### Task 2 – Common Security Weaknesses

1. Reviewed common operating system security weaknesses.
2. Studied authentication methods:
   - Something you know
   - Something you are
   - Something you have
3. Reviewed weak password examples.
4. Learned the importance of the principle of least privilege.
5. Reviewed malware examples:
   - Trojan horse
   - Ransomware

---

### Task 3 – SSH Authentication and Privilege Escalation

1. Started the AttackBox.
2. Started the target machine.
3. Opened the AttackBox terminal.
4. Connected to the remote Linux system using SSH:

   ```bash
   ssh sammie@MACHINE_IP
   ```

5. Accepted the SSH fingerprint prompt.
6. Logged in as Sammie using the discovered password.
7. Verified the current user:

   ```bash
   whoami
   ```

8. Listed files in the directory:

   ```bash
   ls
   ```

9. Read the file `draft.md`:

   ```bash
   cat draft.md
   ```

10. Switched to Johnny’s account:

   ```bash
   su - johnny
   ```

11. Checked Johnny’s command history:

   ```bash
   history
   ```

12. Identified the accidentally typed root password.
13. Switched to the root account:

   ```bash
   su - root
   ```

14. Read the flag file:

   ```bash
   cat flag.txt
   ```

---

## Lab Evidence

### SSH Authentication and Privilege Escalation

- ossecurity-task3-ssh-login
- ossecurity-task3-whoami-output
- ossecurity-task3-directory-listing
- ossecurity-task3-draft-file
- ossecurity-task3-command-history
- ossecurity-task3-root-login
- ossecurity-task3-flag

---

## Personal Reflection

This room showed how weak passwords, poor security habits, and exposed command history can lead to unauthorized access and privilege escalation. Practicing SSH authentication and switching users helped me better understand how attackers can move through Linux systems when basic security controls are weak.