# 🔐 Penetration Testing Report – Booking System Phase 1 (Ver2)

**Date:** April 18, 2025  
**Tested Version:** Phase 1 / Ver2  
**Tested URL:** http://localhost:8000  
**Testing Tools:**  
- ZAP 2.16.0  
- Manual Browser Testing  
- curl & Developer Tools

---

## ✅ Fixed Issues from Previous Version (Ver1)

| Issue                                   | Status     | Notes                                      |
|----------------------------------------|------------|--------------------------------------------|
| SQL Injection                          | ✅ Fixed   | Test payload `' OR 1=1 --` no longer works |
| Missing CSP Header                     | ✅ Fixed   | Header now present                         |
| Missing Anti-clickjacking Header       | ✅ Fixed   | X-Frame-Options added                      |
| X-Content-Type-Options Header Missing  | ✅ Fixed   | Header now present                         |
| Error Disclosure on /register          | ✅ Fixed   | No visible error stack or traceback        |

---

## ❗ New Vulnerabilities Found (ZAP Ver2)

| Risk Level | Issue                        | Location                    | Confidence |
|------------|------------------------------|-----------------------------|------------|
| Medium     | Absence of Anti-CSRF Tokens  | `GET /register`             | Low        |

**Details:**  
ZAP identified that the registration page does not use CSRF tokens to protect against Cross-Site Request Forgery attacks.

**Recommendation:**  
Implement CSRF protection using per-request tokens stored in sessions or cookies, and validated on form submission.

More info:  
- https://cheatsheetseries.owasp.org/cheatsheets/Cross-Site_Request_Forgery_Prevention_Cheat_Sheet.html

---

## ⚠️ Not Yet Retested

| Item                         | Status      | Notes                       |
|------------------------------|-------------|-----------------------------|
| Weak Password Policy         | ❔ Not tested | Needs further validation    |
| Long Input Handling          | ❔ Not tested | Buffer overflow not verified |
| Special Character Handling   | ❔ Not tested | Manual testing recommended  |

---
