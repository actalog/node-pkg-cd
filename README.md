# Node package CD

GitHub Action to automate the Continuous Deployment (CD) process for Node.js packages to the npm registry.

## Features

- Automatically sets up the desired Node.js version.
- Installs dependencies using `npm ci` or `npm install`.
- Builds the package if a `build` script exists in `package.json`.
- Prepares the package for publishing.
- Publishes the package to the npm registry.

## Inputs

| Name               | Description                                        | Required | Default                      |
|--------------------|----------------------------------------------------|----------|------------------------------|
| `node-auth-token`  | npm authentication token                           | Yes      | N/A                          |
| `node-version`     | Node.js version to use                             | No       | `20`                         |
| `registry-url`     | npm registry URL                                   | No       | `https://registry.npmjs.org` |

## Usage

Here's an example of how to use this action in a GitHub workflow:

```yaml
name: CD

on:
  push:
    branches:
      - main

jobs:
  node-pkg-cd:
    name: Node package CD
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actalog/node-pkg-cd@v1
        with:
          node-auth-token: ${{ secrets.NODE_AUTH_TOKEN }}
          node-version: 20
```

## License

This project is licensed under [The Unlicense](LICENSE).
