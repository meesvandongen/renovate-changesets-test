# renovate-changesets-test

Reproduction for the `changesets` post-update option in [meesvandongen/renovate#1](https://github.com/meesvandongen/renovate/pull/1).

Run the **Renovate** workflow to let Renovate from that branch update this pnpm monorepo.
Each Renovate PR should contain changesets like this:

| Package | Setup | Expected changeset |
| --- | --- | --- |
| `@test/lib-a`, `@test/lib-e` | `ms` in `dependencies` | `patch`, sharing one changeset |
| `@test/lib-f` | `ms` and `semver` in `dependencies` | `patch`, in its own changeset (`ms and semver` group) |
| `@test/lib-b` | `react` in `peerDependencies`, widened by default | `patch` |
| `@test/lib-c` | `vue` in `peerDependencies`, replaced by a package rule | `major` |
| `@test/lib-d` | `is-number` from the pnpm catalog | `patch` |
| `@test/app` | private | none |
| `@test/ignored` | in the changesets `ignore` list | none |
| `@test/dev-only` | `semver` in `devDependencies` | none |
