# Become a Hacker

## Status

✅ Completed

---

## Room Information

| Difficulty | Duration | Module |
|------------|----------|--------|
| Easy | 30 Minutes | Module 07 – Attacks and Defenses |

---

# Overview

This room introduced the fundamentals of offensive security and the ethical hacker mindset. It demonstrated how security professionals identify, assess, and safely exploit weaknesses before malicious attackers can. Practical exercises included discovering hidden web pages using Gobuster and performing an automated dictionary attack using Hydra to demonstrate how seemingly small weaknesses can be chained together.

---

# Learning Objectives

- Understand offensive security principles
- Learn common offensive security terminology
- Understand penetration testing methodology
- Discover hidden web resources
- Perform basic web enumeration
- Use Gobuster for directory enumeration
- Use Hydra for password auditing
- Understand how attackers chain weaknesses together
- Develop an offensive security mindset

---

# Tasks Completed

## ✅ Task 1 – Introduction

### Topics

- Offensive Security
- Ethical Hacking
- Penetration Testing
- Security Assessments

### Key Concepts

- Offensive security is proactive.
- Ethical hacking requires authorization.
- Security testing improves defensive posture.
- Attackers think differently than users.

---

## ✅ Task 2 – Finding Weaknesses

### Topics

- Enumeration
- Hidden Resources
- Gobuster
- Wordlists

### Practical Exercise

- Located hidden web pages
- Enumerated directories
- Identified exposed login portal
- Verified HTTP response codes

### Commands Used

```bash
gobuster dir --url http://www.onlineshop.thm/ -w /usr/share/wordlists/dirbuster/directory-list.txt
```

### Findings

Hidden Page

```
/login
```

HTTP Status

```
200 OK
```

---

## ✅ Task 3 – Chaining Weaknesses

### Topics

- Authentication
- Credentials
- Dictionary Attacks
- Hydra

### Practical Exercise

- Tested common passwords
- Automated password testing
- Logged into the application
- Retrieved the secret message

### Commands Used

```bash
hydra -l admin -P passlist.txt www.onlineshop.thm http-post-form "/login:username=^USER^&password=^PASS^:F=incorrect" -V
```

### Results

Username

```
admin
```

Password

```
qwerty
```

Secret Message

```
THM{born_to_hack!}
```

Failed Attempts

```
17
```

---

## ✅ Task 4 – Conclusion

### Key Takeaways

- Enumeration is the first phase of offensive security.
- Hidden pages increase attack surface.
- Weak passwords are a common vulnerability.
- Automation dramatically improves testing efficiency.
- Ethical hackers identify and report weaknesses responsibly.

---

# Tools Used

- Gobuster
- Hydra
- Web Browser
- Linux Terminal

---

# Skills Developed

## Offensive Security

- Ethical Hacking
- Penetration Testing
- Enumeration
- Attack Surface Analysis
- Dictionary Attacks
- Credential Testing

## Web Security

- Hidden Page Discovery
- HTTP Response Analysis
- Authentication Testing

## Security Tools

- Gobuster
- Hydra

---

# Commands Learned

```bash
gobuster dir --url http://www.onlineshop.thm/ -w /usr/share/wordlists/dirbuster/directory-list.txt
```

```bash
hydra -l admin -P passlist.txt www.onlineshop.thm http-post-form "/login:username=^USER^&password=^PASS^:F=incorrect" -V
```

---

# Lessons Learned

- Small weaknesses often become serious when combined.
- Enumeration should always precede exploitation.
- Automation is essential during security assessments.
- Authorization and scope define ethical hacking.
- Strong passwords significantly improve security.

---

# Room Summary

This room provided a practical introduction to offensive security by combining theory with hands-on exercises. Using Gobuster and Hydra, I identified hidden web resources, tested authentication mechanisms, and demonstrated how attackers chain vulnerabilities together to gain unauthorized access. The exercises reinforced the importance of proactive security testing, strong authentication practices, and responsible ethical hacking.