---
name: filament-theme-maker
description: Design, audit, and harden complete Filament v5 panel themes by reading vendor CSS, Blade views, and view component classes before styling. Use when creating or reviewing Filament theme CSS, debugging why a theme override does not apply, mapping fi-* CSS hooks, validating semantic color palettes, or ensuring Forms, Infolists, Schemas, Tables, Widgets, Actions, Notifications, and Support Blade components are fully themed.
license: MIT-0
metadata:
  author: askewbrook
  version: "1.0.0"
  environment: Laravel application with Filament v5 installed and local vendor files available.
---

# Filament Theme Maker

## Operating Rule

Verify the installed Filament version and local vendor files before changing theme CSS. Treat upstream docs as the discovery map and local `vendor/filament/**` as the source of truth for CSS `@apply` rules, props, CSS hooks, and rendered markup.

## Workflow

1. Run Laravel Boost `application-info` and `search-docs` for Filament styling, components, package surfaces, and tests before editing.
2. Fetch `https://filamentphp.com/docs/llms.txt` and open the relevant `5.x` component, styling, and navigation docs from that index.
3. Inspect the matching local vendor Blade views and PHP view component classes completely before deciding coverage.
4. Inspect the relevant vendor CSS source file before writing an override; Filament source CSS uses readable Tailwind `@apply`.
5. Read `references/component-surface-map.md` when building or auditing full component surface coverage.
6. Read `references/css-source-map.md` before changing CSS selectors, spacing, radii, rings, shadows, or layout.
7. Read `references/semantic-class-map.md` when the task names a specific surface or class, such as "button", "modal footer", "table row", or "sidebar item".
8. Read `references/class-hierarchy.yaml` when selector nesting, parent state, or sibling structure matters.
9. Read `references/theme-audit-checklist.md` before editing theme CSS or finalizing a theme review.
10. Prefer CSS hooks and CSS variables over publishing vendor views. If a hook is missing, call out the gap instead of targeting unstable deep markup.
11. Theme against real panel surfaces first: resources, simple/auth pages, tables, widgets, forms, infolists, notifications, and application chrome.
12. Run the smallest meaningful Pest/HTTP test that proves affected theme surfaces or asset registration still render, then run Pint for PHP edits.

## Coverage Standard

A theme is not complete until these surfaces have been seen in the target theme:

- Semantic palettes: `primary`, `gray`, `info`, `success`, `warning`, `danger`, all `50..950` shades.
- Interactive primitives: buttons, icon buttons, links, dropdown items, badges, key disabled/loading/tooltip/badge states.
- Field primitives: input wrapper affixes, text input, select, checkbox, invalid, disabled, inline prefix/suffix.
- Layout primitives: section, fieldset, tabs, empty state, callout, modal, slide-over, pagination.
- Package surfaces: action groups/modals, form field wrappers, schema sections/tabs/callouts/empty states, infolist entries, table container/rows/columns/filters/actions/pagination, widget shells/stats/charts, notifications.
- Application chrome: panel body, topbar, sidebar, page header, breadcrumbs, resource pages, simple auth pages, global search, user menu, theme switcher or other render hooks.

## Implementation Rules

- Locate the active project theme path from the panel provider `->viteTheme()`; do not assume a fixed path such as `resources/css/filament/admin/theme.css`.
- Start with `@theme` variables when the target is a token, then use matching selectors, then scoped specificity, then `!important` only as a last resort.
- Cross-check every utility in the vendor `@apply` line against the override. Common leakers are `mx-auto`, `p-*`, `rounded-*`, `gap-*`, `shadow-*`, and `ring-*`.
- Override Tailwind ring variables directly when needed: `--tw-ring-color`, `--tw-ring-shadow`, `--tw-ring-offset-color`, and related variables.
- Use `@source` coverage for every Blade/PHP file that contains theme class names.
- Avoid dynamic Tailwind class construction unless every generated class appears literally somewhere in a scanned source file.
- Keep product UI restrained: no decorative gradients, glass effects, oversized radii, or marketing-style hero sections on admin pages.
- Never rely on dark-mode classes unless the panel enables dark mode or the request explicitly includes dark-mode coverage.
- Do not create broad visual-regression suites by default. Add one focused render/smoke test when changing route, page, or theme asset registration.

## References

- `references/component-surface-map.md`: documented components, vendor files, important props, hook classes, and states to include.
- `references/css-source-map.md`: vendor CSS files, selectors, common defaults, and override strategy.
- `references/semantic-class-map.md`: component-by-component `fi-*` class descriptions and override target guidance.
- `references/class-hierarchy.yaml`: DOM/class hierarchy for panel shell, simple layout, and shared components.
- `references/theme-audit-checklist.md`: practical audit workflow, CSS-hook guidance, color-map notes, and final verification checklist.
