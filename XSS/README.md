# Cross-Site Scripting (XSS)
![Pentest](https://img.shields.io/badge/Pentest-XSS-orange?logo=linux)
![OWASP](https://img.shields.io/badge/OWASP-Top%2010-critical?logo=owasp)
![Security](https://img.shields.io/badge/Security-Research-red?logo=security)


This directory contains documentation and proof-of-concept examples related to **Cross-Site Scripting (XSS)** vulnerabilities.  
XSS is a common web security issue that allows attackers to inject malicious JavaScript code into web applications, which is then executed in a victim’s browser.

The purpose of this repository is **educational and security research only**.

---

## What is XSS?
Cross-Site Scripting (XSS) occurs when an application includes untrusted user input in a web page without proper validation or output encoding.  
This can allow attackers to execute arbitrary JavaScript in the context of the affected website.

---

## Types of XSS

### 1. Reflected XSS
Reflected XSS occurs when user input is immediately returned by the web application in an HTTP response without proper sanitization.

**Common characteristics:**
- Payload is delivered via URL or request parameters
- Requires user interaction (e.g., clicking a malicious link)
- Not stored on the server

📂 Folder: `./reflected/`

---

### 2. Stored XSS
Stored XSS (also known as Persistent XSS) occurs when malicious input is stored on the server (e.g., database, comments, messages) and later rendered to other users.

**Common characteristics:**
- Payload is permanently stored
- Affects multiple users
- High impact vulnerability

📂 Folder: `./stored/`

---

### 3. DOM-Based XSS
DOM-Based XSS occurs when the vulnerability exists entirely in the client-side JavaScript.  
The malicious payload is never sent to the server, but is executed due to insecure DOM manipulation.

**Common characteristics:**
- Client-side only
- Occurs in JavaScript logic
- Harder to detect by traditional scanners

📂 Folder: `./dom/`

---

## Repository Structure
```text
xss/
├── reflected/
│   └── README.md
├── stored/
│   └── README.md
├── dom/
│   └── README.md
└── README.md
```

---

# Impact of XSS
XSS vulnerabilities may lead to:
- Session Hijacking
- Credential Theft
- Phishing Attacks
- Malicious Redirect
- Execution of actions as authenticated users

---

# Mitigation and Remediation
General best practices to prevent XSS:<br>
- Output encoding based on context (HTML, JS, URL)
- Strong input validation and sanitization
- Implementing Content Security Policy (CSP)
- Avoiding unsafe DOM methods (innerHTML, document.write)
- Using modern frameworks with built-in protections

---

# Disclaimer
This repository is intended for educational purposes and authorized security testing only.
<br>Do not use the provided information or techniques on systems without proper permission.

---

# References
- https://owasp.org/www-community/attacks/xss/
- https://portswigger.net/web-security/cross-site-scripting
