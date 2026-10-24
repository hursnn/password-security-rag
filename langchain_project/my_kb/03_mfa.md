# Multi-Factor Authentication (MFA)

## What Is MFA?

Multi-factor authentication is a security method that requires
users to provide two or more different types of authentication
factors before accessing an account.

MFA provides an additional layer of protection beyond a password.

## Three Authentication Factor Categories

Authentication factors are generally divided into three categories:

1. Something you know, such as a password or PIN.
2. Something you have, such as a security key or authenticator device.
3. Something you are, such as a fingerprint or facial recognition.

Using two passwords does not qualify as multi-factor authentication
because both belong to the same factor category.

## Common MFA Methods

Authenticator applications can generate time-based one-time
passwords (TOTP) that expire after a short period.

Hardware security keys can use FIDO2 or WebAuthn authentication
to provide phishing-resistant protection.

SMS verification codes are widely available but can be vulnerable
to SIM-swapping attacks and phishing.

## Why MFA Matters

If an attacker steals a user's password, MFA can prevent the
attacker from signing in without the additional authentication
factor.

However, not all MFA methods provide equal protection.

## MFA Limitations

Attackers may trick users into revealing one-time codes through
phishing websites.

Repeated authentication prompts may lead to MFA fatigue,
where a user accidentally approves a fraudulent login attempt.

Phishing-resistant authentication methods are preferable
for accounts containing sensitive information.

## MFA Best Practices

Enable MFA for email, financial, and other important accounts.
Prefer passkeys or hardware security keys when supported.
Never share verification codes with another person.
Do not approve unexpected authentication requests.
Store backup recovery codes securely.
