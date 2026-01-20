# 🔧 Useful Commands for MangaBlackverse

## Development

```bash
# Start development server (localhost:3000)
npm run dev

# Watch for changes and auto-rebuild
npm run build && npm start
```

## Production

```bash
# Build for production
npm run build

# Start production server
npm start

# Run production build locally (for testing)
npm run build
NODE_ENV=production npm start
```

## Database

```bash
# Push schema to database
npm run db:push

# Generate Prisma client
npm run db:generate

# Run migrations
npm run db:migrate

# Reset database (careful - deletes data!)
npm run db:reset
```

## Code Quality

```bash
# Check for linting errors
npm run lint

# Fix linting issues
npm run lint -- --fix
```

## Deployment

```bash
# Test build before deploying
npm run build

# Check build output
ls -la .next

# Check bundle size
npm run build | grep "First Load JS"
```

## Vercel Specific

```bash
# Install Vercel CLI
npm install -g vercel

# Test deployment locally (requires Vercel CLI)
vercel dev

# Deploy to production
vercel --prod

# Check deployment status
vercel ls

# View logs
vercel logs
```

## Debugging

```bash
# Run with debug logging
DEBUG=* npm run dev

# Check Node version
node --version

# Check npm version
npm --version

# List installed packages
npm list

# Check for security vulnerabilities
npm audit

# Fix common vulnerabilities
npm audit fix
```

## Clean Up

```bash
# Clean build artifacts
rm -rf .next
rm -rf node_modules
npm install

# Clear npm cache
npm cache clean --force

# Remove lock file and reinstall (if having issues)
rm package-lock.json
npm install
```

## Testing

```bash
# Check if build succeeds
npm run build

# Verify site locally
npm run dev
# Then visit: http://localhost:3000

# Test API endpoint
curl http://localhost:3000/api/health
```

## Environment

```bash
# Copy example to local
cp env.example.txt .env.local

# Check environment variables loaded
echo $NEXT_PUBLIC_SUPABASE_URL

# Source environment file
source .env.local
```

## Git Operations

```bash
# Check git status
git status

# Add deployment files
git add DEPLOYMENT*.md QUICK_DEPLOY.md .env.local vercel.json

# Commit changes
git commit -m "chore: prepare for deployment"

# Push to GitHub
git push origin main

# View commit history
git log --oneline
```

## Package Management

```bash
# Update all packages
npm update

# Check for outdated packages
npm outdated

# Install specific version
npm install @package/name@1.2.3

# Remove package
npm uninstall @package/name
```

## Useful Links (from terminal)

```bash
# Open Supabase dashboard
open https://app.supabase.com

# Open Vercel dashboard
open https://vercel.com/dashboard

# Open GitHub repository
open https://github.com/your-username/MangaBlackverse

# Open local development server
open http://localhost:3000
```

## Next.js Specific

```bash
# Generate optimized build
next build

# Start Next.js server
next start

# Run development with hot reload
next dev

# Export static site (if using static export)
next export
```

## Docker Commands (if using Docker)

```bash
# Build Docker image
docker build -t mangablackverse .

# Run Docker container
docker run -p 3000:3000 mangablackverse

# Stop all containers
docker stop $(docker ps -aq)

# Remove unused images
docker image prune
```

## Performance Analysis

```bash
# Check build performance
npm run build | tail -30

# Analyze bundle size
npm run build | grep "First Load"

# View routes and their sizes
npm run build | grep "Route"
```

## Common Issues & Quick Fixes

```bash
# Issue: Module not found
# Fix:
rm -rf node_modules package-lock.json
npm install

# Issue: Port 3000 already in use
# Fix:
lsof -i :3000  # Find process
kill -9 <PID>   # Kill it
# Or use different port:
npm run dev -- -p 3001

# Issue: Build fails with TypeScript errors
# Fix:
npm run db:generate  # Regenerate types
npm run build

# Issue: Environment variables not loading
# Fix:
# Make sure .env.local exists and is in gitignore
# Restart dev server after changes
```

## Monitoring

```bash
# Watch file changes
npm run dev -- --watch

# Monitor process
top
ps aux | grep node

# Check disk space
df -h

# Monitor network
netstat -tuln | grep 3000
```

---

**Pro Tip**: Most of these commands are already configured in `package.json`
under the "scripts" section. You can add more scripts as needed!

For more info, check: [Next.js Commands](https://nextjs.org/docs/app/getting-started/installation#command)
