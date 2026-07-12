# @qntx/tsconfig

Shared TSConfig configs for QuantX projects. One package, many configs.

Forked and reworked from [tsconfig/bases](https://github.com/tsconfig/bases).

## Install

```sh
npm install --save-dev @qntx/tsconfig
# or
bun add -d @qntx/tsconfig
```

## Usage

```json
{
  "extends": "@qntx/tsconfig/configs/node-lts.json"
}
```

Combine multiple configs (TypeScript 5.0+):

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

## Available configs

All files under [`configs/`](./configs). Common ones:

| Config | Path |
| ------ | ---- |
| Recommended | `@qntx/tsconfig/configs/recommended.json` |
| Strictest | `@qntx/tsconfig/configs/strictest.json` |
| Node LTS | `@qntx/tsconfig/configs/node-lts.json` |
| Node 24 | `@qntx/tsconfig/configs/node24.json` |
| Bun | `@qntx/tsconfig/configs/bun.json` |
| Next.js | `@qntx/tsconfig/configs/next.json` |
| Vite React | `@qntx/tsconfig/configs/vite-react.json` |

`node-ts` is meant to be combined with a Node config (TypeScript 5.8+):

```json
{
  "extends": [
    "@qntx/tsconfig/configs/node22.json",
    "@qntx/tsconfig/configs/node-ts.json"
  ]
}
```

## Development

Requires [Bun](https://bun.sh).

```sh
bun install   # also installs husky commit-msg hook
bun run check
```

Commits follow [Conventional Commits](https://www.conventionalcommits.org/)
(enforced by commitlint + husky).

Publish:

1. Bump `version` in `package.json` (e.g. `1.0.1`)
2. Commit and push
3. Create and push a matching tag:

```sh
git tag v1.0.1
git push origin v1.0.1
```

Pushing `v*` tags runs **Publish @qntx/tsconfig** automatically (OIDC Trusted Publishing, no npm token).

Local first publish (already done for `1.0.0`) or emergency:

```sh
npm publish --access public
```

### Layout

```text
configs/   # published package files
example/   # local smoke example (relative extends)
```
