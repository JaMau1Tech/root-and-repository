# Linux Fundamentals (Pt2)

**Room:** [Linux Fundamentals (Pt2)](https://tryhackme.com/room/linuxfundamentalspart2)
**Platform:** TryHackMe
**Collection:** Linux Fundamentals
**Status:** ✅ Complete
**Target VM:** Ubuntu (SSH via TryHackMe AttackBox)

---

## Room Overview

The second room in the Linux Fundamentals series focused on interacting with Linux systems remotely using SSH, expanding command functionality with flags and switches, working with the filesystem, understanding Linux permissions, switching between users, and exploring the Linux directory structure. Unlike Part 1's browser-based terminal, this room introduced remote administration using Secure Shell (SSH), mirroring how Linux systems are managed in enterprise environments.

---

## Key Concepts

- **Secure Shell (SSH):** The industry-standard protocol for securely administering remote Linux systems. SSH encrypts all communication between the client and server, protecting credentials and commands while they traverse the network.
- **Flags & Switches:** Commands can be extended using short (`-h`) and long (`--help`) options to modify their default behavior. Rather than memorizing every option, Linux administrators commonly rely on built-in documentation.
- **Linux Documentation:** `--help` provides a quick overview of available command options, while `man` displays comprehensive documentation including syntax, descriptions, and examples. Learning to use documentation efficiently is more valuable than memorizing command syntax.
- **Filesystem Management:** Learned how to create (`touch`, `mkdir`), copy (`cp`), move/rename (`mv`), remove (`rm`), and identify (`file`) files and directories.
- **Permissions:** Linux controls access through three permission groups (Owner, Group, Others) and three permission types (Read, Write, Execute). These permissions can be represented symbolically (`rwxr-xr-x`) or numerically (755).
- **Directory Structure:** Important Linux directories include `/etc` (configuration), `/var` (variable data and logs), `/root` (root user's home directory), and `/tmp` (temporary storage).

---

## Commands / Tools Used

| Command | Purpose |
|---|---|
| `ssh user@IP` | Securely connect to a remote Linux machine |
| `ls -a`, `ls -l`, `ls -lh` | Display directory contents with additional information |
| `--help` | Display quick command usage |
| `man <command>` | Open the manual page for a command |
| `touch` | Create an empty file |
| `mkdir` | Create a directory |
| `cp` | Copy files or directories |
| `mv` | Move or rename files/directories |
| `rm` / `rm -R` | Remove files or directories |
| `file` | Identify a file's actual type |
| `su` / `su -l` | Switch user accounts |
| `pwd` | Display the current working directory |
| `cat` | Display file contents |

---

## Administrative Tasks Performed

- Established a secure SSH session from the TryHackMe AttackBox to the target Ubuntu system.
- Used `ls` with multiple flags to display hidden files and detailed permission information.
- Navigated Linux manual pages using `man` and located command options using `--help`.
- Created, copied, moved, renamed, and removed files and directories using Linux filesystem commands.
- Verified unknown file types using the `file` command rather than relying solely on file extensions.
- Interpreted Linux file ownership and permissions using `ls -l`.
- Switched to another user account using `su` to access a protected file.
- Explored core Linux system directories including `/etc`, `/var`, `/root`, and `/tmp`.
- Completed additional self-directed practice beyond the room requirements to reinforce filesystem commands.

---

## Security Concepts Covered

- **Encrypted Remote Administration:** SSH encrypts all communication between client and server, protecting authentication credentials and administrative commands from interception.
- **Principle of Least Privilege:** Linux permissions restrict access based on ownership and group membership, reducing unnecessary privileges.
- **File Verification:** The `file` command identifies a file's actual contents rather than trusting file extensions, helping detect disguised or malicious files.
- **Privilege Separation:** Successfully demonstrated that non-root users cannot access protected directories such as `/root`, reinforcing Linux's access control model.
- **Temporary Storage:** `/tmp` is writable by users but should not be trusted for storing sensitive or persistent information.

---

## Engineering Challenges

- **Permission Restriction:** Attempted to access `/root` while operating as a standard user and correctly received a "Permission denied" error, reinforcing Linux's permission model.
- **Filename Troubleshooting:** During additional practice, accidentally referenced an incorrect filename while using the `file` command. Read the error message, identified the mistake, corrected the filename, and successfully completed the task.
- **Hands-On Reinforcement:** Built an additional practice directory beyond the room objectives to repeatedly practice creating, copying, moving, renaming, identifying, and deleting files until the workflow became natural.

---

## Lessons Learned

- SSH is the primary method used to administer Linux systems remotely in enterprise environments.
- Reading Linux manual pages is a faster and more sustainable approach than attempting to memorize every command.
- Linux permissions enforce security through ownership and access controls rather than relying solely on user trust.
- File extensions alone should never be trusted; administrators should verify file types using the `file` command.
- Small command-line mistakes are common, and carefully reading Linux error messages is an essential troubleshooting skill.

---

## Interview Talking Points

- **Objective:** Learn secure Linux remote administration using SSH while expanding command-line proficiency with filesystem management, permissions, and Linux system directories.
- **Challenge:** Transitioned from browser-based terminal access to authentic remote administration over SSH while learning several new filesystem management commands and Linux permission concepts.
- **Investigation:** Used Linux manual pages (`man`) and built-in help documentation (`--help`) to independently research command options rather than relying on external references. Practiced interpreting Linux permission strings and troubleshooting command-line errors during additional hands-on exercises.
- **Resolution:** Successfully completed all eight room tasks, securely connected to a remote Linux system, managed files and directories, switched users to access protected resources, explored core Linux directories, and earned the **cat linux.txt** badge.
- **Skills Demonstrated:** Remote Linux administration (SSH), command-line documentation, filesystem management, Linux permissions, user management, directory navigation, troubleshooting, and independent problem-solving through additional hands-on practice.

---

**Documentation Standard:** Root & Repository Standalone TryHackMe Workflow v3.1