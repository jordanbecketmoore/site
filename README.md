# moorelab.dev

Developer homepage and home lab blog for Jordan Moore. Built with [Hugo](https://gohugo.io/) and the [PaperMod](https://github.com/adityatelange/hugo-PaperMod) theme.

## Deployment

Files are git-synced into a Hugo container and served with:

```
hugo server
```

## Local Development

```
hugo server -D   # serves at http://localhost:1313, includes drafts
```

## Adding Content

```
hugo new content blog/my-post-title.md
```

Set `draft: false` in the front matter to publish.

## Lab Stats

Edit `data/lab.yaml` to update the stats and service list shown on the [/lab](/lab) page.
