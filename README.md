# Cover Whale - Master Prompt Engineering Guide

Protected internal resource accessible only to @coverwhale.com email addresses.

## 🔒 Authentication

This GitHub Pages site uses OAuth 2.0 authentication via Google to ensure only Cover Whale employees can access the content.

### How it Works:
1. User visits the page
2. Prompted to sign in with Google
3. Email domain verified (@coverwhale.com required)
4. JWT token issued and stored
5. Content displayed

### Authentication Flow:
- **Frontend**: GitHub Pages (this repo)
- **Backend Auth**: Vercel serverless functions (`coverwhale-auth`)
- **Provider**: Google OAuth 2.0
- **Token**: JWT with 24-hour expiration

## 📁 Files

- `index.html` - Authentication wrapper and login page
- `guide.html` - The actual Master Prompt Engineering Guide content
- `README.md` - This file

## 🚀 Deployment

### Prerequisites:
- GitHub account (dmedina5)
- Vercel deployment of `coverwhale-auth` (already set up)
- GitHub Pages enabled

### Deploy Steps:

1. **Create GitHub Repository**
```bash
# Repository name: prompt-engineering-guide
# Public visibility required for GitHub Pages
```

2. **Push Code**
```bash
git add .
git commit -m "Initial commit: Protected prompt engineering guide"
git remote add origin https://github.com/dmedina5/prompt-engineering-guide.git
git branch -M main
git push -u origin main
```

3. **Enable GitHub Pages**
- Go to Settings → Pages
- Source: Deploy from main branch
- Root directory
- Save

4. **Access URL**
```
https://dmedina5.github.io/prompt-engineering-guide/
```

## 🔧 Configuration

The authentication points to:
- Auth API: `https://coverwhale-auth.vercel.app`
- Allowed domain: `@coverwhale.com`
- Token expiration: 24 hours

## 🧪 Testing

To test authentication:
1. Visit the page in incognito mode
2. Click "Sign in with Google"
3. Use a @coverwhale.com email
4. Verify guide loads
5. Refresh page - should remain authenticated
6. Clear localStorage - should prompt for login again

## 🔄 Updating the Guide

To update the guide content:
1. Edit `guide.html` locally
2. Commit and push to GitHub
3. GitHub Pages will automatically redeploy
4. No authentication changes needed

## 🛡️ Security Features

- ✅ Google OAuth 2.0 authentication
- ✅ Email domain verification (@coverwhale.com only)
- ✅ JWT tokens with expiration
- ✅ Secure token storage (localStorage)
- ✅ Token verification on every load
- ✅ HTTPS only (GitHub Pages)

## 📝 Notes

- Authentication wrapper (`index.html`) loads the guide in an iframe
- Guide content (`guide.html`) is the unmodified Master Guide
- Works on all devices (mobile responsive)
- No server-side rendering required
- Completely static hosting (GitHub Pages)

## 🐛 Troubleshooting

**Issue**: "Access Denied" message
- **Solution**: Must use @coverwhale.com email

**Issue**: Stuck on login screen
- **Solution**: Check browser console for errors, verify Vercel auth is running

**Issue**: Token expired
- **Solution**: Automatic re-login prompt after 24 hours

**Issue**: Can't authenticate
- **Solution**: Verify coverwhale-auth Vercel deployment is active

## 👥 Access Management

Currently, access is granted to any @coverwhale.com email. To restrict further:
1. Maintain whitelist in Vercel auth backend
2. Check against specific email addresses
3. Implement role-based access if needed

## 📊 Analytics (Optional)

To track usage:
1. Add Google Analytics to `index.html`
2. Track authentication events
3. Monitor guide page views

## 🔗 Related Projects

- `coverwhale-auth` - Vercel authentication backend
- `ai-prompt-builder-enhanced` - Interactive prompt builder tool
- `coverages-by-state` - Another protected GitHub Pages project

---

**Maintained by**: Daniel Medina (Manager of Core Systems)
**Last Updated**: January 2026
**Status**: Production Ready