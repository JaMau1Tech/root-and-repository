# Linux Fundamentals (Pt3)

**Room:** [Linux Fundamentals (Pt3)](https://tryhackme.com/room/linuxfundamentalspart3)  
**Platform:** TryHackMe  
**Collection:** Linux Fundamentals  
**Status:** ✅ Complete  
**Target VM:** Ubuntu (browser-based lab machine)

---

## Room Overview

Final room in the Linux Fundamentals series, transitioning from basic Linux usage into core Linux administration. Covers terminal text editors, file transfer utilities, process management, task automation with cron, package management using APT, and system log analysis. These topics represent many of the routine responsibilities performed by Linux system administrators and cybersecurity professionals.

---

## Key Concepts

- **Terminal text editors:** Introduced **Nano** as a beginner-friendly command-line editor for creating and modifying files directly from the terminal. Also introduced **Vim**, a more advanced editor commonly used by experienced Linux administrators and developers due to its customization, efficiency, and widespread availability.
- **File transfer utilities:** Learned multiple methods of transferring files between systems. `wget` downloads files from HTTP/HTTPS servers, `scp` securely copies files between hosts using SSH encryption, and Python's built-in `http.server` module can quickly host files for download on a local network.
- **Process management:** Every running program is a **process** with a unique **Process ID (PID)** managed by the Linux kernel. Used `ps`, `ps aux`, and `top` to inspect running processes and learned to terminate processes with `kill` using signals such as **SIGTERM**, **SIGKILL**, and **SIGSTOP**.
- **Service management:** Introduced **systemd** and the `systemctl` utility to start, stop, enable, disable, and inspect services. Learned the difference between services running immediately and services configured to automatically start during boot.
- **Foreground vs background processes:** Commands normally execute in the foreground. Learned to move long-running processes into the background using `&` or `Ctrl + Z`, then restore them using `fg`.
- **Automation with cron:** Linux automates recurring administrative tasks through **cron** and **crontab**. Learned the six-field cron scheduling format and interpreted scheduled jobs, including special entries such as `@reboot`.
- **Package management:** Ubuntu manages software using **APT** repositories. Learned how repositories provide trusted software, how **GPG keys** verify package integrity, and how commands such as `apt update`, `apt install`, and `apt remove` maintain software.
- **System logging:** Linux stores logs primarily in `/var/log`. Examined Apache access logs to identify client activity, demonstrating how logs support troubleshooting, performance monitoring, and incident response.

---

## Commands / Tools Used

| Command | Purpose |
|---|---|
| `nano <file>` | Create or edit a file |
| `wget <url>` | Download files via HTTP/HTTPS |
| `scp` | Securely copy files over SSH |
| `python3 -m http.server` | Start a lightweight web server |
| `ps` | View running processes |
| `ps aux` | View all running processes |
| `top` | Monitor processes in real time |
| `kill <PID>` | Terminate a process |
| `systemctl` | Manage Linux services |
| `fg` | Bring a background process to the foreground |
| `crontab -e` | Edit scheduled cron jobs |
| `crontab -l` | View scheduled cron jobs |
| `apt update` | Refresh package repository information |
| `apt install <package>` | Install software |
| `apt remove <package>` | Remove installed software |
| `cat` | Display file contents |
| `grep` | Search file contents |
| `less` | View large files |

---

## Administrative Tasks Performed

- Edited files using Nano and recovered the room flag from the provided file.
- Started a Python HTTP server to share files across the network.
- Downloaded files from the hosted web server using `wget`.
- Examined running processes using `ps aux`.
- Identified a specific running process containing the room flag.
- Learned how Linux services are managed using `systemctl`.
- Reviewed cron scheduling and interpreted the deployed machine's scheduled task.
- Examined Ubuntu package management concepts including repositories, GPG keys, and APT.
- Navigated Apache log files within `/var/log/apache2`.
- Identified the visiting client IP address and requested resource from the Apache access log.

---

## Security Concepts Covered

- SSH provides encrypted file transfers through **SCP**, protecting confidentiality during transmission.
- Linux process management allows administrators to safely terminate malicious or unresponsive software.
- Services should be configured to start only when necessary, following the Principle of Least Privilege.
- Cron automation reduces manual administration while ensuring repetitive maintenance tasks execute consistently.
- Software repositories and GPG keys protect systems from installing untrusted or modified software.
- Apache access logs provide forensic evidence during incident response by recording client IP addresses, timestamps, requested resources, and HTTP responses.
- System logs are foundational sources for troubleshooting, monitoring, and detecting suspicious activity.

---

## Engineering Challenges

- Initially interpreted the room's cron question using the system-wide `/etc/crontab` schedule instead of the user crontab viewed with `crontab -l`. Identified that the expected answer referenced the `@reboot` scheduled task rather than the system maintenance jobs.
- Encountered **Permission denied** when attempting to read `access.log`. Investigated alternate log files and successfully analyzed `access.log.1`, identifying both the client's IP address and the requested resource.
- Reinforced the distinction between user-specific scheduled jobs and system-wide cron configuration files while troubleshooting the automation task.

---

## Lessons Learned

- Nano provides an accessible introduction to terminal-based text editing, while Vim offers greater flexibility for advanced administration.
- Lightweight tools such as Python's built-in HTTP server simplify temporary file sharing during administration and testing.
- Understanding Linux process management is essential for troubleshooting, service administration, and security investigations.
- Cron scheduling requires careful interpretation of scheduling fields and special directives such as `@reboot`.
- Package repositories combined with GPG verification provide a secure software installation process.
- Log analysis often requires investigating archived or rotated logs rather than only the active log file.
- Permission errors frequently indicate that an administrator should inspect alternate files or investigate file ownership before assuming a system issue.

---

## Interview Talking Points

- **Objective:** Complete the Linux Fundamentals learning path by transitioning from basic Linux usage into practical Linux administration concepts including process management, automation, package management, and log analysis.
- **Challenge:** Troubleshot permission restrictions while analyzing Apache logs and distinguished between user crontabs and system-wide cron schedules to correctly interpret scheduled automation.
- **Investigation:** Examined running processes, scheduled cron jobs, hosted files using Python's HTTP server, transferred files with `wget`, and analyzed Apache access logs to identify client activity.
- **Resolution:** Successfully completed all administrative exercises involving Nano, Python HTTP Server, `wget`, process management, cron scheduling, package management concepts, and Apache log analysis while validating multiple room flags.
- **Skills Demonstrated:** Linux administration, process management, service management, automation, package management, secure file transfer, web server hosting, system log analysis, troubleshooting methodology, and command-line proficiency.

---

**Documentation Standard:** Root & Repository Standalone TryHackMe Workflow v3.1