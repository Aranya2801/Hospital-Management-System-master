# 🤝 Contributing to MedCore HMS

Thank you for your interest in contributing! This document explains how to get involved effectively.

---

## 📋 Table of Contents
- [Code of Conduct](#code-of-conduct)
- [Getting Started](#getting-started)
- [Development Workflow](#development-workflow)
- [Commit Convention](#commit-convention)
- [Pull Request Process](#pull-request-process)
- [Coding Standards](#coding-standards)
- [Testing Requirements](#testing-requirements)
- [Reporting Bugs](#reporting-bugs)

---

## Code of Conduct

All contributors are expected to uphold a respectful, inclusive, and harassment-free environment. We follow the [Contributor Covenant v2.1](https://www.contributor-covenant.org/version/2/1/code_of_conduct/).

---

## Getting Started

1. **Fork** the repository on GitHub
2. **Clone** your fork locally:
   ```bash
   git clone https://github.com/YOUR_USERNAME/Hospital-Management-System-master.git
   cd Hospital-Management-System-master
   ```
3. **Add upstream** remote:
   ```bash
   git remote add upstream https://github.com/Aranya2801/Hospital-Management-System-master.git
   ```
4. **Install dependencies** for both backend and frontend:
   ```bash
   cd backend && npm install
   cd ../frontend && npm install
   ```
5. **Set up environment**:
   ```bash
   cp .env.example .env
   # Fill in local credentials
   ```

---

## Development Workflow

```bash
# 1. Sync with upstream before starting work
git fetch upstream
git checkout main
git merge upstream/main

# 2. Create a feature branch
git checkout -b feature/your-feature-name
# or for bug fixes:
git checkout -b fix/describe-the-bug

# 3. Make your changes
# Write code, add tests, update docs

# 4. Run tests before committing
cd backend && npm test
cd ../frontend && npm test

# 5. Commit with conventional commits
git add .
git commit -m "feat(billing): add GST calculation for lab items"

# 6. Push to your fork
git push origin feature/your-feature-name

# 7. Open a Pull Request on GitHub
```

---

## Commit Convention

We use **Conventional Commits** for automated changelogs and versioning.

```
<type>(<scope>): <short description>

[optional body]

[optional footer]
```

### Types
| Type | When to use |
|------|-------------|
| `feat` | New feature |
| `fix` | Bug fix |
| `docs` | Documentation only |
| `style` | Formatting, no logic change |
| `refactor` | Code restructure, no feature/fix |
| `test` | Adding or fixing tests |
| `chore` | Build, CI, dependency updates |
| `perf` | Performance improvement |
| `security` | Security patch |

### Scopes
`auth`, `patients`, `doctors`, `appointments`, `billing`, `lab`, `pharmacy`, `beds`, `analytics`, `ui`, `api`, `db`, `docker`, `ci`

### Examples
```bash
feat(appointments): add AI-powered no-show risk score display
fix(billing): correct GST rounding for partial payments
docs(api): add OpenAPI spec for lab orders endpoint
test(patients): add integration tests for duplicate Aadhar detection
perf(analytics): cache dashboard KPIs with Redis TTL
security(auth): enforce bcrypt rounds=12 on password reset
```

---

## Pull Request Process

1. **Ensure your branch is up-to-date** with `main`
2. **Fill out the PR template** completely
3. **Link related issues** using `Closes #123`
4. **All CI checks must pass** — tests, lint, build
5. **Request review** from at least one maintainer
6. **Address all review comments** before merging
7. PRs are squash-merged to keep history clean

### PR Title Format
Same as commit messages: `feat(scope): description`

---

## Coding Standards

### JavaScript / Node.js
- **ES2022+** syntax, strict mode (`'use strict'`)
- **ESLint** config in `.eslintrc.js` — run `npm run lint`
- **Async/await** preferred over `.then()` chains
- Always use `try/catch` in controllers — pass error to `next(error)`
- Use `ApiError` for all thrown HTTP errors
- No `console.log` in production code — use `logger`

### React / Frontend
- **Functional components** with hooks only
- **Redux Toolkit** for global state — no prop drilling more than 2 levels
- Use `api.js` Axios instance for all HTTP calls (never raw fetch/axios)
- Component filenames in **PascalCase**: `PatientDetail.jsx`
- Utility filenames in **camelCase**: `formatters.js`
- One component per file

### CSS
- **Tailwind CSS** utility classes only
- No custom CSS unless absolutely necessary
- Responsive-first: mobile → tablet → desktop

### Database
- All schema changes via **migration files** in `database/migrations/`
- Use UUIDs for all primary keys
- Never hard-delete patient data (soft delete via `deleted_at`)
- Always add indexes for foreign keys and frequently queried columns

---

## Testing Requirements

All PRs **must** include tests for new features and bug fixes.

### Backend
```bash
# Unit tests
npm test

# Coverage (must be ≥ 80%)
npm run test:coverage

# Integration tests
npm run test:integration
```

### Frontend
```bash
npm test -- --coverage --watchAll=false
```

### What to test
- ✅ Happy path (expected inputs)
- ✅ Edge cases (empty arrays, null values, max lengths)
- ✅ Error cases (invalid auth, missing fields, DB errors)
- ✅ Auth guard — protected routes reject unauthenticated requests

---

## Reporting Bugs

Use the **Bug Report** issue template and include:

1. **Steps to reproduce** — be specific
2. **Expected behavior**
3. **Actual behavior**
4. **Environment** — Node version, OS, browser
5. **Logs / Screenshots** if applicable
6. **Patient data** — NEVER include real patient data in issues

---

## Security Vulnerabilities

**Do NOT open a public issue for security vulnerabilities.**  
Email us at: `security@medcore.in` or see [SECURITY.md](SECURITY.md)

---

## Questions?

Open a [Discussion](https://github.com/Aranya2801/Hospital-Management-System-master/discussions) — we're happy to help!
