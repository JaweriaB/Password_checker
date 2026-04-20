#!/usr/bin/env python3
"""
Password Strength Checker - by Jaweria Batool
Checks password strength based on length, complexity, and common patterns.
Usage: python3 password_checker.py
"""

import re
import getpass


def check_strength(password):
    score = 0
    feedback = []

    # Length checks
    if len(password) >= 8:
        score += 1
    else:
        feedback.append("[-] Too short — use at least 8 characters")

    if len(password) >= 12:
        score += 1
    else:
        feedback.append("[~] Longer passwords are stronger — aim for 12+")

    # Character variety
    if re.search(r"[A-Z]", password):
        score += 1
    else:
        feedback.append("[-] Add uppercase letters (A-Z)")

    if re.search(r"[a-z]", password):
        score += 1
    else:
        feedback.append("[-] Add lowercase letters (a-z)")

    if re.search(r"[0-9]", password):
        score += 1
    else:
        feedback.append("[-] Add numbers (0-9)")

    if re.search(r"[!@#$%^&*()_+\-=\[\]{};':\"\\|,.<>\/?]", password):
        score += 1
    else:
        feedback.append("[-] Add special characters (!@#$% etc.)")

    # Common weak passwords
    common = ["password", "123456", "qwerty", "abc123", "letmein",
              "admin", "welcome", "monkey", "dragon", "master"]
    if password.lower() in common:
        score = 0
        feedback.append("[-] This is one of the most common passwords — change it!")

    # Repeated characters
    if re.search(r"(.)\1{2,}", password):
        score -= 1
        feedback.append("[~] Avoid repeated characters (aaa, 111)")

    # Determine strength level
    if score <= 1:
        strength = "VERY WEAK"
        bar = "[#         ]"
    elif score == 2:
        strength = "WEAK"
        bar = "[###       ]"
    elif score == 3:
        strength = "MEDIUM"
        bar = "[#####     ]"
    elif score == 4:
        strength = "STRONG"
        bar = "[#######   ]"
    else:
        strength = "VERY STRONG"
        bar = "[##########]"

    return strength, bar, score, feedback


def main():
    print("=" * 50)
    print("      PASSWORD STRENGTH CHECKER")
    print("      by Jaweria Batool")
    print("=" * 50)
    print("NOTE: Password is hidden as you type.\n")

    while True:
        password = getpass.getpass("Enter password to check: ")

        if not password:
            print("[-] No password entered.\n")
            continue

        strength, bar, score, feedback = check_strength(password)

        print("\n" + "=" * 50)
        print(f"  Strength : {strength}")
        print(f"  Score    : {score}/6")
        print(f"  Meter    : {bar}")
        print("=" * 50)

        if feedback:
            print("\nSuggestions:")
            for tip in feedback:
                print(f"  {tip}")

        print()
        again = input("Check another password? (y/n): ").strip().lower()
        if again != "y":
            break

    print("\n[+] Stay secure!")
    print("=" * 50)


if __name__ == "__main__":
    main()