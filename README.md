# Antigravity
Google's Antigravity IDE can supercharge your scientific workflows and pipelines

# Building

on the repo turn on github pages at: https://github.com/gdgaiforscience/Antigravity/settings/pages
And have it render from root, then:

Build the workshop files with 
```
git clone  
cd Antigravity
quarto render antigravity.qmd 
git commit -am "New build"
git push
```
quarto publish gh-pages antigravity.qmd 
