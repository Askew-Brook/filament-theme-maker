# Filament Theme Audit Checklist

Use this before editing or approving a Filament theme.

## Discovery

- Confirm versions with Laravel Boost `application-info`.
- Use Laravel Boost `search-docs` for `components`, `styling colors`, `css hooks`, and any package surface you will touch.
- Fetch the official docs index from `https://filamentphp.com/docs/llms.txt`.
- Open the exact docs pages from the index. For v5 components, use `https://filamentphp.com/docs/5.x/components/<slug>.md`.
- Inspect local vendor views/classes fully. Do not copy assumptions from older Filament versions.

## Theme Entry Points

- Panel provider: inspect `->viteTheme()`, `->colors()`, `->darkMode()`, `->sidebarWidth()`, render hooks, custom login page, discovered pages/resources/widgets.
- Theme CSS: inspect imports, `@source` entries, CSS layers, theme variants, and any `fi-*` overrides.
- App chrome: inspect topbar, sidebar, global search, user menu, page header, page content gap, simple pages, auth pages, breadcrumbs, resource pages.
- Custom render hooks: inspect any Blade rendered into `HEAD_START`, topbar, global search, sidebar, or page hooks.

## CSS Hook Rules

- Prefer hook classes beginning with `fi-`.
- Use broad stable hooks first: `.fi-body`, `.fi-main`, `.fi-topbar`, `.fi-sidebar`, `.fi-page-content`, `.fi-section`, `.fi-btn`, `.fi-input-wrp`, `.fi-modal-window`, `.fi-ta-ctn`.
- Avoid styling anonymous deep descendants unless the vendor view exposes no hook and the risk is accepted.
- Avoid publishing vendor Blade views. If publishing is unavoidable, pin Filament versions and test every upgrade manually.
- Keep `!important` rare and scoped to one exact hook where ordinary cascade cannot win.

## Palette And Contrast

- Register complete `50,100,200,300,400,500,600,700,800,900,950` shade maps for every color.
- Check `primary`, `gray`, `info`, `success`, `warning`, `danger`.
- Include pale/warm colors in button tests because Filament may choose dark text on lighter backgrounds for accessibility.
- Inspect `getColorMap()` implementations for actual slot names and contrast logic.
- Verify text color, icon-only color, hover color, disabled state, focus ring, and dark-mode output when dark mode is enabled.

## Component State Coverage

- Avatar: all standard sizes, custom size, circular/square.
- Badge: colors, sizes, icon before/after, link, disabled, tooltip, delete button.
- Button: colors, sizes, solid/outlined, anchor, icon before/after, badge, disabled, tooltip, hidden-label responsive state, group.
- Breadcrumbs: linked ancestors and terminal item.
- Callout: all colors, no icon, heading-only, description, controls, footer, custom icon color/size.
- Checkbox: checked, unchecked, invalid, disabled.
- Dropdown: multiple placements/widths, header, list, colored items, icon colors, badges, image, disabled, anchor.
- Empty state: contained/uncontained, compact, icon colors/sizes, footer action.
- Fieldset: contained/uncontained, required, hidden label, nested fields.
- Icon button: colors, sizes, badge, anchor, disabled, tooltip, accessible label.
- Input/select/wrapper: affixes, icons, inline affixes, valid/invalid, disabled, select.
- Link: colors, sizes, weights, icons, badge, disabled, button tag.
- Loading indicator: sizes, colors, in-button and standalone.
- Modal: default, slide-over, sticky header/footer, widths, alignment, icon colors, close restrictions.
- Pagination: length-aware, simple if app uses it, first/last links, active/disabled items, records-per-page select.
- Section: default, compact, uncontained, aside, content-before, collapsible, collapsed, divided, secondary, after-header, footer.
- Tabs: contained/uncontained, vertical/horizontal, active, icon before/after, badges, anchor.

## Package Surface Coverage

- Actions: trigger variants, action groups, destructive color, confirmation modal, modal footer actions.
- Forms: field wrapper, validation messages, helper text, labels, inline labels, repeaters, rich editor/file upload if used.
- Infolists: text/icon/image/color entries, repeatable entries, key-value entries, placeholders.
- Schemas: section/tabs/wizard/callout/empty-state/layout primes.
- Tables: header, filters, search, rows, hover, striped/grouped rows if used, selected rows, empty state, actions, summaries, pagination.
- Widgets: widget card/shell, stats overview values/descriptions/icons/charts, chart colors, loading state.
- Notifications: inline and toast stack, database notification slide-over if enabled.

## Verification

- Run `vendor/bin/pint --dirty --format agent` after PHP edits.
- Run a minimal test: `php artisan test --compact <file>` or `--filter=<name>`.
- Use Laravel Boost `get-absolute-url` before sharing a URL.
- Use `browser-logs` only for recent browser errors after manual page inspection.
- If the theme CSS changed but the UI does not reflect it, remind the user that Vite may need `npm run build`, `npm run dev`, or the project dev command.

## Common Failure Modes

- Missing `@source` entries for new Blade/PHP files, causing Tailwind classes to be purged.
- Dynamic class construction that Tailwind cannot see.
- Styling only resource pages while auth/simple pages remain default.
- Overriding radius/spacing on `.fi-section` but missing `.fi-sc-section`, `.fi-ta-ctn`, `.fi-modal-window`, `.fi-dropdown-panel`, or `.fi-input-wrp`.
- Testing only `primary`, while `warning` and pale palettes choose different text/background shade paths.
- Forgetting package-generated surfaces such as action modals, table filters, rich editor attachments, database notifications, and widget stat descriptions.
