# PHPInfo Information Disclosure

## Summary

A PHPInfo page was found to be publicly accessible without authentication.

The `phpinfo()` function is commonly used for debugging and displaying detailed information about the PHP environment. When exposed on a production server, it may disclose technical information that should not be publicly accessible.

This finding was identified during authorized security research using my own reconnaissance tool, `dirscanner`.

## Affected URL

https://redacted.target.com/info.php

## Severity

⚠️ Medium

CWE-200: Exposure of Sensitive Information to an Unauthorized Actor

## Steps to Reproduce

1. Identify publicly accessible PHP files or diagnostic endpoints on an authorized target.
2. Access the suspected `phpinfo()` page.
3. Observe that the PHP configuration information is accessible without authentication.
4. Review the information disclosed by the page.

## Proof of Concept

https://redacted.target.com/info.php

The page publicly exposes PHP environment and server configuration information.

Sensitive information from the original target has been redacted from this write-up.

## Information Disclosed

Depending on the server configuration, a publicly accessible PHPInfo page may reveal information such as:

- PHP version
- Web server information
- Loaded PHP modules
- Server environment
- File system paths
- PHP configuration values
- Environment variables
- Request and server information

## Impact

Exposing PHPInfo information can provide attackers with useful intelligence about the application's underlying environment.

This information may help an attacker:

- Fingerprint the server environment
- Identify outdated or vulnerable components
- Understand the application's directory structure
- Identify enabled PHP modules
- Discover configuration details useful for further security research

The actual impact depends on the information exposed by the PHPInfo page.

## Mitigation and Remediation

To properly mitigate this issue:

• Remove unnecessary `phpinfo()` pages from production environments.

• Restrict diagnostic and debugging endpoints to authorized administrators.

• Disable unnecessary information disclosure in production.

• Review PHP and web server configuration before deploying applications.

• Avoid exposing environment variables or sensitive configuration values through diagnostic pages.

## Disclosure Information

> Reporting Method: Responsible Disclosure
>
> Discovery Method: `dirscanner`
>
> Recognition: Letter of Recognition
>
> Target: Redacted
>
> Status: Resolved
