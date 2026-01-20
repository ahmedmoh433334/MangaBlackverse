# 🚀 MangaBlackverse Deployment Guide

A comprehensive guide for deploying MangaBlackverse to production using Supabase and Vercel.

## Prerequisites

- GitHub Account
- Supabase Account ([supabase.com](https://supabase.com))
- Vercel Account ([vercel.com](https://vercel.com))
- Node.js 20+ (for local testing)

---

## Step 1: Set Up Supabase

### 1.1 Create a Supabase Project

1. Go to [Supabase Dashboard](https://app.supabase.com)
2. Click **"New Project"**
3. Fill in the details:
   - **Name**: `MangaBlackverse`
   - **Database Password**: Create a strong password (save it securely!)
   - **Region**: Select the region closest to your users
4. Click **"Create new project"**
5. Wait 2-3 minutes for the project to be provisioned

### 1.2 Retrieve API Credentials

1. Once the project is created, go to **Project Settings** → **API**
2. Copy these values:
   - **Project URL**: `https://[project-id].supabase.co`
   - **Anon Public Key**: Your `anon` key (safe for frontend)
3. Save these values in a secure location

### 1.3 Initialize Database Schema

1. In Supabase Dashboard, go to **SQL Editor**
2. Click **"New Query"**
3. Open `supabase-schema.sql` from the project root
4. Copy its entire content
5. Paste it into the SQL editor in Supabase
6. Click **"Run"** or press `Ctrl/Cmd + Enter`

Expected output:
```
✅ Tables created successfully
✅ Indexes created
✅ RLS policies configured
```

---

## Step 2: Configure Environment Variables

### 2.1 Local Development

1. Create `.env.local` in the project root (template provided):
```env
NEXT_PUBLIC_SUPABASE_URL=https://your-project-id.supabase.co
NEXT_PUBLIC_SUPABASE_ANON_KEY=your-anon-public-key-here
```

2. Never commit `.env.local` to Git (it's in `.gitignore`)

### 2.2 Vercel Configuration

These variables will be added in Vercel dashboard later.

---

## Step 3: Deploy to Vercel

### 3.1 Connect Your Repository

1. Go to [Vercel Dashboard](https://vercel.com/dashboard)
2. Click **"New Project"**
3. Select your GitHub repository containing MangaBlackverse
4. Click **"Import"**

### 3.2 Configure Project Settings

1. **Framework Preset**: Select "Next.js" (auto-detected)
2. **Build Command**: `next build`
3. **Output Directory**: `.next`
4. **Install Command**: `npm ci`

### 3.3 Add Environment Variables

1. Scroll down to **"Environment Variables"**
2. Click **"Add"** and enter:
   - **Name**: `NEXT_PUBLIC_SUPABASE_URL`
   - **Value**: `https://your-project-id.supabase.co`
   - **Environments**: Select all (Development, Preview, Production)

3. Click **"Add"** again for the second variable:
   - **Name**: `NEXT_PUBLIC_SUPABASE_ANON_KEY`
   - **Value**: Your anon public key
   - **Environments**: Select all

4. Click **"Deploy"**

### 3.4 Monitor Deployment

1. Vercel will automatically build and deploy
2. Watch the deployment logs - look for:
   ```
   ✓ Compiled successfully
   ✓ Build completed
   ```
3. Once complete, you'll see your **Production URL**

---

## Step 4: Verify Deployment

### 4.1 Test Your Site

1. Visit your Vercel URL (format: `https://mangablackverse-xxxxx.vercel.app`)
2. Check these features:
   - Homepage loads properly ✓
   - Anime listings display ✓
   - Search functionality works ✓
   - Images load correctly ✓
   - Navigation between pages works ✓

### 4.2 Test API Endpoints

Check health status:
```bash
curl https://your-vercel-url.vercel.app/api/health
```

Should return: `{"status":"ok"}`

### 4.3 Check Database Connection

Test if Supabase connection works:
```bash
curl https://your-vercel-url.vercel.app/api/popular
```

Should return anime data from Supabase.

---

## Step 5: Set Up Custom Domain (Optional)

1. In Vercel Project Settings → **Domains**
2. Click **"Add Domain"**
3. Enter your domain name
4. Follow DNS configuration instructions
5. Wait for DNS propagation (5-30 minutes)

---

## Step 6: Enable Continuous Deployment

Every time you push to your GitHub repository:
1. Vercel automatically rebuilds your site
2. Deploys to a preview URL first
3. After approval, deploys to production

To set up auto-deployment:
1. Go to Vercel Project Settings → **Git**
2. Ensure **"Deploy on push to main"** is enabled
3. All future pushes will trigger automatic deployments

---

## Common Issues & Solutions

### Issue: NEXT_PUBLIC_SUPABASE_URL is undefined

**Solution**:
- Go to Vercel Project Settings → Environment Variables
- Verify both variables are added
- Redeploy: Go to Deployments → Click latest → Click "Redeploy"

### Issue: Images not displaying

**Solution**:
- Check `next.config.ts` has correct `remotePatterns`
- Ensure MyAnimeList and Supabase domains are whitelisted
- Clear browser cache and hard refresh (Ctrl+Shift+R)

### Issue: Database connection errors

**Solution**:
- Verify Supabase project is running
- Check `supabase-schema.sql` was executed
- Verify credentials in Vercel environment variables
- Check Supabase project logs for errors

### Issue: Build fails with "next: not found"

**Solution**:
- In Vercel Project Settings, verify:
  - Node.js version is 20.x
  - Build command is `next build`
  - Install command is `npm ci`

### Issue: 404 errors on routes

**Solution**:
- This is normal for API routes - they return 404 if accessed directly
- Test with curl or fetch to proper endpoints
- Check API routes exist in `src/app/api/`

---

## Performance Monitoring

### Enable Analytics in Vercel

1. Go to Project Settings → **Analytics**
2. Enable Web Analytics
3. Get insights on:
   - Page load times
   - Traffic patterns
   - Core Web Vitals

### Monitor Supabase

1. Go to Supabase Dashboard → **Logs**
2. Check for:
   - Query errors
   - Authentication issues
   - Database performance

---

## Security Best Practices

✅ **DO:**
- Keep `NEXT_PUBLIC_SUPABASE_ANON_KEY` secret even though it's "public"
- Use Supabase RLS (Row Level Security) policies
- Rotate database passwords regularly
- Enable two-factor authentication on Supabase & Vercel

❌ **DON'T:**
- Commit `.env.local` to Git
- Share API keys in public
- Use production database for testing
- Disable HTTPS
- Leave database accessible from anywhere

---

## Scaling Your Application

### Database Optimization

1. Monitor Vercel Analytics for slow pages
2. Review Supabase query logs
3. Add database indexes for frequently searched fields
4. Consider implementing caching

### Image Optimization

Current setup uses:
- Next.js Image Optimization
- Automatic format conversion (WebP)
- Responsive images
- Lazy loading

### Monitoring & Alerts

1. Set up Vercel project alerts
2. Monitor Supabase metrics
3. Receive notifications on deployment failures
4. Track error logs

---

## Useful Commands

```bash
# Development
npm run dev          # Start dev server on localhost:3000

# Production Build
npm run build        # Create optimized build
npm start            # Start production server

# Database Management
npm run db:generate  # Generate Prisma client
npm run db:push      # Push schema to database
npm run db:migrate   # Run migrations
npm run db:reset     # Reset database (careful!)

# Code Quality
npm run lint         # Run ESLint
```

---

## Resources

- **Next.js Docs**: https://nextjs.org/docs
- **Supabase Docs**: https://supabase.com/docs
- **Vercel Docs**: https://vercel.com/docs
- **Tailwind CSS**: https://tailwindcss.com/docs
- **shadcn/ui**: https://ui.shadcn.com/

---

## Support & Troubleshooting

If you encounter issues:

1. Check the deployment logs in Vercel
2. Review Supabase project logs
3. Test locally with `npm run dev`
4. Verify environment variables
5. Clear build cache and redeploy
6. Check GitHub Actions logs if using CI/CD

---

## Deployment Checklist

- [ ] Supabase project created
- [ ] Database schema initialized
- [ ] API credentials copied
- [ ] `.env.local` configured locally
- [ ] GitHub repository is public or Vercel has access
- [ ] Vercel project created and connected
- [ ] Environment variables added to Vercel
- [ ] First deployment completed successfully
- [ ] Site loads on Vercel URL
- [ ] API endpoints responding
- [ ] Database queries working
- [ ] Custom domain configured (optional)
- [ ] CI/CD pipeline enabled
- [ ] Analytics enabled
- [ ] Monitoring configured

---

## Next Steps

After deployment:

1. **Promote to Production**: Set up your custom domain
2. **Monitor Performance**: Enable Vercel Analytics
3. **Set Up Alerts**: Configure error notifications
4. **Plan Scaling**: Monitor usage and scale as needed
5. **Regular Backups**: Set up automatic Supabase backups

---

🎉 **Congratulations! Your site is now live on the web!**

For questions or issues, refer to the official documentation or GitHub issues.
