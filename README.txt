M&N MASONRY - STATIC SITE
=========================

PREVIEW LOCALLY
Double-click index.html. All paths are relative, so images and links work
straight from the folder with no server needed. The embedded GoHighLevel
form needs an internet connection to load.

DEPLOY
1. Drag this whole folder into Cloudflare Pages or Netlify.
2. Point mandnmasonryct.com at it from Porkbun DNS.
3. Turn on "force HTTPS".
4. 404.html is picked up automatically by both hosts.
5. Submit https://mandnmasonryct.com/sitemap.xml in Google Search Console.

THE FORM
The GoHighLevel survey (NdQLG01OU0jSOXUSEftG) is embedded in the "Get your
free estimate" block at the bottom of all 31 pages. form_embed.js loads once
per page, right before </body>, which is what auto-sizes the iframe height.
Do not add a second copy of that script to a page.

BEFORE GOING LIVE - three replacements left
1. PHONE. (203) 555-0147 is a placeholder in the reserved fake-number range.
   Find and replace it, and the tel:+12035550147 links, across all files.
2. INSURANCE. Pages say "licensed and fully insured, certificate on request".
   Swap in the real liability limits once you have the COI.
3. PROJECT COUNT. Pages say 27 years. The "200+ projects" figure was left out
   because it contradicts the founding date. Add the real number.

STRUCTURE
  index.html                    homepage
  services/index.html           hub, links to all 16
  services/<slug>/index.html    16 service pages
  service-areas/index.html      hub, links to all 12
  service-areas/<slug>/         12 town pages
  images/                       29 photos plus the logo
  404.html, sitemap.xml, robots.txt

NAVIGATION
- Services and Service Areas open on hover on desktop, and on tap under 1050px
  where a Menu button appears.
- Internal links point at index.html so the folder works by double-click.
  Cloudflare Pages and Netlify both normalise /x/index.html to /x/ live, and
  every canonical tag already declares the clean trailing-slash URL.
