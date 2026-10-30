# DayCasion export download page

Static page served by GitHub Pages at https://export.daycasion.com.

It holds no secrets and no member data. A member opens it from the link in their "export ready" email
(`https://export.daycasion.com/#export=<export id>`; the id stays in the address fragment, which is never sent to
this host), signs in with their DayCasion email and password, and downloads their ZIP parts.

Every check is made by Supabase, not by this page:
- sign-in: Supabase Auth (the same accounts as the app);
- which exports are visible: row-level security on `export_jobs` (owner only);
- downloads: 1-hour signed links that Supabase Storage issues only to the owner of a ready, unexpired export.

The publishable key in index.html is the public key the app also uses; it grants nothing on its own.

Files: `index.html` (the page), `CNAME` (custom domain), `.nojekyll` (serve files as-is), `robots.txt` (no indexing).
