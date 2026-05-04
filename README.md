# Filament Theme Maker

An Agent Skill for designing, auditing, and hardening complete Filament v5 panel themes.

This repository is compatible with the open Agent Skills format and can be installed with the `skills` CLI used by [skills.sh](https://skills.sh). The skill pushes an agent to inspect installed Filament vendor files, source CSS, Blade views, semantic `fi-*` class hooks, and package surfaces before writing theme overrides.

## What It Covers

- Filament v5 theme audit workflow.
- Vendor CSS source map for panel, support, forms, schemas, tables, infolists, widgets, actions, and notifications.
- Semantic class map for component-level theme fixes such as buttons, modals, table rows, sidebars, forms, and global search.
- Component surface checklist for full theme coverage.
- Practical override guidance for `@theme`, CSS hooks, Tailwind `@apply`, ring variables, shadow variables, specificity, and `@source` coverage.

## What It Does Not Include

- Any application-specific Filament pages or implementation code.
- Published vendor source from Filament.
- A finished theme.
- Any affiliation with Filament, Laravel, or their maintainers.

## Install With Skills CLI

After this repository is published, install it with:

```bash
npx skills add owner/filament-theme-maker --skill filament-theme-maker
```

To install locally before publishing:

```bash
npx skills add . --skill filament-theme-maker
```

For Codex specifically:

```bash
npx skills add . --skill filament-theme-maker --agent codex
```

## Manual Install

Copy the skill folder into either your global Codex skills directory:

```bash
cp -R skills/filament-theme-maker "$CODEX_HOME/skills/filament-theme-maker"
```

Or into a project-local skills directory:

```bash
mkdir -p .agents/skills
cp -R skills/filament-theme-maker .agents/skills/filament-theme-maker
```

Then use it in a Filament project:

```text
Use $filament-theme-maker to audit this Filament panel theme and implement missing coverage.
```

## Repository Layout

```text
skills/
  filament-theme-maker/
    SKILL.md
    metadata.json
    agents/openai.yaml
    references/
      class-hierarchy.yaml
      component-surface-map.md
      css-source-map.md
      semantic-class-map.md
      theme-audit-checklist.md
```

## Requirements

The skill expects to run inside a Laravel project with Filament v5 installed. It deliberately treats local `vendor/filament/**` files as the source of truth, because theme hooks, source CSS, and component markup can change between Filament releases.

## Versioning

The skill version lives in `skills/filament-theme-maker/SKILL.md`:

```yaml
metadata:
  version: "1.0.0"
```

When publishing a release, update that metadata value and tag the repository with the same semver:

```bash
git tag v1.0.0
git push origin main --tags
```

Users can install latest from the default branch:

```bash
npx skills add owner/filament-theme-maker --skill filament-theme-maker
```

Or pin to a release tag:

```bash
npx skills add owner/filament-theme-maker#v1.0.0 --skill filament-theme-maker
```

## License

MIT-0. See [LICENSE](LICENSE).
