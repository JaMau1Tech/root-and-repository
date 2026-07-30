# Linux Fundamentals (Pt1)

**Room:** [Linux Fundamentals (Pt1)](https://tryhackme.com/room/linuxfundamentalspart1)
**Platform:** TryHackMe
**Collection:** Linux Fundamentals
**Status:** ✅ Complete
**Target VM:** Ubuntu (browser-based lab machine)

---

## Room Overview

First room in the Linux Fundamentals series, introducing the terminal as the primary interface for Linux (in contrast to Windows' GUI-first approach). Covers identity (`whoami`), output (`echo`), navigation (`ls`, `cd`, `cat`, `pwd`), searching (`find`, `grep`), and shell operators/redirection (`&`, `&&`, `>`, `>>`).

---

## Key Concepts

- **Linux's real-world footprint:** far broader than desktop use — web servers, embedded/car systems, Point of Sale systems, critical infrastructure (traffic controllers, industrial sensors), and phones (Android). Command-line fluency matters more for Linux roles than typical Windows admin roles because so much real-world Linux infrastructure is headless (no GUI at all).
- **Terminal fundamentals:** a command is an instruction; output is the system's response. Interacting with Linux is a conversational command-in/output-out loop.
- **Identity:** `whoami` shows the current user — foundational in security work since privilege and permissions are entirely user-context-dependent; it's typically the first command run after gaining any shell access.
- **Output:** `echo` prints specified text; multi-word text requires quotes (`echo "hello world"`). Critically, `echo "command"` prints the literal string, it does **not execute** the named command — a common early mixup.
- **Navigation:** `ls` (list), `cd` (change directory), `cat` (print file contents), `pwd` (print working directory/current location). Folders and files are color-coded in the terminal for quick visual identification.
- **Searching:** `find -name <filename>` locates files by name across the filesystem; `grep "<text>" <file>` searches inside a file's contents for a matching pattern — dramatically faster and more reliable than manually scrolling through large files (e.g., extracting a flag from a hundreds-of-lines-long web server log).
- **Shell operators:**
  - `&` — run a command in the background, don't wait for it to finish
  - `&&` — run sequentially; the second command only runs if the first succeeds ("dominoes")
  - `>` — redirect output to a file, **overwriting** existing content
  - `>>` — redirect output to a file, **appending** to existing content (never overwrites)
- **Command output vs. literal string:** `command > file` captures the *result* of running a command; `echo "text" > file` writes the *literal text* typed, regardless of whether that text happens to look like a command name.

---

## Commands / Tools Used

| Command | Purpose |
|---|---|
| `whoami` | Show current user |
| `echo <text>` | Output text; `echo "text"` for multi-word strings |
| `ls` | List directory contents |
| `cd <folder>` | Change directory |
| `cat <file>` | Print file contents |
| `pwd` | Print current working directory |
| `find -name <filename>` | Search for a file by name |
| `grep "<text>" <file>` | Search inside a file for matching text |
| `>` / `>>` | Redirect output (overwrite / append) |
| `&` / `&&` | Background execution / sequential execution on success |

---

## Administrative Tasks Performed

- Ran `whoami` and multiple `echo` variations (including quoted multi-word strings) to confirm output behavior
- Navigated the home folder with `ls`, identified 4 folders (`folder1`–`folder4`) plus `access.log`
- Used `cd folder1` → `ls` → `cat passwords.txt` to locate and read the folder's file (`password123`)
- Confirmed location with `pwd` (`/home/tryhackme/folder1`)
- Used `grep "THM" access.log` to extract a flag from a large web server log file (`THM{ACCESS}`)
- Tested `>` and `>>` redirection directly, confirming `>>` appends rather than overwrites (contradicting the room's own task text, which incorrectly described append behavior as overwriting)
- Completed a 12-question practice set covering identity, navigation, searching, and operators/redirection to reinforce the room's material

---

## Security Concepts Covered

- `whoami` as a near-universal first command in both legitimate administration and post-exploitation contexts, since it establishes what a session's privileges actually are
- `grep`-based log searching as a foundational technique for incident response and log analysis — finding specific indicators (IPs, error patterns, credentials) in large files without manual scrolling
- The practical distinction between capturing a command's *output* (`command > file`) versus writing a *literal string* (`echo "text" > file`) — a subtle but important scripting/automation distinction
- `&&` as a safe command-chaining pattern that only proceeds on success, relevant to writing reliable scripts/automation

---

## Engineering Challenges

- **Room content error:** Task 5's instructions describe using `>>` and then state the result "replaces the previous text entirely" — this incorrectly describes `>` (overwrite) behavior while discussing `>>` (append). Verified via direct terminal testing that `>>` correctly appends (confirmed twice, building a 2-line then 3-line file), meaning the room's own text is inaccurate and should not be trusted over direct observation.
- **Practice-round conceptual gap:** initially wrote `echo "whoami" > identity.txt` intending to capture the output of the `whoami` command, but `echo "whoami"` in quotes only prints the literal string "whoami" — it does not execute the command. Corrected to `whoami > identity.txt` to properly capture command output.
- **Command-chaining gap:** needed additional explanation on `&&` (e.g., `mkdir new_folder && cd new_folder`) before it was fully solidified — flagged as an area needing more hands-on repetition rather than immediate correct recall.

---

## Lessons Learned

- Terminal-provided documentation (even from the platform itself) can contain errors — direct hands-on verification (testing `>>` behavior directly rather than trusting the written description) is a more reliable source of truth than instructional text alone.
- The distinction between "run a command and capture its output" vs. "print a literal string that happens to look like a command" is a foundational scripting concept worth reinforcing early, since it's an easy and common mistake.
- `&&` chaining logic (proceed only on success) is conceptually different from simply running two commands back to back, and benefits from repeated hands-on practice to fully internalize.

---

## Interview Talking Points

- **Objective:** Build foundational Linux terminal fluency — identity, navigation, file searching, and shell operators/redirection — as the first room in the Linux Fundamentals series, using a browser-based Ubuntu lab.
- **Challenge:** Identified and worked through a factual error in the room's own instructional text regarding `>>` redirection behavior; also surfaced and corrected a personal misunderstanding of the difference between capturing command output versus echoing a literal string.
- **Investigation:** Directly tested redirection behavior in the terminal rather than taking the room's description at face value, building a multi-line file with `>>` to empirically confirm append (not overwrite) behavior.
- **Resolution:** Completed all 5 tasks, correctly identifying user context, generating and reading file output, extracting a flag from a large log file via `grep`, and correctly using redirection operators — followed by a 12-question self-directed practice set to reinforce the material, achieving 10/12 correct with two concepts flagged for further repetition.
- **Skills Demonstrated:** Linux terminal fundamentals, file navigation and content inspection, pattern-based file searching (`grep`, `find`), shell operator logic (background execution, conditional chaining), output redirection, and critical evaluation of documentation accuracy against direct empirical testing.

---

**Documentation Standard:** Root & Repository Standalone TryHackMe Workflow v3.1