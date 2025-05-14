# Deploy to GH-Pages Using Minimalify

<img src="./logo/logo-dark.png" alt="Minimalify Logo" width="100" />

<br />

[![npm version](https://img.shields.io/npm/v/minimalify.svg)](https://www.npmjs.com/package/minimalify)
[![download](https://img.shields.io/npm/dw/minimalify.svg)](https://www.npmjs.com/package/minimalify)
[![License: Apache](https://img.shields.io/badge/License-Apache-blue.svg)](LICENSE)

Minimalify is a zero-dependency CLI/library for building blazing-fast, static HTML/CSS/JS sites with reusable components. Drop in your source, define a tiny config, run minimalify build, and get a fully inlined, minified build/ folder ready for deployment.
Read more about Minimalify [here](https://therahulagarwal.com/minimalify/)

A composite GitHub Action to:

- Install deps (npm, yarn, pnpm, bun, or Deno)  
- Cache `node_modules`  
- Run lint & format (optional)  
- Build (`run build` or Deno script)  
- Read `outDir` from JSON or JS config (`outDir` key; default `dist`)  
- Push output to a specified branch (default `gh-pages`)  
- Enable GitHub Pages on that branch

## Inputs

| Name             | Required | Default  | Description                                            |
|------------------|----------|----------|--------------------------------------------------------|
| `package-manager`| no       | `npm`    | `npm`/`yarn`/`pnpm`/`bun`/`deno`                      |
| `node-version`   | no       | `16`     | Node.js version (ignored for Deno)                     |
| `cache-deps`     | no       | `true`   | Cache dependencies?                                    |
| `precheck`       | no       | `true`   | Run lint & format?                                     |
| `workdir`        | no       | `.`      | Working directory for install/build                    |
| `branch`         | no       | `gh-pages`| Branch to deploy to                                   |
| `config-file`    | no       | `minimalify.config.json`| JSON or JS file exporting `{ outDir }`            |
| `github-token`   | yes      | —        | Token with repo permissions                            |

## Example

```yaml
uses: ragarwalll/deploy-with-minimalify@v1
with:
  package-manager: pnpm
  node-version: '20'
  cache-deps: true
  precheck: true
  workdir: './'
  branch: gh-pages
  config-file: './minimalify.config.[js|json]'
  github-token: ${{ secrets.GITHUB_TOKEN }}
```

## License

This project is licensed under the Apache License 2.0. See the [LICENSE](LICENSE) file for details.