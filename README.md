# midiboard-site

The public website for **Midiboard** — an iPhone Bluetooth MIDI controller with a layout editor you
build your own control surfaces in. A landing page, a support page and a privacy policy. Static: three
HTML files, one stylesheet and some images. No build step, no framework, and no requests to anything
outside this folder.

**This repository contains no application source.** Midiboard itself lives in a private repository; only
the website is here, so the site can be hosted publicly without publishing the app.

## Why this exists separately

GitHub Pages only serves free sites from public repositories, and the app's repository has to stay
private. Keeping the site in its own public repository solves that without exposing anything else.

If the site is hosted on Cloudflare Pages instead — which *can* deploy from a private repository — this
repository isn't needed; the app repo's `site/` directory is deployed directly and this becomes a mirror
you can ignore.

## Source of truth

**Do not edit these files here.** They are mirrored from `site/` in the app repository, which is where
the screenshots are generated and where the copy is kept in step with what the app actually does.
Editing here means the next mirror silently overwrites your change.

To publish an update, run this from the app repository:

```sh
./tools/publish-site.sh
```

It copies `site/` across, drops the internal notes that shouldn't be public, commits and pushes.

## Hosting

Any static host works. The site is deliberately self-contained: no CDN, no fonts, no analytics, nothing
to configure.

- **GitHub Pages** — Settings → Pages → Deploy from a branch → `main` / root. The `.nojekyll` file stops
  Jekyll from processing the folder.
- **Cloudflare Pages / Netlify** — connect the repository, leave the build command empty, output
  directory is the root.

A custom domain needs a `CNAME` file here (GitHub Pages) or a Custom Domain entry in the host's
dashboard. `.app` domains are HTTPS-only; every host above issues the certificate for free.
