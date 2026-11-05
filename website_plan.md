# Website Plan

Roadmap for updating https://ethanmur.github.io/ (Jekyll, Minimal Mistakes fork, hosted on GitHub Pages).

## Guiding decisions
- Stay on **GitHub Pages** for hosting. Revisit object storage (e.g. Cloudflare R2) only if files outgrow the repo.
- **Skip** interactive maps, iframes and server-side code for now. Return to them when a blog post needs one.
- Keep the blog on this site (not Substack/Medium). Revisit if the audience grows.
- Local preview before committing: `bundle exec jekyll serve --livereload`, then open http://localhost:4000

## 1. Landing page update
- Keep the left author sidebar for now.
- Add larger banner images in the middle of the page.
- Add a one or two sentence blurb about what I do beneath the images.
- Notes:
  - Options: `header: overlay_image` in `_pages/about.md` front matter (uses `_includes/page__hero.html`), or image markup in the page body.
  - Test `author_profile: true` vs `false` and `classes: wide` to see which layout feels right.
  - A fully custom landing page (the `splash` layout, deleted in cleanup but recoverable from git history) is a possible later experiment.
  - Put images in `images/` (and compress them; large files slow the site and bloat the repo).

## 2. Custom domain
- Buy **ethanmurray.com** or **ethanmurrayweather.com** (both checked as candidates; ethanmurray.com is preferred for brevity).
- Steps:
  1. Buy the domain from a registrar (Cloudflare, Namecheap, Porkbun).
  2. Add DNS records pointing to GitHub Pages (A records to GitHub's IPs, or a CNAME from `www` to `ethanmur.github.io`; check GitHub's docs for current values).
  3. Set the custom domain under repo Settings -> Pages (creates a `CNAME` file) and enable "Enforce HTTPS".
  4. Update `url:` in `_config.yml` to the new address.
  5. Confirm the old `ethanmur.github.io` address redirects.

## 3. Hosting
- Remain on GitHub Pages (soft limits: ~1 GB repo, 100 MB per file).
- Datasets and images are currently megabytes each, so no external storage is needed.
- Possible later: Cloudflare R2 for large files, Zenodo for citable datasets and manuscripts.

## 4. Blog and comments
- Add a `_posts/` folder (files named `YYYY-MM-DD-title.md`) with plain text, images and video.
- Replace the hand-written list in `_pages/blog.md` with an auto-generated post list.
- Comments: **Giscus** (free, uses GitHub Discussions).
  - Enable Discussions on the repo, install the giscus app, then configure it via the theme's custom comments provider.
- Audience: posting quietly to build forecasting and writing skills. Consider Substack or similar later if readership grows. The existing RSS feed (`jekyll-feed`) already supports subscriptions.

## Next up: content tasks
- [ ] **About tab:** expand the About text with more detail (affiliations, research background, interests). It currently has only the PhD/Vassar and current-research paragraphs.
- [ ] **Research tab:**
  - Make the one-slide and four-slide overview decks visible on the page itself (embedded viewer or inline images), not just download links. Note: originally written as "home page"; confirm whether that means the Research tab or the landing page.
  - Update both decks first. They are about two years old (`files/ethan-murray-research-one-slide.pdf`, `files/ethan-murray-research-four-slides.pdf`).
  - Brainstorm other additions to the tab (e.g. project summaries, key figures, datasets or code links, field campaign photos, current/ongoing work).
- [ ] **Publications tab:** add recent papers in CV format, newest to oldest, in full bibliography style.
  - Currently the page loops over an empty `publications` collection. Options: add one entry per paper under `_publications/`, or write a single list in the page. A single list is simpler for a short publication record.
- [ ] **CV tab:** replace with the latest resume and CV PDFs (`files/ethan-murray-resume.pdf`, `files/ethan-murray-cv.pdf`) and update the date labels on the links.
- [ ] **Blog:** start a new post on historic southwest Colorado flooding.
  - Needs the `_posts/` folder and an auto-generated post list on `_pages/blog.md` (see section 4). Giscus comments can follow.
- [ ] **Photography tab:** decide whether to remove it or add to it. It currently holds film camera notes and a Sand Dunes gallery. If kept, consider more galleries and a short intro; if removed, drop it from the nav and the About page text.

## Later / deferred
- Interactive viewers (JavaScript charts, or chunked data such as Zarr/Parquet read straight from storage with no server).
- Server-side or iframe-embedded apps, only if a post requires them.
- Remaining cleanup:
  - (none)

## Done
- Cleanup of demo content, dead automation and unused includes/layouts.
- `_config.yml` trimmed of empty keys and unused blocks (talks, staticman, analytics, etc.). Add keys back when needed, e.g. `comments: provider: "custom"` for Giscus.
- Research page title changed to "Research"; About-page typos fixed.
- Gemfile simplified to `github-pages` + `webrick`.
- Landing page: image mosaic, Playfair Display blurb, new headshot, updated sidebar (location, affiliation, email shown as text), gray page background, larger "Home" nav title with darker text and border.
- About text moved to its own About tab.
