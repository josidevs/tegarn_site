# tegarn_site

Minimal landing page for **tegarnbygg.se**, hosted on GitHub Pages.

```
public/index.html                # the site
.github/workflows/pages.yml      # deploys public/ to GitHub Pages on every push to main
```

Preview locally by opening `public/index.html` in a browser.

## Deploy

1. Push to GitHub. In the repo: **Settings → Pages → Source: GitHub Actions**.
2. **Settings → Pages → Custom domain:** `tegarnbygg.se`, then tick **Enforce HTTPS**
   once the certificate is issued (can take up to ~1 hour after DNS resolves).
3. DNS (in Oderland's DNS management for tegarnbygg.se):

   | Type  | Name | Value                    |
   |-------|------|--------------------------|
   | A     | @    | 185.199.108.153          |
   | A     | @    | 185.199.109.153          |
   | A     | @    | 185.199.110.153          |
   | A     | @    | 185.199.111.153          |
   | AAAA  | @    | 2606:50c0:8000::153      |
   | AAAA  | @    | 2606:50c0:8001::153      |
   | AAAA  | @    | 2606:50c0:8002::153      |
   | AAAA  | @    | 2606:50c0:8003::153      |
   | CNAME | www  | `<github-user>.github.io` |

   Remove any old A/AAAA records for `@`/`www`. **Leave MX/SPF/DKIM records alone**
   so email to thomas@tegarnbygg.se keeps working.

After that, every push to `main` redeploys automatically.
