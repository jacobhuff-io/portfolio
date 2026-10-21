# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A personal portfolio site for jacobhuff.io, built with [Hugo](https://gohugo.io/) and the [PaperMod](https://github.com/adityatelange/hugo-PaperMod) theme, deployed to GitHub Pages. There is no application code, test suite, or linter — the repo is site configuration plus (eventually) Markdown content.

## Commands

Requires Hugo **extended** and Go (CI uses Hugo 0.162.1, Go 1.26.2, Dart Sass 1.99.0).

```bash
hugo server -D                          # local dev server incl. drafts, http://localhost:1313
hugo build --gc --minify                # production build into ./public (same flags as CI)
hugo new content posts/my-post.md       # new page from archetypes/default.md (created with draft: true)
hugo mod get -u                         # update the PaperMod module version in go.mod/go.sum
```

## Architecture notes

- **Config:** `hugo.yaml` is the only site config. `baseURL` is `https://jacobhuff.io/`, but CI overrides it with the GitHub Pages URL via `--baseURL`.
- **Theme:** PaperMod is loaded only as a Hugo Module (`module.imports` in `hugo.yaml`, version pinned in `go.mod`/`go.sum`). There is no `themes/` directory or git submodule. Change theme versions with `hugo mod get`; to override theme templates, put files at the same path under the site's own `layouts/`.
- **Styling:** the look follows the e-ink design laws (only ink `#000` and paper `#fff`, no greys, hierarchy by weight, line weights 1/2/3/4 px by role, no transitions). It lives in `assets/css/extended/eink.css`, which PaperMod appends after its own CSS, and `layouts/partials/extend_head.html` (loads Lato). Dark mode and the theme toggle are off in `hugo.yaml`.
- **Content:** no `content/` directory exists yet. New pages default to `draft: true` (from `archetypes/default.md`) and won't appear in production builds until that flag is removed.
- **Deployment:** `.github/workflows/hugo.yaml` builds and deploys to GitHub Pages on every push to `main` (or manual dispatch). Pushing to `main` publishes the site.
