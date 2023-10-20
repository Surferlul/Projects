---
title: "GitHub Action: logseq-excalidraw-to-svg"
---

A postprocessor for logseq-spa. Adjusts the width of the website content

## Inputs

| Input | Requred | Logseq Default | Description |
| ----- | ------- | ------- | ----------- |
| content-width | true | 810px | Width that the page content is supposed to have |

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
      - name: adjust content width
        uses: Surferlul/logseq-publish-adjust-content-width@main
        with:
          content-width: 1000px
      - name: add a nojekyll file # to make sure asset paths are correctly identified
        run: touch $GITHUB_WORKSPACE/www/.nojekyll
      - name: Deploy 🚀
        uses: JamesIves/github-pages-deploy-action@v4
        with:
          folder: www
```

### [View on Marketplace](https://github.com/marketplace/actions/logseq-adjust-content-width)

### [View on Github](https://github.com/Surferlul/logseq-publish-adjust-content-width)