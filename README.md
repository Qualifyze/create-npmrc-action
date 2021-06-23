# create-npmrc-action

GitHub Action that creates an .npmrc file. Useful if you need access to private NPM packages.
This repository provides two actions:

1. `create`: Create an `.npmrc` file with the passed access token. This is required before installing private NPM packages.
2. `remove`: Remove the file created by the above action to make the access token is not leaked in subsequent workflow steps.

## Example usage:

```yml
on: [push]

jobs:
  install:
    runs-on: ubuntu-latest
    name: Install dependencies
    steps:
      - uses: actions/checkout@v2
      - name: Create .npmrc
        uses: Qualifyze/create-npmrc-action/create@main
        with:
          token: ${{ secrets.NPM_TOKEN }}
      - name: Install private NPM packages
        run: npm ci
      - name: Remove .npmrc
        uses: Qualifyze/create-npmrc-action/remove@main
```
