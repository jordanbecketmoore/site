# moorelab.dev

Hugo static site for Jordan Moore's developer homepage and home lab blog.

## Deployment

The site runs in a Hugo container. Files are synced in via git, and the container serves the site with:

```
hugo server
```

Do not suggest static builds (`hugo --minify`) or separate web servers. The container's `hugo server` process is the runtime.

## Stack

- **Hugo** v0.161+ (extended not required)
- **Theme**: PaperMod, pinned as a git submodule at `themes/PaperMod/`
- **Lab stats**: Hugo data files (`data/lab.yaml`) — rendered at build time via the `lab-stats` shortcode, no runtime JS

## Site Structure

```
content/
  _index.md        # homepage (PaperMod profileMode)
  about.md
  links.md
  blog/            # blog posts go here
    _index.md
  lab/             # lab dashboard
    _index.md      # calls {{< lab-stats >}}
data/
  lab.yaml         # update this to change lab stats/services
layouts/
  shortcodes/
    lab-stats.html # renders data/lab.yaml as a stat grid
archetypes/
  post.md          # used by `hugo new content`
```

## Common Tasks

**Add a blog post:**
```
hugo new content blog/my-post-title.md
```
Posts are drafts by default (`draft: true`). Set to `false` to publish.

**Update lab stats:**
Edit `data/lab.yaml`. The shortcode reads it at build time — no template changes needed.

**Add a nav link:**
Add a `[[menu.main]]` entry in `hugo.toml`.

**Local preview:**
```
hugo server -D   # -D includes draft posts
```

## Theme Notes

PaperMod is a submodule — do not edit files inside `themes/PaperMod/`. Override templates by mirroring the path under `layouts/` (Hugo's standard lookup order applies).

The two deprecation warnings from PaperMod (`LanguageDirection`, `LanguageCode`) are in the theme's own templates and are harmless.
