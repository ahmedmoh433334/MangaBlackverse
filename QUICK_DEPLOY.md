# ⚡ Quick Deployment Instructions

Follow these steps to deploy **MangaBlackverse** to the web in 5 minutes!

## 🚀 Quick Start (TL;DR)

### 1️⃣ Set Up Supabase (2 minutes)

```bash
# Go to: https://supabase.com
# 1. Sign up with GitHub
# 2. Create new project: "MangaBlackverse"
# 3. Copy your credentials:
#    - Project URL: https://xxxxx.supabase.co
#    - Anon Key: eyJhbG...
# 4. Go to SQL Editor → New Query
# 5. Copy content from: supabase-schema.sql
# 6. Paste and click "Run"
```

### 2️⃣ Deploy to Vercel (2 minutes)

```bash
# Go to: https://vercel.com
# 1. Sign up with GitHub
# 2. Click "New Project"
# 3. Select your GitHub repository
# 4. Add Environment Variables:
#    NEXT_PUBLIC_SUPABASE_URL = https://xxxxx.supabase.co
#    NEXT_PUBLIC_SUPABASE_ANON_KEY = your_anon_key_here
# 5. Click "Deploy"
# 6. Wait 2-3 minutes
# 7. You have a URL! 🎉
```

### 3️⃣ Test Your Site (1 minute)

```bash
# Visit your URL from Vercel
# Check:
# ✓ Homepage loads
# ✓ Click browse anime
# ✓ Search works
# Done!
```

---

## 📋 Detailed Steps

### Step 1: Supabase Setup

#### Create Account & Project
1. Visit https://supabase.com
2. Click "Sign Up"
3. Choose "Continue with GitHub"
4. Click "New Project"
5. Enter:
   - **Name**: MangaBlackverse
   - **Password**: (strong password)
   - **Region**: nearest to you
6. Click "Create new project"
7. Wait ~3 minutes ⏳

#### Get Your Credentials
1. In Supabase Dashboard, click **Project Settings**
2. Click **API** tab
3. Copy:
   - `Project URL` (looks like: https://xxxxx.supabase.co)
   - `Anon public key` (long text starting with eyJ...)
4. Save these in a text file temporarily

#### Set Up Database
1. In Supabase Dashboard, click **SQL Editor** (on left)
2. Click **New Query**
3. In your project folder, open file: `supabase-schema.sql`
4. Copy ALL the content
5. Paste into Supabase SQL editor
6. Click **Run** button (or Ctrl+Enter)
7. Wait for success messages ✅

---

### Step 2: Vercel Deployment

#### Connect Repository
1. Visit https://vercel.com
2. Click **Sign Up** (or Sign In)
3. Choose **GitHub**
4. Click **New Project**
5. Find your repository (MangaBlackverse)
6. Click **Import**

#### Configure & Deploy
1. Framework will auto-select: **Next.js** ✓
2. Scroll down to **Environment Variables**
3. Click **Add** for each variable:

   **Variable 1:**
   - Name: `NEXT_PUBLIC_SUPABASE_URL`
   - Value: `https://xxxxx.supabase.co` (from Supabase)
   
   **Variable 2:**
   - Name: `NEXT_PUBLIC_SUPABASE_ANON_KEY`
   - Value: Your anon key (from Supabase)

4. Make sure both are set for: **Development, Preview, Production**
5. Click **Deploy** 🚀
6. Vercel will build and deploy automatically
7. Wait for "Deployment Complete" ✓

#### Get Your URL
1. When deployment finishes, you'll see:
   - Production URL (like: https://mangablackverse-abc123.vercel.app)
2. Click it to visit your live site!

---

### Step 3: Verify Everything Works

Visit your Vercel URL and check:

- [ ] Homepage loads with anime carousel
- [ ] "Browse Anime" button works
- [ ] Search bar functions
- [ ] Images load correctly
- [ ] No error messages in browser console

**Test in Browser Console:**
```javascript
// Check if Supabase is connected
console.log(localStorage.getItem('supabase.auth.token'))
```

---

## 🔧 Files You Need to Know

✅ **Already Created:**
- `.env.local` - Environment variables (local only)
- `vercel.json` - Vercel configuration
- `next.config.ts` - Next.js settings
- `DEPLOY_GUIDE.md` - Full deployment guide

✅ **Provided in Project:**
- `supabase-schema.sql` - Database schema
- `package.json` - Dependencies
- All source code in `src/` folder

---

## ❓ Troubleshooting

| Problem | Solution |
|---------|----------|
| "SUPABASE_URL is undefined" | Add env vars in Vercel dashboard, then redeploy |
| Build fails | Check Node version is 20.x in Vercel settings |
| Database errors | Make sure you ran `supabase-schema.sql` in SQL Editor |
| Images won't show | Clear browser cache (Ctrl+Shift+R) and wait 5 min |
| Build says "next not found" | Click "Redeploy" in Vercel deployments tab |

---

## 📱 After Launch

### Optional: Add Custom Domain
1. In Vercel Project Settings → **Domains**
2. Click **"Add Domain"**
3. Enter your domain (e.g., mangablackverse.com)
4. Update DNS records at your domain provider
5. Wait for DNS propagation (5-30 min)

### Automatic Updates
- Push changes to GitHub
- Vercel automatically rebuilds
- Your site updates in 2-3 minutes!

---

## 🎓 Learn More

- **Next.js**: https://nextjs.org
- **Supabase**: https://supabase.com/docs
- **Vercel**: https://vercel.com/docs
- **Tailwind**: https://tailwindcss.com

---

## ✅ Deployment Checklist

- [ ] Supabase account created
- [ ] Database initialized with `supabase-schema.sql`
- [ ] Credentials copied (URL & Anon Key)
- [ ] Vercel account created
- [ ] GitHub repo connected to Vercel
- [ ] Environment variables added to Vercel
- [ ] Deployment completed successfully
- [ ] Site loads on Vercel URL
- [ ] All features working

---

🎉 **Congratulations! Your site is live!**

Need help? Check DEPLOY_GUIDE.md for detailed instructions.
