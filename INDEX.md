# owasp-dashboard-static — File Index

## Main Files

### `index.html` (83 KB)
The entire interactive dashboard in a single HTML file. No dependencies, no server needed.

**Contains:**
- ✅ All HTML structure
- ✅ All CSS (Tailwind + custom styles)
- ✅ All JavaScript functionality
- ✅ All embedded data (OWASP vulnerabilities, user database, breach data)
- ✅ All 10 vulnerability demos
- ✅ All 4 interactive simulators
- ✅ All 30+ Claude Code prompts

**Size:** 83 KB (minifiable to ~55 KB)  
**Lines:** 1,113 lines of code

---

## Documentation Files

### `README.md` (3.7 KB)
Complete feature documentation and customization guide.

**Sections:**
- What's different from the original Flask version
- Quick start (local testing & GitHub Pages)
- Full feature list (all 10 vulnerabilities)
- Technical details
- Embedded data overview
- Customization instructions
- Limitations & security note

### `DEPLOY.md` (5.4 KB)
Deployment guide with 6 options.

**Deployment Methods:**
1. **GitHub Pages** (recommended, free)
2. **Netlify** (instant, free)
3. **Vercel** (instant, free)
4. **AWS S3 + CloudFront**
5. **Docker**
6. **Local development**

**Also includes:**
- Performance optimization
- Troubleshooting
- Custom domain setup
- Analytics integration
- CI/CD with GitHub Actions

### `QUICKSTART.md` (4.6 KB)
Fast 2-minute quick start guide.

**Covers:**
- Fastest way to run locally (30 seconds)
- What you'll see in the dashboard
- Try interactive demos (IDOR, password hashing, SQL injection, SSRF)
- Copy prompts for Claude Code
- File structure
- Browser support
- FAQ

### `.nojekyll` (empty file)
GitHub Pages configuration file. Tells GitHub not to process the site through Jekyll.

**Purpose:** Ensure the site deploys correctly to GitHub Pages.

---

## Related Files (in parent directory)

### `OWASP_DASHBOARD_VERSIONS.md`
Comparison guide between two versions:
- Original Flask version (`owasp-dashboard/app.py`)
- Static version (`owasp-dashboard-static/index.html`)

**Helps you choose:**
- When to use Flask version
- When to use static version
- Feature comparison table

---

## Quick Navigation

| What do you want to do? | Read this |
|---|---|
| See what's included | README.md |
| Get started fast | QUICKSTART.md |
| Deploy to live | DEPLOY.md |
| Choose Flask vs Static | ../OWASP_DASHBOARD_VERSIONS.md |
| Run everything | index.html |

---

## Testing Checklist

- [ ] Test locally: `python3 -m http.server 8000`
- [ ] Click each vulnerability (A01-A10)
- [ ] Run demo for each
- [ ] Try interactive simulators
- [ ] Copy Claude Code prompts
- [ ] Deploy to GitHub Pages
- [ ] Share the live link

---

## Key Features

### 10 OWASP Vulnerabilities
- **A01:** Broken Access Control (IDOR)
- **A02:** Cryptographic Failures
- **A03:** Injection (SQL)
- **A04:** Insecure Design
- **A05:** Security Misconfiguration
- **A06:** Vulnerable Components
- **A07:** Auth & Identification Failures
- **A08:** Software & Data Integrity Failures
- **A09:** Logging & Monitoring Failures
- **A10:** Server-Side Request Forgery

### 4 Interactive Simulators
- IDOR: Access any user by ID
- Password hashing: MD5 vs bcrypt
- SQL Injection: Test payloads
- SSRF: Fetch internal URLs

### Real-World Breaches
- LinkedIn 2012 (6.5M MD5 hashes)
- Equifax 2017 (148M SSNs)
- SolarWinds 2020 (18,000 orgs)
- Capital One 2019 (106M records)

### 30+ Claude Code Prompts
Every vulnerability includes 3 prompts:
- Security auditing
- Implementation guides
- Test case generation

---

## Development

All code is in `index.html`. To customize:

1. **Edit vulnerability data:** Search for `const OWASP = [`
2. **Change fake users:** Search for `const FAKE_USERS = {`
3. **Add prompts:** Find `prompts = [` in each demo function
4. **Update styling:** Edit the `<style>` section

No build tools needed. Edit, save, refresh browser.

---

## Browser Support

✅ Works in:
- Chrome 90+
- Firefox 88+
- Safari 14+
- Edge 90+

No IE11 support. Pure ES6 JavaScript.

---

## File Sizes

| File | Size | Purpose |
|------|------|---------|
| index.html | 83 KB | Everything |
| README.md | 3.7 KB | Documentation |
| DEPLOY.md | 5.4 KB | Deployment |
| QUICKSTART.md | 4.6 KB | Quick start |
| .nojekyll | 0 B | GitHub config |
| **Total** | **~100 KB** | **Production ready** |

---

## No Dependencies

❌ No Node.js  
❌ No Python backend  
❌ No build tools  
❌ No npm/pip  
❌ No database  
❌ No server

✅ Just open `index.html` in a browser!

---

## Questions?

- **How do I run it?** → See QUICKSTART.md
- **How do I deploy?** → See DEPLOY.md
- **What's inside?** → See README.md
- **Flask vs Static?** → See ../OWASP_DASHBOARD_VERSIONS.md

---

**Everything you need is here. Start with `python3 -m http.server 8000` and enjoy! 🚀**
