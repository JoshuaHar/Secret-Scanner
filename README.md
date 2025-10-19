# Secret Scanner
A Python-based CLI tool that scans files or directories for common hardcoded secrets such as API keys, passwords, and tokens using regular expressions.

## How it works
The scanner follows these steps:
1. Accepts a file or directory as input.
2. Recursively scans through all text files.
3. Uses regular expressions to detect patterns that look like hardcoded secrets.
4. Outputs a report showing:
- The filename
- Line number
- The matched string
- A short context snippet

## Patterns Detected
The scanner looks for these common secret patterns:
1. AWS Access Key ID — AKIA[0-9A-Z]{16}
2. AWS Secret Access Key — A 40-character secret often labeled “aws” or “secret.”
3. Google API Key — AIza[0-9A-Za-z\-_]{35}
4. GitHub Token — gh[pousr]_[0-9A-Za-z]{36}
5. Slack Token — xox[baprs]-?[0-9A-Za-z-]{10,48}
6. Stripe Secret Key — sk_(live|test)_[0-9a-zA-Z]{24}
7. Private Key Block — Matches lines like -----BEGIN RSA PRIVATE KEY-----
8. High-Entropy Token — Long random base64-like strings (length ≥ 30).
9. Password Assignment — Variables like password = "..." or secret = "...".
