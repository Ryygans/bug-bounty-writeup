# Open Redirect Vulnerability

<p align="center">
  <img src="or.png" width="650" height="500">
</p>

---

## Summary
An **Open Redirect** is a vulnerability that allows an application to redirect users to an arbitrary external website based on user-controlled input.

This issue is commonly found in endpoints that handle navigation flows such as **login**, **registration**, or other authentication-related processes, where a redirection parameter is used after user interaction.

---

## Affected URLs
- https://redacted.target.com/login?referrer=
- https://redacted.target.com/register?referrer=

---

## Severity
- ⚠️ **Medium**
- **CWE-601: Open Redirect**

---

## Steps to Reproduce
```text
1. Visit a page suspected to be vulnerable to open redirect.
2. Append an external URL to the `referrer` parameter.
   Example:
   https://redacted.target.com/login?referrer=https://malicious.site/
3. If testing the `login` or `register` endpoint, complete the required form fields first.
4. Submit the form or press Enter.
5. Observe that the application redirects the user to the external website.

# Proof of Concept
```bash
https://redacted.target.com/login?referrer=https://google.com/
```

# Impact
```text
The primary impact of an open redirect vulnerability is phishing.
Attackers can leverage a trusted domain to redirect users to malicious websites, increasing the credibility of phishing attacks and the likelihood of credential theft or malware delivery.
```

# Mitigation and Remediation
```text
To properly mitigate open redirect vulnerabilities:
• Avoid using user-supplied input directly in redirect destinations.
• Implement a server-side allowlist of trusted redirect URLs or domains.
• Use internal identifiers instead of full URLs for redirection logic.
• If external redirection is unavoidable, display a warning or confirmation page before redirecting users.
```

# Disclosure Information
```text
> Reporting Date: July 2024
> Status:         Resolved
> Bounty?         Coupon Code
```
