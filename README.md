# renovate-config

Repository with Renovate config shared across my repositories - I do not want to manage them one-by-one.

## Usage

Reference a preset from a repository's `renovate.json` via the `extends` field:

```json
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": ["github>vojtechmares/renovate-config"]
}
```

Referencing the repository without a preset name resolves to `default`. To use the `automerge` preset:

```json
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": ["github>vojtechmares/renovate-config:automerge"]
}
```

## Presets

### `default`

Base config extended by all other presets. Built on top of `config:recommended`.

- Timezone set to `Europe/Prague`.
- Updates scheduled daily, after 5am and before 6am.
- Semantic commit messages enabled.
- PRs created once status checks are no longer pending (`not-pending`).
- Minimum release age of 14 days before an update is proposed.
- All PRs labelled `dependencies`.

### `automerge`

Extends `default` and enables automerge.

- Automerge enabled for minor, patch and lock file maintenance updates.
- Automerge strategy is `rebase`, performed via PRs.
- Major version updates are **not** automerged.
