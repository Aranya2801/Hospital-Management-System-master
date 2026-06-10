# 🔐 Security Policy

## Supported Versions

| Version | Supported |
|---------|-----------|
| 2.x     | ✅ Active support |
| 1.x     | ⚠️ Security fixes only |
| < 1.0   | ❌ No longer supported |

---

## Reporting a Vulnerability

**Please do NOT report security vulnerabilities through public GitHub issues.**

### How to Report

1. **Email**: `security@medcore.in`
2. **Subject**: `[SECURITY] Brief description`
3. **Include**:
   - Type of vulnerability (XSS, SQL Injection, Auth bypass, etc.)
   - Step-by-step reproduction instructions
   - Potential impact assessment
   - Suggested fix (optional but appreciated)

### Response Timeline

| Stage | Target Time |
|-------|------------|
| Acknowledgement | Within 24 hours |
| Initial assessment | Within 72 hours |
| Status update | Weekly |
| Patch release | Within 30 days for critical |

---

## Security Controls

### Authentication & Authorization
- JWT with short expiry (24h) + refresh token rotation
- bcrypt password hashing (cost factor 12)
- Account lockout after 5 failed attempts (30 min)
- Role-based access control (8 roles)
- Token blacklisting on logout

### Data Protection (HIPAA)
- AES-256 encryption for PII at rest
- TLS 1.3 in transit
- Soft delete only — patient data never permanently erased
- Full audit log of all data access
- Aadhar numbers masked in API responses

### API Security
- Rate limiting (500 req/15min global, 20/15min auth)
- Input validation with Joi schemas
- SQL injection prevention via Sequelize parameterized queries
- XSS prevention via Helmet.js + CSP headers
- CORS restricted to known origins

### Infrastructure
- Non-root Docker containers
- Secrets via environment variables (never hardcoded)
- Dependency audit in CI/CD pipeline
- Regular npm audit checks

---

## Responsible Disclosure

We follow responsible disclosure practices. Researchers who report valid vulnerabilities will be:
- Credited in our CHANGELOG (with permission)
- Notified when the fix is released

We ask that you:
- Give us reasonable time to fix before public disclosure
- Do not access or modify real patient data
- Do not perform denial-of-service attacks
- Act in good faith

Thank you for helping keep MedCore HMS secure! 🙏
