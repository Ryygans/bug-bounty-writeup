# Reflected Cross-Site Scripting (XSS)

# Summary
**Reflected Cross-Site Scripting (XSS)** is a web security vulnerability that allows an attacker to inject and execute malicious JavaScript code in a victim’s browser.  
This vulnerability occurs when a web application **fails to properly validate or sanitize user input** (such as URL parameters or form inputs) and **reflects the input directly in the HTTP response** without proper output encoding.

As a result, the injected script is executed in the context of the affected domain.

---

# Affected URLs
- https://redacted.yourtarget.com/search?q=

---

# Severity
- **Medium ⚠**
- **CWE-79: Improper Neutralization of Input During Web Page Generation _(Cross-site Scripting)_**
The severity may increase to High if the vulnerable endpoint is accessible to authenticated users or processes sensitive data.

---

# Steps to Reproduce
```text
1. Navigate to a web page that accepts user input via URL parameters.
2. Inject a simple JavaScript payload into the parameter.
3. Example payload:
   <script>alert(document.domain)</script>
4. Full URL:
   https://redacted.yourtarget.com/search?q=<script>alert(document.domain)</script>
5. Press Enter.
6. The application reflects the injected payload and executes the script in the browser.
```

---

# Proof of Concept
- https://pmb.redacted.sch.id/search?q=<script>prompt(document.cookie)</script>
<br><br>Result:
<br>A JavaScript prompt dialog appears displaying the cookie or domain, confirming successful script execution.
---

# Impact
```text
Successful exploitation of this Reflected XSS vulnerability may allow an attacker to:
- Steal user session cookies (Session Hijacking)
- Perform phishing attacks using trusted domains
- Redirect users to malicious websites
- Execute actions on behalf of authenticated users
- Damage the reputation and trust of the application

When combined with social engineering, this vulnerability can lead
to serious security risks.

```

---

# Mitigation and Remediation
**Mitigating Reflected XSS involves a layered defense: Output Encoding user-provided data (converting < to &lt;) before display, implementing strong Input Validation/Sanitization (filtering or rejecting bad characters), using Content Security Policy (CSP) to restrict script sources, and employing Web Application Firewalls (WAFs) to block malicious requests. Additionally, developers should use security frameworks with built-in protections and keep systems updated.**

---

# Disclosure Information
```text
> Reporting Date: September 2024
> Status:         Resolved
> Bounty?         2M (Makasih MAs)
```
