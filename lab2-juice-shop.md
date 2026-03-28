# Lab 2: OWASP Juice Shop

## Overview

OWASP Juice Shop is an intentionally vulnerable web application designed for security training. This lab focused on practical exploitation of common web vulnerabilities such as SQL injection, broken access control, information disclosure, and cross-site scripting.

## Completed Challenges

### 1. Find the Hidden Scoreboard

Using browser developer tools and the `main.js` source file, the hidden `/score-board` path was discovered. Visiting that route completed the challenge.

**Impact:** hidden internal routes were exposed, increasing the risk of discovery of other administrative or sensitive paths.

### 2. Create a New Admin User

A registration request was intercepted in Burp Suite and modified before being replayed in Repeater. By adding a `role` field with the value `admin`, a normal account was elevated.

**Impact:** privilege escalation exposed sensitive administration functionality.

### 3. Find the Admin Page

After gaining elevated access, the administrative interface could be located and used.

**Impact:** administrative access increases risk to confidentiality, integrity, and availability.

### 4. View Another User's Basket

By changing the basket identifier in the browser session, another user's basket contents became visible.

**Impact:** broken access control exposed another customer's order data.

### 5. Login as Admin

A SQL injection payload was used in the login request to bypass authentication and obtain admin access.

**Impact:** full account compromise and privileged access.

### 6. Trigger an Unhandled Error

The application exposed internal details when a request was not handled gracefully.

**Impact:** information disclosure revealed development and framework details that could help an attacker.

### 7. Login as Bender

A SQL injection payload was used to authenticate as another user account.

**Impact:** complete account takeover.

### 8. Change Bender's Password

By intercepting and modifying the password change request, the current-password field could be removed and the password changed.

**Impact:** permanent or semi-permanent loss of control for the victim user.

### 9. DOM XSS

A client-side payload was inserted into the search function, causing script execution.

**Impact:** session theft, malicious content injection, and user redirection become possible.

### 10. Steal User Credentials

A union-based SQL injection was used to determine the correct column count and extract user identifiers, email addresses, and password hashes from the database.

**Impact:** major confidentiality breach affecting all users.

## Tools Used

- Browser developer tools
- Burp Suite Repeater
- SQL injection payloads
- Stored and DOM XSS payloads

## Reflection

This lab provided practical insight into how multiple vulnerability classes work in real applications. The most challenging task was extracting user credentials because it required iterative testing and careful interpretation of error messages.

It also demonstrated how information disclosure and SQL injection often reinforce one another.

## Strengths and Weaknesses

### Strengths

- Excellent for hands-on practice
- Clear challenge structure and feedback
- Useful for learning how web vulnerabilities connect together

### Weaknesses

- Intentionally unrealistic in how many severe issues exist at once
- Should be treated as a training platform, not a realistic secure-by-default application model

## Add screenshots

```md
![Challenge completed](assets/lab2-challenge-completed.png)
```
