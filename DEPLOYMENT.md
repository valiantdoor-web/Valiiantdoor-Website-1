# Valiant Garage Door Website - Production Deployment Guide

## Deployment Status

**Last Updated:** February 4, 2026  
**Status:** ⚠️ Ready for Production - Deployment Required

## Overview

The Valiant Garage Door website is fully developed and ready for production deployment. All code, branding, assets, and functionality are complete on the `main` branch. However, the actual production deployment to a live URL needs to be completed.

## Current State

### ✅ What's Complete
- [x] All website pages (Home, Services, About, Contact, Quote, Mission, Gallery)
- [x] Professional branding and design
- [x] Backend API with Express.js and Nodemailer
- [x] Quote request form with email notifications
- [x] SEO optimization (sitemap.xml, robots.txt)
- [x] Vercel deployment configuration (vercel.json)
- [x] Security features (rate limiting, input validation)
- [x] Responsive design for all devices
- [x] All assets and images

### ⚠️ What Needs Action
- [ ] Active production deployment on Vercel
- [ ] Live production URL
- [ ] Environment variables configured in Vercel dashboard
- [ ] DNS configuration (if using custom domain)
- [ ] Updated sitemap.xml and robots.txt with actual production URL

## Deployment Instructions

### Option 1: Deploy to Vercel (Recommended)

#### Prerequisites
- Vercel account (free tier available at https://vercel.com)
- GitHub repository access

#### Steps

1. **Connect Repository to Vercel**
   - Go to https://vercel.com/new
   - Import the GitHub repository: `vm-valiantshit/Valiiantdoor-Website`
   - Select the `main` branch for production

2. **Configure Project Settings**
   - Framework Preset: Other
   - Root Directory: ./
   - Build Command: (leave empty - not needed)
   - Output Directory: (leave empty - not needed)

3. **Set Environment Variables**
   Navigate to Project Settings → Environment Variables and add:
   ```
   SMTP_HOST=smtp.gmail.com
   SMTP_PORT=587
   SMTP_SECURE=false
   SMTP_USER=valiantdoor@gmail.com
   SMTP_PASS=your-gmail-app-password
   REQUESTS_TO=vm@valiantdoor.com
   REQUESTS_FROM=vm@valiantdoor.com
   PORT=3000
   ```
   
   **Important Gmail Configuration:**
   - For Gmail, you **MUST** use an [App Password](https://support.google.com/accounts/answer/185833), not your regular Gmail password
   - To create an App Password:
     1. Go to your Google Account settings
     2. Navigate to Security → 2-Step Verification (enable if not already)
     3. Scroll to "App passwords"
     4. Generate a new app password for "Mail"
     5. Use this 16-character password as `SMTP_PASS`
   - The Gmail account is: `valiantdoor@gmail.com`
   - Emails will be sent to: `vm@valiantdoor.com`

4. **Deploy**
   - Click "Deploy"
   - Wait for deployment to complete (usually 1-2 minutes)
   - Vercel will provide a production URL (e.g., `your-project.vercel.app`)

5. **Update URLs in Repository**
   After deployment, update the following files with your actual production URL:
   - `sitemap.xml` - Replace all instances of the URL
   - `robots.txt` - Update the Sitemap URL
   
   Commit and push these changes to trigger automatic redeployment.

6. **Test Production Site**
   - Visit your production URL
   - Test the quote form submission
   - Verify email notifications are working
   - Check all pages load correctly
   - Test mobile responsiveness

#### Optional: Custom Domain

1. In Vercel Dashboard:
   - Go to Project Settings → Domains
   - Add your custom domain (e.g., `valiantgaragedoor.com`)
   - Follow DNS configuration instructions
   - Wait for DNS propagation (up to 48 hours)

2. Update URLs again with custom domain in:
   - `sitemap.xml`
   - `robots.txt`

### Option 2: Deploy via Vercel CLI

```bash
# Install Vercel CLI
npm i -g vercel

# Login to Vercel
vercel login

# Deploy to production
vercel --prod

# Set environment variables (interactive)
vercel env add SMTP_HOST production    # smtp.gmail.com
vercel env add SMTP_PORT production    # 587
vercel env add SMTP_USER production    # valiantdoor@gmail.com
vercel env add SMTP_PASS production    # Your Gmail App Password
vercel env add REQUESTS_TO production  # vm@valiantdoor.com
vercel env add REQUESTS_FROM production # vm@valiantdoor.com
```

**Note:** For `SMTP_PASS`, you must use a Gmail App Password, not your regular password.

### Option 3: Other Hosting Platforms

The website can also be deployed to:
- **Netlify**: Similar process to Vercel
- **Railway**: Good for Node.js apps
- **Render**: Free tier available
- **Traditional VPS**: Deploy with PM2 or similar

For these platforms:
1. Connect your GitHub repository
2. Set build command: `npm install`
3. Set start command: `npm start`
4. Configure environment variables as listed above

## Post-Deployment Checklist

After successful deployment:

- [ ] Verify live URL is accessible
- [ ] Test quote form submission
- [ ] Confirm email notifications work
- [ ] Check all page links
- [ ] Verify images load correctly
- [ ] Test mobile responsiveness
- [ ] Update sitemap.xml with production URL
- [ ] Update robots.txt with production URL
- [ ] Submit sitemap to Google Search Console
- [ ] Test contact forms
- [ ] Review SSL certificate (HTTPS)
- [ ] Monitor first week for errors

## Monitoring and Maintenance

### Vercel Dashboard
- Access deployment logs
- View analytics
- Monitor function invocations
- Check error rates

### Regular Maintenance
- Monitor email notifications
- Review contact form submissions
- Update content as needed
- Keep dependencies updated (`npm update`)

## Troubleshooting

### Email Not Sending
1. Verify environment variables in Vercel dashboard:
   - `SMTP_HOST` should be `smtp.gmail.com`
   - `SMTP_USER` should be `valiantdoor@gmail.com`
   - `SMTP_PASS` should be your Gmail App Password (16 characters, no spaces)
   - `REQUESTS_TO` should be `vm@valiantdoor.com`
2. Ensure you're using a Gmail App Password, not your regular password
3. Verify 2-Step Verification is enabled on your Google Account
4. Review Vercel function logs for detailed error messages
5. Ensure SMTP port 587 is accessible from Vercel

### 404 Errors
1. Verify all files are committed to main branch
2. Check vercel.json routing configuration
3. Ensure server.js is serving static files correctly

### Deployment Fails
1. Check Vercel build logs
2. Verify package.json dependencies
3. Ensure Node.js version compatibility
4. Review vercel.json configuration

## Support

For deployment issues:
- Vercel Documentation: https://vercel.com/docs
- GitHub Repository: https://github.com/vm-valiantshit/Valiiantdoor-Website
- Contact: vm@valiantdoor.com

## Next Steps

To complete production deployment:

1. **Immediate Action Required:**
   - Deploy repository to Vercel following instructions above
   - Configure environment variables
   - Obtain production URL

2. **Follow-Up Actions:**
   - Update sitemap.xml and robots.txt with production URL
   - Test all functionality
   - Configure custom domain (optional)
   - Set up monitoring

3. **Future Enhancements:**
   - Consider Vercel KV for caching (already in dependencies)
   - Set up Vercel Analytics
   - Configure Web Vitals monitoring
   - Add backup email service

---

**Status:** The codebase is production-ready. Deployment to Vercel can be completed in under 10 minutes following the instructions above.
