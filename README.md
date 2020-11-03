# Let's resize some images!

We will use [Image Action](https://github.com/marketplace/actions/image-actions) to resize an image in a pull request.

Steps:
1. Create a .github/workflows/calibreapp-image-actions.yml file in your repository with the following configuration:

```
name: Compress Images
on:
  pull_request:
    paths:
      - '**.jpg'
      - '**.jpeg'
      - '**.png'
      - '**.webp'
jobs:
  build:
    if: github.event.pull_request.head.repo.full_name == github.repository
    name: calibreapp/image-actions
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Repo
        uses: actions/checkout@master

      - name: Compress Images
        uses: calibreapp/image-actions@master
        with:
          githubToken: ${{ secrets.GITHUB_TOKEN }}
```
2. Upload an image (LARGE image) and open a pull request
