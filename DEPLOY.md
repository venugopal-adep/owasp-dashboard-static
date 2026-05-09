# Deployment Guide — OWASP Dashboard Static Version

## Option 1: GitHub Pages (Recommended)

### Step 1: Prepare Your Repository
```bash
# If using a new repo
git init
git add .
git commit -m "Add OWASP dashboard static version"
```

### Step 2: Create `docs/` Folder
```bash
mkdir -p docs
cp index.html docs/
cp .nojekyll docs/
cp README.md docs/
```

### Step 3: Enable GitHub Pages
1. Go to your GitHub repo → **Settings**
2. Scroll to **Pages** section
3. Select **Deploy from a branch**
4. Choose branch: `main` (or `master`)
5. Select folder: `docs/`
6. Click **Save**

### Step 4: Access Your Dashboard
Your dashboard will be live at:
```
https://YOUR_USERNAME.github.io/YOUR_REPO/
```

Or if using a custom domain:
```
https://your-custom-domain.com/
```

---

## Option 2: Netlify

### Step 1: Push to GitHub
```bash
git push origin main
```

### Step 2: Connect to Netlify
1. Go to [netlify.com](https://netlify.com) → **Sign up with GitHub**
2. Click **New site from Git**
3. Select your repository
4. **Build settings:**
   - Build command: (leave empty)
   - Publish directory: `.` (root folder)
5. Click **Deploy site**

Your site will be live in seconds.

---

## Option 3: Local Development

### Using Python
```bash
cd owasp-dashboard-static
python3 -m http.server 8000
# Open http://localhost:8000
```

### Using Node.js
```bash
npm install -g http-server
cd owasp-dashboard-static
http-server
```

### Using VS Code Live Server
1. Install [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) extension
2. Right-click `index.html`
3. Select **Open with Live Server**
4. Auto-opens in browser

---

## Option 4: AWS S3 + CloudFront

### Step 1: Upload to S3
```bash
aws s3 cp index.html s3://your-bucket-name/index.html
aws s3 cp README.md s3://your-bucket-name/README.md
```

### Step 2: Make Public
```bash
aws s3api put-object-acl --bucket your-bucket-name --key index.html --acl public-read
```

### Step 3: Set Up CloudFront (Optional)
1. Create CloudFront distribution pointing to S3 bucket
2. Enable HTTPS
3. Access via CloudFront domain

---

## Option 5: Docker

### Create Dockerfile
```dockerfile
FROM nginx:alpine
COPY owasp-dashboard-static /usr/share/nginx/html
EXPOSE 80
```

### Build & Run
```bash
docker build -t owasp-dashboard .
docker run -p 8080:80 owasp-dashboard
# Open http://localhost:8080
```

### Push to Docker Hub
```bash
docker tag owasp-dashboard YOUR_USERNAME/owasp-dashboard
docker push YOUR_USERNAME/owasp-dashboard
```

---

## Option 6: Vercel

### Step 1: Install Vercel CLI
```bash
npm install -g vercel
```

### Step 2: Deploy
```bash
cd owasp-dashboard-static
vercel
```

### Step 3: Follow Prompts
- Confirm project name
- Vercel will auto-detect static files
- Your site is live!

---

## Performance Optimization

### Minify HTML
```bash
npm install -g html-minifier-terser
html-minifier-terser --collapse-whitespace --remove-comments index.html -o index.min.html
```

Expected result: **83 KB → ~55 KB**

### Enable Compression
Most hosting providers (GitHub Pages, Netlify, Vercel) automatically gzip HTML.

### Cache Headers
Set long cache expiration for static content:
```nginx
# nginx.conf
location / {
    expires 1y;
    add_header Cache-Control "public, immutable";
}
```

---

## Troubleshooting

### "Page not found" on GitHub Pages
- Ensure `.nojekyll` file exists in deployment folder
- Check that `index.html` is in the correct folder
- Wait 2-3 minutes for GitHub to rebuild

### CSS/JS Not Loading
- Open browser DevTools (F12)
- Check **Network** tab for failed requests
- Ensure Tailwind CDN URL is accessible

### Interactive Features Not Working
- Check browser console (F12 → Console)
- Look for JavaScript errors
- Try a different browser

---

## Custom Domain

### With GitHub Pages
1. Create `CNAME` file with your domain
2. Update DNS records to point to GitHub Pages
3. GitHub will auto-verify and enable HTTPS

### With Netlify
1. Go to **Site settings** → **Domain management**
2. Add custom domain
3. Update DNS records
4. Netlify auto-provisions SSL certificate

---

## Monitoring & Analytics

### Add Google Analytics
Add to `<head>` section:
```html
<script async src="https://www.googletagmanager.com/gtag/js?id=YOUR_GA_ID"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());
  gtag('config', 'YOUR_GA_ID');
</script>
```

### Track Demo Usage
```javascript
// Add to runDemo() function
gtag('event', 'demo_run', {
  vulnerability_id: currentId,
  timestamp: new Date().toISOString()
});
```

---

## Version Control

### Keep Original & Static in Sync
```bash
# When you update owasp-dashboard/ (Flask version)
# Remember to update owasp-dashboard-static/ with new data

# Useful git command to track both:
git log --oneline -- owasp-dashboard/ owasp-dashboard-static/
```

---

## CI/CD Integration

### GitHub Actions (Auto-Deploy on Push)
Create `.github/workflows/deploy.yml`:
```yaml
name: Deploy
on: [push]
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Deploy to GitHub Pages
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./owasp-dashboard-static
```

Then on every push, the dashboard auto-deploys!

---

## Support

- **Issue:** File a bug report on GitHub
- **Question:** Start a discussion
- **Suggestion:** Submit a pull request

Happy deploying! 🚀
