# OWASP Top 10 — Interactive Demo Dashboard (Static/GitHub Pages Version)

A **zero-backend**, **GitHub Pages compatible** version of the interactive OWASP Top 10 security dashboard.

## What's Different from the Original

| Feature | Flask Original | Static Version |
|---------|---|---|
| **Backend** | Flask + Python | ❌ None |
| **Database** | Required | ❌ No database |
| **Deployment** | Server needed | ✅ GitHub Pages |
| **File Size** | Large | ✅ 83 KB (single HTML) |
| **Dependencies** | Many | ✅ None |
| **Speed** | Loads from server | ✅ Instant (client-side) |

## Quick Start

### Local Testing
```bash
cd owasp-dashboard-static
# Option 1: Python simple server
python3 -m http.server 8000

# Option 2: Live server (VS Code extension)
# Right-click index.html → Open with Live Server
```

Then open: **http://localhost:8000**

### Deploy to GitHub Pages

1. **Copy `index.html` to your repo's `docs/` folder:**
   ```bash
   mkdir -p docs
   cp index.html docs/
   ```

2. **Enable GitHub Pages in repo settings:**
   - Go to Settings → Pages
   - Select `docs/` as source
   - Save

3. **Access at:** `https://YOUR_USERNAME.github.io/YOUR_REPO/docs/`

## Features

✅ **10 OWASP Top 10 Vulnerabilities**
- A01: Broken Access Control (IDOR demo)
- A02: Cryptographic Failures (password cracking)
- A03: Injection (SQL injection simulator)
- A04: Insecure Design (design flaws)
- A05: Security Misconfiguration (config audit)
- A06: Vulnerable Components (dependency scan)
- A07: Auth Failures (credential stuffing)
- A08: Integrity Failures (supply chain attack)
- A09: Logging Failures (good vs bad logs)
- A10: SSRF (internal network access)

✅ **Interactive Simulators**
- IDOR: Access any user's data by changing ID
- Password Hashing: See how MD5 vs bcrypt works
- SQL Injection: Test injection payloads
- SSRF: Try to fetch internal URLs

✅ **Real-World Breaches**
- LinkedIn 2012 (password hashing)
- Equifax 2017 (unpatched library)
- Capital One 2019 (SSRF + cloud misconfiguration)
- SolarWinds 2020 (supply chain attack)

✅ **Claude Code Prompts**
Every demo includes 3 copy-paste prompts for Claude Code:
- Security auditing prompts
- Implementation guides
- Test case generation

## Technical Details

- **Framework:** Vanilla JavaScript (no build tools)
- **Styling:** Tailwind CSS (CDN)
- **Size:** 83 KB uncompressed (minifiable to ~50 KB)
- **Browser Support:** All modern browsers (ES6)
- **No external APIs:** Everything embedded in the HTML

## Embedded Data

All data is hardcoded in the HTML:
- OWASP vulnerability metadata
- Fake user database (for IDOR demo)
- Password hashes (for crypto demo)
- Package vulnerabilities (for dependency scan)
- Breach timelines and statistics

This eliminates the need for any backend or API calls.

## Customization

To add your own data:

1. **Edit OWASP list:** Line ~170 in `<script>`
2. **Change fake users:** Update `FAKE_USERS` object
3. **Modify prompts:** Edit the `prompts` array in each demo runner
4. **Update styling:** Edit the `<style>` section

## Limitations

- **No real attack execution** (all simulations are client-side)
- **No persistent state** (data resets on page refresh)
- **No real database queries** (uses hardcoded demo data)
- **No authentication** (all data is public)

## Security Note

This is **educational only**. It demonstrates vulnerabilities using safe, client-side simulations. It should never be used for actual penetration testing or real attacks.

## License

Same as the original OWASP dashboard project.

---

**Deploy to GitHub Pages in seconds. No server needed. Perfect for:**
- Teaching security in schools
- Onboarding new engineers
- Security awareness training
- Open-source documentation
