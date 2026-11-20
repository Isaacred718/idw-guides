# IDW Guides

Local static site for the IDW 30 day church first directory test.
Intended address: guides.idwent.com
Status: Publishing approved by Isaac on 2026-11-20. Published to GitHub Pages with custom domain guides.idwent.com.

## What is here

- index.html: home page listing the 3 live draft guides and the planned topics
- style.css: IDW black and gold styling, no build step, no external assets
- guides/: 3 full guide pages as HTML, publish ready drafts pending Isaac's review
- Outlines for pages 4 to 12 live outside this repo in ~/workspace/idw-guides-drafts/ (local only, not published). No HTML exists for these yet, by design.
- sitemap.xml: lists only the home page and the 3 guide pages
- robots.txt: allows all crawlers, points to the sitemap
- CNAME: contains guides.idwent.com, for GitHub Pages

## Writing rules used

- Short, plain, direct copy for church volunteers
- No em dashes and no en dashes in client facing copy
- No prices anywhere
- No invented client stories, testimonials, or results
- No affiliate links and no email addresses published
- Every guide ends with a soft call to action for a free 15 minute Room and Stream Health Check, linking to the contact area at https://idwent.com/

## Deploy steps (for later, only when Isaac approves publishing)

Hosting route: GitHub Pages. Note, from the day 1 check on 2026-11-19: idwent.com is live on GitHub Pages, the guides subdomain still hits Porkbun wildcard parking, and the Cloudflare signup was never completed. So GitHub Pages is the route, not Cloudflare.

1. Create a new public GitHub repository, for example idw-guides, under the isaacred718 account.
2. Upload or push the contents of this folder to the repository root, including the CNAME file. The CNAME file must stay at the root and must contain exactly: guides.idwent.com
3. In the repository on GitHub, open Settings, then Pages. Set the source to deploy from the main branch, root folder.
4. Wait for the first Pages build to finish. The site will first appear at isaacred718.github.io plus the repository path, until DNS is set.
5. DNS at Porkbun, one explicit record only:
   - Log in to Porkbun and open DNS for idwent.com.
   - Add a CNAME record: host guides, target isaacred718.github.io
   - This explicit guides record must override the existing wildcard parking record, which currently points subdomains at Porkbun parking. An explicit host record takes priority over a wildcard in DNS. Do not delete other records unless a later check says to. Leave the apex records for idwent.com itself untouched.
   - Do not change the apex, www, mail, or verification records as part of this step.
6. Back in GitHub Pages settings, confirm the custom domain shows guides.idwent.com and wait for the HTTPS certificate to be issued. Tick Enforce HTTPS once the certificate is ready.
7. Verify: open https://guides.idwent.com/ and each of the 3 guide URLs from sitemap.xml. Check them on a phone as well as a desktop.
8. Only after the site is verified live: add the property in Google Search Console and submit https://guides.idwent.com/sitemap.xml

## If DNS does not take

- Allow time for DNS to propagate, then recheck.
- Confirm in Porkbun that the explicit guides CNAME exists and has no typo, and that no conflicting A or AAAA record exists for the guides host.
- Confirm the CNAME file in the repository root still contains only guides.idwent.com

## Rollback

- Remove the guides CNAME record at Porkbun to take the subdomain offline. The main idwent.com site is a separate setup and is not affected by this folder.
