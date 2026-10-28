# tegarn_site

Minimal landing page for **tegarnbygg.se**, hosted on Oderland (cPanel).

```
public/
  index.html   # the site
  .htaccess    # HTTPS + non-www redirect
.cpanel.yml    # cPanel Git deploy: copies public/ -> ~/public_html/
```

Preview locally by opening `public/index.html` in a browser.

## Deploy to Oderland

### Option A – cPanel Git Version Control (recommended)

1. Push this repo to GitHub/GitLab (or any reachable Git remote).
2. In Oderland's cPanel: **Files → Git™ Version Control → Create**.
   - Clone URL: your repo URL (private repos need an SSH deploy key added in cPanel's *SSH Access*).
   - Repository path: e.g. `repositories/tegarn_site` (**not** `public_html`).
3. Open the repo in cPanel → **Pull or Deploy** tab → *Update from Remote* → *Deploy HEAD Commit*.
   cPanel runs `.cpanel.yml`, which copies `public/` into `~/public_html/`.

Future updates: `git push`, then *Update from Remote* + *Deploy HEAD Commit* in cPanel.

### Option B – Manual upload

Upload the contents of `public/` (including the hidden `.htaccess`) to `public_html/`
via cPanel **File Manager** or SFTP (host/user from Oderland's welcome email).

### Notes

- Make sure `tegarnbygg.se` is the primary domain of the cPanel account (or that its
  document root is `public_html`); otherwise adjust `DEPLOYPATH` in `.cpanel.yml`.
- `.htaccess` forces HTTPS. If the SSL certificate isn't issued yet, run
  **Security → SSL/TLS Status → Run AutoSSL** in cPanel.
