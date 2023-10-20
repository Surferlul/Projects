---
title: "GitHub Action - logseq-publish-theme-tenset"
---

A postprocessor for logseq-spa. Applies logseq-tenset-theme to published site

## Example Action

```yaml
on: [push]

permissions:
  contents: write
jobs:
  test:
    runs-on: ubuntu-latest
    name: Publish Logseq graph
    steps:
      - uses: actions/checkout@v3
      - uses: logseq/publish-spa@main
        with:
          version: nightly
          theme-mode: dark
      - name: apply tenset theme
        uses: Surferlul/logseq-publish-theme-tenset@main
      - name: add a nojekyll file # to make sure asset paths are correctly identified
        run: touch $GITHUB_WORKSPACE/www/.nojekyll
      - name: Deploy 🚀
        uses: JamesIves/github-pages-deploy-action@v4
        with:
          folder: www
```

### [View on Marketplace](https://github.com/marketplace/actions/logseq-publish-apply-tenset-theme)

### [View on Github](https://github.com/Surferlul/logseq-publish-theme-tenset)