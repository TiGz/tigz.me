# tigz.me

Static showcase homepage for [tigz.me](https://tigz.me), featuring web applications by Adam Chesney.

## Featured Projects

- **[Avatarz](https://tigz.me/avatarz)** - AI-powered avatar generation
- **[Foosbournament](https://tigz.me/foosbournament)** - Foosball tournament management

## Development

This is a static HTML site with no build step required. Open `index.html` in a browser to preview.

```bash
# Using Python
python -m http.server 8000

# Using Node.js
npx serve .
```

## Deployment

The site deploys automatically to GitHub Pages on push to `main` via the workflow in `.github/workflows/deploy.yml`.

### Initial GitHub Pages Setup

1. Go to repository **Settings** > **Pages**
2. Under "Build and deployment", select **GitHub Actions** as the source
3. Push to `main` to trigger the first deployment

## Custom Domain Setup

### Setting up tigz.me

1. In GitHub repository **Settings** > **Pages**, enter `tigz.me` as the custom domain
2. GitHub will create a `CNAME` file automatically
3. Configure DNS with your domain registrar:

   | Type  | Name | Value                  |
   |-------|------|------------------------|
   | A     | @    | 185.199.108.153        |
   | A     | @    | 185.199.109.153        |
   | A     | @    | 185.199.110.153        |
   | A     | @    | 185.199.111.153        |
   | CNAME | www  | tigz.github.io  |

4. Wait for DNS propagation (up to 24 hours)
5. Enable "Enforce HTTPS" once the certificate is provisioned

### Mapping Sibling Apps to tigz.me

The sibling apps (avatarz, foosbournament) can be deployed to `tigz.me`:

#### Option A: Subdirectories (Recommended)

Deploy each app to `tigz.me/avatarz` and `tigz.me/foosbournament`:

1. In each app's GitHub repo settings, set the custom domain to `tigz.me`
2. Configure each app's build to use the correct base path:
   - Avatarz: `base: '/avatarz/'` in vite.config
   - Foosbournament: `base: '/foosbournament/'` in vite.config
3. The apps will be served as subdirectories of the main tigz.me site

**Note:** GitHub Pages only allows one custom domain per repository. For subdirectory routing, consider:
- Using a single monorepo with all apps
- Using a reverse proxy or CDN like Cloudflare
- Using Cloudflare Pages instead (supports multiple projects on subpaths)

#### Option B: Subdomains

Use `avatarz.tigz.me` and `foosbournament.tigz.me`:

1. In each app's GitHub repo, go to **Settings** > **Pages**
2. Set custom domain to `avatarz.tigz.me` or `foosbournament.tigz.me`
3. Add DNS records:

   | Type  | Name           | Value                  |
   |-------|----------------|------------------------|
   | CNAME | avatarz        | tigz.github.io  |
   | CNAME | foosbournament | tigz.github.io  |

4. Update each app's build config for the root path (no subdirectory needed)
5. Enable HTTPS for each subdomain

## Tech Stack

- Vanilla HTML/CSS (no build step)
- Satoshi + General Sans fonts via Fontshare
- GitHub Actions for deployment
- GitHub Pages for hosting
