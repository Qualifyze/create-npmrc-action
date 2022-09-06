# create-npmrc-action

## Deprecated

Instead, please use `registry-url` parameter of the standard GitHub action `setup-node`:

```yml
on: push

jobs:
  install:
    runs-on: ubuntu-latest
    name: Install dependencies
    steps:
      - name: Check out repository
        uses: actions/checkout@v2

      - name: Set up Node.js
        uses: actions/setup-node@v2
        with:
          node-version: 16.16.0
          registry-url: https://registry.npmjs.org
          cache: npm

      - name: Install private NPM packages
        run: npm ci
        env:
          NODE_AUTH_TOKEN: ${{ secrets.NPM_TOKEN }}
```
