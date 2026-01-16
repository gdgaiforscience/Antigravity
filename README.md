# Antigravity
Google's Antigravity IDE can supercharge your scientific workflows and pipelines.

Modify `antigravity.qmd` to update the tutorial pages: https://gdgaiforscience.github.io/Antigravity/

# Setting up this repo for auto-building the github pages site

Build the workshop files locally with 
```
git clone  
cd Antigravity
quarto render antigravity.qmd 
git commit -am "New build"
git push
```

You must also make a `gh-pages` branch and publish the quarto pages to it locally first. Probably better ways to do this:
```
git checkout -n gh-pages
quarto publish gh-pages antigravity.qmd 
git push origin gh-pages
git checkout main
```

On the repo turn on github pages at: https://github.com/gdgaiforscience/Antigravity/settings/pages
And have it render from `gh-pages` branch.

Add this github action file to render the quarto page on any repo updates. Note any code execution (e.g Python or executable blocks with `{}` syntax will need more installations).
```
name: Quarto Publish

on:
  push:
    branches: main

permissions:
  contents: write
  
jobs:
  build-deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Check out repository
        uses: actions/checkout@v3

      - name: Set up Quarto
        uses: quarto-dev/quarto-actions/setup@v2
        with:
          tinytex: true

      - name: Publish to GitHub Pages (and render)
        uses: quarto-dev/quarto-actions/publish@v2
        with:
          target: gh-pages
          path: antigravity.qmd
```
