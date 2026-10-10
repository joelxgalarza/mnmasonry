M&N MASONRY - CLOUDFLARE WORKERS DEPLOY
=======================================

Everything served to the public lives in public/. Nothing else in this repo is
uploaded. That is deliberate: the assets directory used to be the repo root,
which meant wrangler was uploading .git as public files.

DEPLOY
  npx wrangler deploy
The Cloudflare git integration runs this on push. It reads wrangler.jsonc, so
the "Output Directory" field in the dashboard is ignored.

Expected build log line:
  Read 65 files from the assets directory /opt/buildhome/repo/public
If it says 152 files, or the path does not end in /public, stop the deploy.

_archive/ holds the old _redirects and netlify.toml. Both were wrong for
Cloudflare: that _redirects file used Netlify syntax, and Cloudflare Workers
does not support domain-level (www to apex) redirects in that file at all.
Safe to delete _archive whenever.

public/_redirects is Workers static-asset syntax, not the archived Netlify
file. It 301s /index.html and no-slash paths onto the trailing-slash URL.
wrangler.jsonc sets html_handling to force-trailing-slash, so /services/
returns 200 and /services or /services/index.html redirect there.

WWW REDIRECT (dashboard, not a file)
  Domain > Rules > Redirect Rules > Create
    If:   Hostname equals www.mandnmasonryct.com
    Then: Dynamic redirect
          concat("https://mandnmasonryct.com", http.request.uri.path)
          301, preserve query string
  Needs a proxied DNS record for www or the rule never fires.
  All canonical tags point at the bare domain.

BEFORE GOING LIVE - three replacements
1. PHONE. (203) 555-0147 is a placeholder (reserved fake-number range).
   Replace it and the tel:+12035550147 links across public/.
2. INSURANCE. Pages say "licensed and fully insured, certificate on request".
   Swap in real liability limits once you have the COI.
3. PROJECT COUNT. Pages say 27 years. The "200+ projects" figure was left out
   because it contradicts the 1999 founding date. Add the real number.

THE FORM
GoHighLevel survey NdQLG01OU0jSOXUSEftG is on all 31 pages, with
form_embed.js loaded once per page before </body>. Do not add a second copy.
