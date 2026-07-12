# Contributing

Thanks for helping improve `@qntx/tsconfig`.

## Prerequisites

- [Bun](https://bun.sh) (recommended)
- Node.js LTS (for `npm publish` in CI)

## Setup

```sh
bun install
```

`prepare` runs [Husky](https://typicode.github.io/husky/) so git hooks under `.husky/` are registered.

## Project layout

```text
configs/                 # published package files (source of truth)
example/                 # smoke consumer (relative extends)
.github/workflows/       # CI + publish
```

Only the `configs/` directory is published (`package.json` → `files`).

## Scripts

| Command             | Description                                                         |
| ------------------- | ------------------------------------------------------------------- |
| `bun run check`     | Install example deps and run `tsc --noEmit`                         |
| `bun run fmt`       | Format with [Oxfmt](https://oxc.rs/docs/guide/usage/formatter.html) |
| `bun run fmt:check` | Check formatting (used in CI)                                       |
| `bun run test`      | Alias of `check`                                                    |

## Making changes

1. Edit or add a file under `configs/` (JSONC is allowed; keep `$schema` / `display` consistent with peers).
2. Format and verify:

```sh
bun run fmt
bun run check
```

1. Update [README.md](./README.md) if you add a widely used config or change the public path convention.

### Commit messages

Use [Conventional Commits](https://www.conventionalcommits.org/):

```text
<type>(<scope>): <subject>
```

Examples:

```text
feat(configs): add node26 base
fix(configs): align node-lts with node24
docs: clarify extends path in README
ci: allow manual CI dispatch
```

Enforced locally by commitlint (`commit-msg`) and optionally `pre-commit` (`bun run check`).

## Release

Maintainers only.

- Bump `version` in `package.json`.
- Commit and push to the default branch.
- Tag and push (must match the version, e.g. `1.0.2` → `v1.0.2`):

```sh
git tag v1.0.2
git push origin v1.0.2
```

Pushing a `v*` tag runs **Publish @qntx/tsconfig** (OIDC [Trusted Publishing](https://docs.npmjs.com/trusted-publishers); no long-lived npm token).

Requirements:

- npm Trusted Publisher configured for this repo and `deploy.yml`
- GitHub repository **public** if using `npm publish --provenance`
- `package.json` `version` not already published

Emergency local publish (after `npm login`):

```sh
npm publish --access public
```

## CI

| Workflow | Trigger                                     |
| -------- | ------------------------------------------- |
| CI       | `push`, `pull_request`, `workflow_dispatch` |
| Publish  | `push` tags `v*`, `workflow_dispatch`       |

CI runs `fmt:check` and `check`.
