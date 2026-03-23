# Security Policy

## Supported Versions

Only the **latest released version** of each ColdBrew package receives security updates.

| Package | Supported |
|---------|-----------|
| core | Latest release |
| interceptors | Latest release |
| errors | Latest release |
| log | Latest release |
| tracing | Latest release |
| options | Latest release |
| grpcpool | Latest release |
| data-builder | Latest release |
| hystrixprometheus | Not supported (deprecated) |

## Reporting a Vulnerability

If you discover a security vulnerability in any ColdBrew package, please report it responsibly.

**Do NOT open a public GitHub issue for security vulnerabilities.**

Instead, email **coldbrew-security@googlegroups.com** with:

1. A description of the vulnerability
2. Steps to reproduce the issue
3. The affected package(s) and version(s)
4. Any potential impact you have identified

### What to Expect

- **Acknowledgment** within 72 hours of your report
- **Assessment** within 1 week — we will confirm whether the issue is a valid vulnerability
- **Fix timeline** communicated once the issue is confirmed
- **Credit** in the release notes (unless you prefer to remain anonymous)

### What Qualifies as a Security Issue

- Authentication or authorization bypasses
- Remote code execution
- Information disclosure (credentials, tokens, PII leakage)
- Denial of service vulnerabilities in the framework itself
- Dependency vulnerabilities that affect ColdBrew users

### What Does NOT Qualify

- Bugs that do not have a security impact (please open a regular GitHub issue)
- Security issues in applications built with ColdBrew (not in ColdBrew itself)
- Social engineering or phishing concerns

## Security Practices

ColdBrew follows these practices to maintain security:

- All packages are tested with Go's race detector (`go test -race`)
- Dependencies are monitored with `govulncheck`
- The "no breaking changes" policy ensures security patches do not disrupt production services
