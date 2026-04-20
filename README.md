# Password Strength Checker

A security-focused Python utility that evaluates password entropy, detects common weak patterns, and implements secure masked input.

---

## Security Features

| Feature | Security Reasoning |
|---|---|
| Masked input via `getpass` | Prevents shoulder surfing � password never appears on screen |
| Common password blacklist | Blocks credentials found in known breach dictionaries |
| Repeated character detection | Flags low-entropy patterns that reduce effective key space |
| Complexity scoring across 6 criteria | Enforces character variety to resist brute-force and dictionary attacks |
| Actionable feedback | Guides users toward stronger credentials without revealing the password |

---

## Scoring Logic

Password strength is calculated by evaluating multiple complexity factors independently:

| Criteria | Points |
|---|---|
| At least 8 characters | +1 |
| At least 12 characters | +1 |
| Contains uppercase (A-Z) | +1 |
| Contains lowercase (a-z) | +1 |
| Contains numbers (0-9) | +1 |
| Contains special characters (!@#$ etc.) | +1 |
| Matches common password list | Score = 0 |
| Repeated characters detected (aaa, 111) | -1 |

Length and complexity are scored separately � a long but simple password will not score the same as a short but complex one.

---

## Usage

```bash
python3 password_checker.py
```

No external dependencies. Runs entirely on Python 3 standard library.

---

## Example Output

```
==================================================
      PASSWORD STRENGTH CHECKER
      by Jaweria Batool
==================================================
NOTE: Password is hidden as you type.

Enter password to check:

==================================================
  Strength : VERY STRONG
  Score    : 6/6
  Meter    : [##########]
==================================================

Suggestions:
  (none � all criteria met)
```

---

## � Requirements

- Python 3.x
- No external libraries � standard library only (`re`, `getpass`)

---

## Ethical Notice

This tool is for **educational and personal use only**.  
Passwords entered are never stored, logged, or transmitted.  
Do not use this tool to evaluate or handle other people's credentials without their explicit consent.

---

## � About

Built by **Jaweria Batool** � self-taught Python developer on Ubuntu Linux.  
Focused on cybersecurity tooling and security-aware software design.
