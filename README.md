# SoundCode For Dolby E — User Guide

MkDocs Material documentation site for **SoundCode For Dolby E**.

## Local development

```bash
pip install mkdocs-material
mkdocs serve
```

Then open <http://127.0.0.1:8000>.

## Build

```bash
mkdocs build
```

The static site is generated into `site/`, which is committed to the repository.
Rebuild and commit `site/` whenever you change the docs.

## Deployment

Pushing to this repository triggers the GitHub Actions workflow in
[.github/workflows/main.yml](.github/workflows/main.yml), which syncs the
pre-built `site/` directory into the `neyrinckaudio/docs-neyrinck` repository
under the `soundcode-dolby-e/` target directory (published at
`neyrinck.com/soundcode-dolby-e/docs`).

The sync uses the `DIST_REPO_PAT` secret — a Personal Access Token with write
access to `neyrinckaudio/docs-neyrinck`. Set it under **Settings → Secrets and
variables → Actions** in this repository.
