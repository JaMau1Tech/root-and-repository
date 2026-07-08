# Linux Commands

This document contains commonly used Linux commands learned during cybersecurity practice.

---

# Navigation Commands

## pwd

```bash
pwd
```

Displays the current working directory.

## ls

```bash
ls
```

Lists files and directories.

Useful options:

```bash
ls -l
ls -la
```

- `-l` shows detailed information.
- `-a` shows hidden files.

## cd

```bash
cd directory-name
```

Changes directories.

Examples:

```bash
cd Documents
cd ..
cd ~
```

---

# File Management Commands

## mkdir

```bash
mkdir foldername
```

Creates a new directory.

## touch

```bash
touch filename.txt
```

Creates a new file.

## cp

```bash
cp source destination
```

Copies files.

Example:

```bash
cp notes.txt backup.txt
```

## mv

```bash
mv oldname.txt newname.txt
```

Moves or renames files.

## rm

```bash
rm filename
rm -r foldername
```

Deletes files and directories.

Warning: deleted files are usually difficult to recover.

---

# File Viewing Commands

## cat

```bash
cat filename.txt
```

Displays the contents of a file.

## nano

```bash
nano filename.txt
```

Opens a file in the Nano text editor.

## less

```bash
less filename.txt
```

Displays file contents one page at a time.

Useful keys:

- `q` quits
- `Space` moves forward
- `b` moves backward

---

# Permissions and Administrative Commands

## chmod

```bash
chmod permissions filename
```

Changes file permissions.

Example:

```bash
chmod +x script.sh
```

Makes a file executable.

## chown

```bash
sudo chown user file
```

Changes file ownership.

## sudo

```bash
sudo command
```

Runs a command with administrative privileges.

Example:

```bash
sudo apt update
```

---

# Searching Commands

## find

```bash
find . -name filename.txt
```

Searches for files.

## grep

```bash
grep "text" filename.txt
```

Searches inside files.

---

# Package Management

## apt update

```bash
sudo apt update
```

Updates the package list.

## apt upgrade

```bash
sudo apt upgrade
```

Upgrades installed packages.

---

# Cybersecurity Relevance

Linux commands are important because:

- Most cybersecurity tools run on Linux.
- Penetration testing requires command-line skills.
- Linux administration is essential for servers.
- Permissions help identify security misconfigurations.
- Searching files is useful during investigations.

---

# Lessons Learned

- Linux is command-line driven.
- Small commands can make major system changes.
- Always understand a command before using `sudo`.
- Practice commands in a lab before using them on important systems.
