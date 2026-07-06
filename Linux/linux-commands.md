# Linux Commands

This document contains commonly used Linux commands that I am learning and using throughout my cybersecurity journey.

---

# Navigation Commands

## pwd

```bash
pwd
```

Displays the current working directory.

---

## ls

```bash
ls
```

Lists files and directories.

### Useful Options

```bash
ls -l
ls -la
```

- `-l` shows detailed information.
- `-a` shows hidden files.

---

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

- `cd ..` moves up one directory.
- `cd ~` returns to the home directory.

---

# File Management Commands

## mkdir

```bash
mkdir foldername
```

Creates a new directory.

---

## touch

```bash
touch filename.txt
```

Creates a new file.

---

## cp

```bash
cp source destination
```

Copies files.

Example:

```bash
cp notes.txt backup.txt
```

---

## mv

```bash
mv oldname.txt newname.txt
```

Moves or renames files.

---

## rm

```bash
rm filename
rm -r foldername
```

Deletes files and directories.

⚠️ Be careful with `rm` because deleted files usually cannot be recovered.

---

# File Viewing Commands

## cat

```bash
cat filename.txt
```

Displays the contents of a file.

---

## nano

```bash
nano filename.txt
```

Opens a file in the Nano text editor.

---

## less

```bash
less filename.txt
```

Displays file contents one page at a time.

Press:

- `q` to quit
- `Space` to move forward
- `b` to move backward

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

---

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

# Cybersecurity Relevance

Learning Linux commands is important because:

- Most cybersecurity tools run on Linux.
- Penetration testing often requires command-line skills.
- Linux administration is essential for servers and security operations.
- Understanding permissions helps identify security misconfigurations.

---

# Lessons Learned

- Linux is heavily command-line driven.
- Small commands can make major system changes.
- Always understand a command before running it with `sudo`.
- Practice commands in a virtual machine before using them on production systems.