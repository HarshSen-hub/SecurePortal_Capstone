 # 🔐 SecurePortal – Secure Student Portal

A secure student registration and login portal built using **Python, Flask, and SQLite**. The project demonstrates secure coding practices, authentication, authorization, database security, session management, multi-factor authentication, and security auditing.

> **Project Type:** Academic Capstone Project  
> **Domain:** Secure Coding & Vulnerability Assessment  
> **Framework:** Flask  
> **Database:** SQLite

---

## 📌 Table of Contents

- [Overview](#-overview)
- [Features](#-features)
- [Technology Stack](#-technology-stack)
- [Project Structure](#-project-structure)
- [Installation and Setup](#-installation-and-setup)
- [Administrator Setup](#-administrator-setup)
- [Two-Factor Authentication](#-two-factor-authentication)
- [Security Implementation](#-security-implementation)
- [Database Structure](#-database-structure)
- [Testing](#-testing)
- [Limitations and Future Improvements](#-limitations-and-future-improvements)
- [Disclaimer](#-disclaimer)

---

## 🚀 Overview

SecurePortal is a web-based student portal designed to demonstrate how common web application vulnerabilities can be prevented through secure coding practices.

It provides separate access for students and administrators, with security mechanisms implemented across authentication, authorization, database operations, session handling, and user activity monitoring.

The application focuses on protecting user credentials, preventing unauthorized access, reducing common web vulnerabilities, and maintaining an audit trail of important security events.

### How It Works

1. Students register using the registration page.
2. User information is validated by the Flask backend.
3. Passwords are securely hashed before being stored in the SQLite database.
4. Registered users authenticate through the login system.
5. The application checks user roles and grants access to authorized pages.
6. Additional security mechanisms protect sessions and sensitive operations.
7. Administrators can manage student accounts and monitor security events.

---

## ✨ Features

### 👨‍🎓 Student Features
- Student registration and login.
- Secure password storage.
- Personal dashboard and profile management.
- Password reset functionality.
- Two-factor authentication using an authenticator app.
- Account security settings.
- Secure logout and session management.

### 🛡️ Administrator Features
- Separate administrator authentication.
- Role-based access control.
- View and search student records.
- Manage and delete student accounts.
- Monitor recent security events.
- View failed login and rate-limit activity.
- Export security audit logs as CSV.

### 🔒 Security Features
- Password hashing using Werkzeug.
- SQL injection prevention.
- Cross-Site Scripting (XSS) protection.
- Cross-Site Request Forgery (CSRF) protection.
- Brute-force login protection.
- Secure session management.
- Time-based One-Time Password (TOTP) authentication.
- Secure password reset tokens.
- Security audit logging.
- HTTP security headers.

---

## 🧰 Technology Stack

| Technology | Purpose |
|---|---|
| Python | Backend programming |
| Flask | Web application framework |
| SQLite | Database management |
| HTML5 | Web page structure |
| CSS3 | Styling and layout |
| JavaScript | Frontend interactions |
| Flask-WTF | CSRF protection |
| Werkzeug | Password hashing and security utilities |
| PyOTP | TOTP-based two-factor authentication |
| ItsDangerous | Secure token-related utilities |

---

## 📁 Project Structure

```text
SecurePortal_Upgraded/
│
├── app.py
│   └── Main Flask application, routes and security controls
│
├── config.py
│   └── Application configuration and secret key management
│
├── database.py
│   └── SQLite database, tables and database operations
│
├── requirements.txt
│   └── Python dependencies
│
├── .env.example
│   └── Example environment configuration
│
├── .gitignore
│   └── Files excluded from Git
│
├── test_security.py
│   └── Main automated security test suite
│
├── test_security_extended.py
│   └── Additional security tests
│
├── SECURITY_TEST_PLAN.md
│   └── Security testing documentation
│
├── templates/
│   ├── base.html
│   ├── index.html
│   ├── register.html
│   ├── login.html
│   ├── dashboard.html
│   ├── admin.html
│   ├── security.html
│   ├── verify_mfa.html
│   ├── forgot_password.html
│   ├── reset_password.html
│   └── error.html
│
├── static/
│   ├── css/
│   │   └── style.css
│   ├── js/
│   │   └── script.js
│   └── images/
│
└── instance/
    └── Application database and generated secret-key data
```

---

## ⚙️ Installation and Setup

Follow these steps to run SecurePortal locally.

### 1. Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/SecurePortal.git
```

Navigate into the project directory:

```bash
cd SecurePortal
```

### 2. Create a Virtual Environment

**macOS / Linux**

```bash
python3 -m venv .venv
source .venv/bin/activate
```

**Windows**

```powershell
py -m venv .venv
.venv\Scripts\activate
```

### 3. Install Dependencies

```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

### 4. Run the Application

```bash
python app.py
```

### 5. Open the Application

Visit the following address in your browser:

```text
http://127.0.0.1:5000
```

The application automatically creates the required database when it starts.

---

## 👨‍💼 Administrator Setup

An administrator account must be created through the Flask command line.

Run this command from the project directory:

```bash
python -m flask --app app create-admin
```

Follow the prompts to enter the administrator's name, email, and password.

After creating the account:

1. Open the application in your browser.
2. Navigate to the login page.
3. Enter the administrator credentials.
4. Access the administrator dashboard.

Administrator registration is not available through the public student registration page.

---

## 🔑 Two-Factor Authentication

SecurePortal supports TOTP-based two-factor authentication.

To enable it:

1. Log in to a student account.
2. Open **Dashboard → Security**.
3. Select the authenticator setup option.
4. Add the displayed setup key to a compatible authenticator application.
5. Enter the generated six-digit verification code.
6. Complete the MFA setup.

After activation, the user must provide both their password and authenticator code during login.

---

## 🔒 Security Implementation

Security is a core component of SecurePortal. The following mechanisms are implemented to protect the application.

| Security Mechanism | Implementation |
|---|---|
| Password Security | Werkzeug password hashing using scrypt by default |
| SQL Injection Prevention | Parameterized SQL queries |
| XSS Prevention | Jinja2 autoescaping, input validation and CSP |
| CSRF Protection | Flask-WTF CSRF tokens |
| Brute-Force Protection | Login attempt tracking and request throttling |
| Authentication | Secure user login and password verification |
| Authorization | Role-based access control for students and administrators |
| Session Security | Secure cookie settings and idle session expiration |
| Multi-Factor Authentication | TOTP-based verification |
| Password Recovery | Random, time-limited, single-use reset tokens |
| Audit Logging | Records important account and security events |
| Security Headers | CSP, X-Frame-Options, X-Content-Type-Options and other headers |

### Important Security Details

**1. Password Hashing**

Passwords are never stored as plain text. Werkzeug generates password hashes before they are saved in the database.

**2. SQL Injection Prevention**

Parameterized SQL queries ensure that user input is treated as data rather than executable SQL commands.

**3. XSS Protection**

Jinja2 automatic escaping and Content Security Policy help prevent malicious scripts from executing through user-controlled content.

**4. CSRF Protection**

CSRF tokens are validated on POST requests to prevent unauthorized requests made through a user's authenticated session.

**5. Brute-Force Protection**

Failed login attempts are tracked using email and IP information. The application applies a limit of five failed attempts within a 15-minute window.

**6. Session Management**

The application uses signed Flask sessions, HttpOnly and SameSite cookie settings, session clearing during login/logout, and a 30-minute idle timeout.

**7. Password Reset Security**

Password reset uses random tokens whose SHA-256 hashes are stored in the database. Tokens expire after 20 minutes and can only be used once.

**8. Security Audit Trail**

Important events such as successful and failed logins, registration, logout, password resets, MFA changes, and account updates are recorded for administrator monitoring.

---

## 🗄️ Database Structure

SecurePortal uses SQLite for storing application data.

The database is created automatically inside:

```text
instance/students.db
```

### Main Database Tables

| Table | Purpose |
|---|---|
| `students` | Stores student and administrator account information |
| `login_attempts` | Tracks failed login attempts |
| `audit_logs` | Stores important security and account activity |
| `password_reset_tokens` | Stores hashed password reset tokens and their expiry information |

The database also supports session-version tracking to invalidate existing sessions after password resets.

---

## 🧪 Testing

SecurePortal includes automated security testing files.

Run the main security test suite:

```bash
python test_security.py
```

Run the extended security tests:

```bash
python -m unittest -v test_security_extended.py
```

### Security Testing Scenarios

The application can be tested against the following scenarios:

- Attempt SQL injection through login inputs.
- Test whether malicious HTML or JavaScript executes.
- Submit requests without valid CSRF tokens.
- Perform repeated failed login attempts.
- Attempt administrator access using a student account.
- Test session expiration.
- Verify MFA authentication.
- Test expired and previously used password reset tokens.
- Verify security audit events and CSV export.

Refer to **[SECURITY_TEST_PLAN.md](SECURITY_TEST_PLAN.md)** for additional testing details.

> Run the test suites in your own environment and report the actual results. Do not assume tests have passed without executing them.

---

## 🚧 Limitations and Future Improvements

Although SecurePortal demonstrates several important security practices, some improvements are required before production deployment.

| Current Limitation | Future Improvement |
|---|---|
| SQLite database | Use PostgreSQL or another production database |
| MFA secrets stored without encryption at rest | Implement encryption for stored MFA secrets |
| No MFA recovery codes | Add secure backup and recovery codes |
| Admin MFA is not mandatory | Enforce MFA for administrator accounts |
| No email verification | Add email ownership verification |
| Application-level rate limiting | Use centralized rate limiting such as Redis |
| SMTP required for email delivery | Configure a reliable email service |
| No defined audit-log retention policy | Implement log retention and access policies |

Additional improvements could include security monitoring alerts, dependency scanning, password breach screening, and deployment hardening.

---

## 📌 Disclaimer

SecurePortal is an educational academic project developed to demonstrate secure web application development and common security controls.

It is **not a production-certified authentication system**. Before deploying it publicly, additional security reviews, HTTPS configuration, secure secret management, production database setup, monitoring, backups, and deployment hardening are necessary.

---

## 👥 Project Contributors

Developed as a collaborative academic project by a team of six members.

**Project:** SecurePortal – Secure Student Portal  
**Focus:** Secure Coding and Vulnerability Prevention

---

⭐ If you find this project useful, consider giving the repository a star!
