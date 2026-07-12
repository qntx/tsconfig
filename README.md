# @qntx/tsconfig

Shared [TypeScript](https://www.typescriptlang.org/) base configs for QuantX projects.

One package, many ready-to-extend configs under `configs/`. Forked and reworked from
[tsconfig/bases](https://github.com/tsconfig/bases).

## Install

```sh
npm install --save-dev @qntx/tsconfig
```

```sh
pnpm add -D @qntx/tsconfig
```

```sh
bun add -d @qntx/tsconfig
```

```sh
yarn add -D @qntx/tsconfig
```

## Usage

Point `extends` at a config file in this package:

```json
{
  "extends": "@qntx/tsconfig/configs/node-lts.json"
}
```

Compose multiple bases (TypeScript 5.0+):

```json
{
  "extends": [
    "@qntx/tsconfig/configs/strictest.json",
    "@qntx/tsconfig/configs/node24.json"
  ]
}
```

Inspect the resolved config:

```sh
tsc --showConfig
```

### Paths

Configs ship as real files under the package root (no `exports` remapping). Always use:

```text
@qntx/tsconfig/configs/<name>.json
```

## Available configs

All configs live in [`configs/`](./configs). Common choices:

| Config | Path |
| --- | --- |
| Recommended | `@qntx/tsconfig/configs/recommended.json` |
| Strictest | `@qntx/tsconfig/configs/strictest.json` |
| Node LTS | `@qntx/tsconfig/configs/node-lts.json` |
| Node 24 | `@qntx/tsconfig/configs/node24.json` |
| Bun | `@qntx/tsconfig/configs/bun.json` |
| Next.js | `@qntx/tsconfig/configs/next.json` |
| Vite React | `@qntx/tsconfig/configs/vite-react.json` |

Also included: `node10`–`node26`, `node-ts`, `create-react-app`, `cypress`, `deno`,
`docusaurus`, `ember`, `nuxt`, `qjsengine`, `react-native`, `remix`, `svelte`, `taro`.

### `node-ts`

Requires TypeScript 5.8+. Combine with a Node base:

```json
{
  "extends": [
    "@qntx/tsconfig/configs/node22.json",
    "@qntx/tsconfig/configs/node-ts.json"
  ]
}
```

## Contributing

See [CONTRIBUTING.md](./CONTRIBUTING.md) for local setup, checks, commits, and release.

## License

Licensed under the MIT License ([LICENSE](./LICENSE) or <https://opensource.org/licenses/MIT>).

This project is derived from [tsconfig/bases](https://github.com/tsconfig/bases).
Unless you explicitly state otherwise, any contribution intentionally submitted for
inclusion in this project shall be under the MIT License, without additional terms or conditions.

---

<div align="center">

A **[QuantX](https://qntx.fun)** open-source project.

<a href="https://qntx.fun"><img alt="QuantX" width="369" src="https://raw.githubusercontent.com/qntx/.github/main/profile/qntx-banner.svg" /></a>

<!--prettier-ignore-->
Code is law. We write both.

</div>
