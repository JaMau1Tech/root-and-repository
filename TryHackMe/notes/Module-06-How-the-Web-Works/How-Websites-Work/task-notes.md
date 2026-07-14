# How Websites Work

## Status

✅ Completed

---

## Overview

This room introduced how modern websites are built by explaining the relationship between client-side and server-side technologies. It covered HTML, JavaScript, website architecture, sensitive data exposure, and HTML injection, providing the foundation for understanding web application security.

---

## Objectives

- Understand front-end and back-end architecture
- Learn the purpose of HTML
- Learn the role of JavaScript
- Identify sensitive data exposure
- Understand HTML injection
- Build a foundation for future web security topics

---

## Key Concepts

### Website Architecture

A modern website consists of two primary components:

#### Front End (Client-Side)

Responsible for rendering content in the user's browser.

Examples include:

- HTML
- CSS
- JavaScript

#### Back End (Server-Side)

Responsible for processing requests and returning responses.

Examples include:

- Web servers
- Databases
- APIs
- Authentication

---

### HTML

HyperText Markup Language is the standard language used to build the structure of web pages.

Common elements include:

- `<html>`
- `<head>`
- `<body>`
- `<h1>`
- `<p>`
- `<img>`
- `<button>`

Common attributes:

- id
- class
- src

---

### JavaScript

JavaScript provides interactivity for web pages.

Examples include:

- Dynamic page updates
- DOM manipulation
- Button events
- User interaction

Important concepts:

- `<script>`
- `document.getElementById()`
- `innerHTML`
- `onclick`

---

### Sensitive Data Exposure

Sensitive data exposure occurs when confidential information is unintentionally exposed to users.

Examples:

- Passwords
- API Keys
- Tokens
- Hidden URLs
- HTML comments

Common discovery methods:

- View Page Source
- Browser Developer Tools

---

### HTML Injection

HTML Injection occurs when user input is displayed without sanitization.

Potential risks include:

- Fake links
- Fake login forms
- Website defacement
- Phishing attacks

Mitigations:

- Input validation
- Input sanitization
- Output encoding

Golden Rule:

> Never trust user input.

---

## Practical Skills

- Understanding website architecture
- Reading HTML
- Editing HTML
- Using JavaScript
- Viewing page source
- Finding exposed credentials
- Performing HTML injection

---

## Skills Developed

### Web Technologies

- Front-End Fundamentals
- Back-End Fundamentals
- HTML
- JavaScript
- DOM Manipulation

### Security

- Source Code Review
- Sensitive Data Exposure
- HTML Injection
- Input Validation
- Input Sanitization

### Practical

- HTML Editing
- JavaScript Manipulation
- Web Page Analysis
- Client-side Security Testing

---

## Real-World Relevance

Understanding how websites are constructed is essential before learning web application penetration testing.

The concepts introduced in this room directly prepare you for future topics such as:

- Cross-Site Scripting (XSS)
- SQL Injection
- Authentication vulnerabilities
- API security
- OWASP Top 10

---

## Personal Reflection

This room connected the networking concepts learned in DNS and HTTP with the technologies used to build modern websites. It also introduced common client-side security issues that form the basis for many web application attacks.