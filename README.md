# Kerberos Authentication & X.509 Certificate Generation
**Amirkabir University of Technology | Fall 2024**  
**Course: Fundamentals of Information Security**

## Overview
Two practical implementations covering key management concepts: a Kerberos-based client-server authentication system and X.509 public-key certificate generation.

## Part 1 — Kerberos Authentication (Flask + requests-kerberos)

A simulated Kerberos authentication flow built with Python and Flask.

**Components:**
- **KDC** (Key Distribution Center): user registration & authentication
- **TGS** (Ticket Granting Server): issues and validates service tickets
- **Client**: makes Kerberos-authenticated HTTP requests via `requests-kerberos`

**Authentication Flow:**
1. Register user → `POST /register`
2. Authenticate → `GET /authenticate` → receive ticket + session key
3. Verify ticket → `GET /verify_ticket`
4. Issue service ticket → `GET /issue_service_ticket`
5. Verify service ticket → `GET /verify_service_ticket`

## Part 2 — X.509 Certificate Generation (Bonus)

Generates a self-signed X.509 certificate using Python's `cryptography` library, covering:
- Subject Alternative Names (DNS + IP)
- RSA private key generation (2048-bit, PEM)
- Certificate validity period
- Basic constraints

## Structure
```
kerberos_request/
├── kerberos_service.py   # Flask app (KDC + TGS + Service)
└── kerberos-request.py   # Kerberos-authenticated client
x509_certificate.ipynb    # X.509 certificate generation
requirements.txt
```

## Setup
```bash
pip install -r requirements.txt

# Terminal 1 — run Flask server
cd kerberos_request
python kerberos_service.py

# Terminal 2 — run client
python kerberos-request.py
```
