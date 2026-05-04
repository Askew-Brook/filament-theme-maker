# Filament v5 Vendor CSS Source Map

Read these files before writing overrides. Filament source CSS is readable and uses Tailwind `@apply`; prefer source files over compiled `dist/theme.css`.

## Project Theme Entry

- Find active panel providers under `app/Providers/Filament/*PanelProvider.php`.
- Find the active theme file from each panel provider's `->viteTheme()` call. Common examples include `resources/css/filament/admin/theme.css` and `resources/css/filament/{panel}/theme.css`.
- Theme files usually import `vendor/filament/filament/resources/css/theme.css`, then project-specific variants or overrides.
- Keep `@source` entries current for every PHP/Blade path that contains theme class names, commonly `app/Filament/**/*` and `resources/views/filament/**/*`.

## Override Strategy

1. Use `@theme` custom properties for token-level colors, radii, spacing, and fonts.
2. Match the exact vendor selector after the import when ordinary cascade is enough.
3. Scope with a stable parent such as `.fi-body .fi-header` for slightly higher specificity.
4. Use `!important` only when the vendor rule uses an important utility or an inherited custom property/ring variable cannot otherwise be neutralized.

Audit every vendor `@apply` utility on the selector. If vendor sets padding, margin, radius, gap, ring, shadow, display, or width and the override does not neutralize it, the old value can leak through.

## Common Tailwind Variable Gotchas

- Ring utilities may require direct variable overrides: `--tw-ring-color`, `--tw-ring-shadow`, `--tw-ring-offset-color`, `--tw-ring-offset-shadow`.
- Shadow utilities may require `box-shadow: none` plus `--tw-shadow: 0 0 #0000`.
- Dark-mode utilities only apply under `.dark`; if a panel has `->darkMode(false)`, do not spend time tuning dark-only selectors unless preparing reusable theme work.
- `.fi-main` has responsive padding from vendor: `px-4 md:px-6 lg:px-8`. Edge-to-edge content must account for all breakpoints.
- `.fi-page-header-main-ctn` carries page header/content vertical rhythm.
- `.fi-topbar-ctn` is sticky and layered; inspect z-index before changing overlays or dropdowns.

## Panel Shell CSS

| Surface | Source file | Core selectors |
| --- | --- | --- |
| Base/dark root | `vendor/filament/filament/resources/css/base.css` | `:root.dark`, base panel variables |
| Layout/body | `vendor/filament/filament/resources/css/components/layout.css` | `.fi-body`, `.fi-layout`, `.fi-main-ctn`, `.fi-main`, `.fi-simple-main` |
| Page wrapper | `vendor/filament/filament/resources/css/components/page.css` | `.fi-page`, `.fi-page-header-main-ctn`, `.fi-page-content`, `.fi-page-main` |
| Header | `vendor/filament/filament/resources/css/components/header.css` | `.fi-header`, `.fi-header-heading`, `.fi-header-subheading`, `.fi-header-actions-ctn` |
| Topbar | `vendor/filament/filament/resources/css/components/topbar.css` | `.fi-topbar-ctn`, `.fi-topbar`, `.fi-topbar-start`, `.fi-topbar-end`, `.fi-topbar-item-btn`, `.fi-topbar-item.fi-active` |
| Sidebar | `vendor/filament/filament/resources/css/components/sidebar.css` | `.fi-sidebar`, `.fi-sidebar-header`, `.fi-sidebar-nav`, `.fi-sidebar-group`, `.fi-sidebar-item`, `.fi-sidebar-item-btn` |
| Global search | `vendor/filament/filament/resources/css/components/global-search.css` | `.fi-global-search-*` |
| User menu | `vendor/filament/filament/resources/css/components/user-menu.css` | `.fi-user-menu-*`, scoped topbar/sidebar trigger rules |
| Theme switcher | `vendor/filament/filament/resources/css/components/theme-switcher.css` | `.fi-theme-switcher` |
| Tenant menu | `vendor/filament/filament/resources/css/components/tenant-menu.css` | `.fi-tenant-menu` |
| Logo | `vendor/filament/filament/resources/css/components/logo.css` | `.fi-logo` |
| Account widget | `vendor/filament/filament/resources/css/widgets/account-widget.css` | `.fi-wi-account` |
| Filament info widget | `vendor/filament/filament/resources/css/widgets/filament-info-widget.css` | `.fi-wi-filament-info` |

## Support Components CSS

| Surface | Source file | Core selectors |
| --- | --- | --- |
| Avatar | `vendor/filament/support/resources/css/components/avatar.css` | `.fi-avatar`, `.fi-circular`, `.fi-size-*` |
| Badge | `vendor/filament/support/resources/css/components/badge.css` | `.fi-badge`, `.fi-badge-label-ctn`, `.fi-badge-delete-btn` |
| Breadcrumbs | `vendor/filament/support/resources/css/components/breadcrumbs.css` | `.fi-breadcrumbs`, `.fi-breadcrumbs-item-*` |
| Button | `vendor/filament/support/resources/css/components/button.css` | `.fi-btn`, `.fi-btn-badge-ctn`, `.fi-outlined`, `.fi-processing` |
| Callout | `vendor/filament/support/resources/css/components/callout.css` | `.fi-callout`, `.fi-callout-*` |
| Dropdown | `vendor/filament/support/resources/css/components/dropdown/index.css`, `header.css`, `list/index.css`, `list/item.css` | `.fi-dropdown`, `.fi-dropdown-panel`, `.fi-dropdown-list-item` |
| Empty state | `vendor/filament/support/resources/css/components/empty-state.css` | `.fi-empty-state`, `.fi-empty-state-*` |
| Fieldset | `vendor/filament/support/resources/css/components/fieldset.css` | `.fi-fieldset`, `.fi-fieldset-*` |
| Grid | `vendor/filament/support/resources/css/components/grid.css` | `.fi-grid` |
| Icon | `vendor/filament/support/resources/css/components/icon.css` | `.fi-icon`, color/size hooks |
| Icon button | `vendor/filament/support/resources/css/components/icon-button.css` | `.fi-icon-btn`, `.fi-icon-btn-badge-ctn` |
| Checkbox | `vendor/filament/support/resources/css/components/input/checkbox.css` | `.fi-checkbox-input`, `.fi-valid`, `.fi-invalid` |
| Input | `vendor/filament/support/resources/css/components/input/index.css` | `.fi-input`, `.fi-input-has-inline-*` |
| Input wrapper | `vendor/filament/support/resources/css/components/input/wrapper.css` | `.fi-input-wrp`, `.fi-input-wrp-prefix`, `.fi-input-wrp-suffix`, `.fi-invalid`, `.fi-disabled` |
| Select | `vendor/filament/support/resources/css/components/input/select.css` | `.fi-select-input` |
| Radio | `vendor/filament/support/resources/css/components/input/radio.css` | `.fi-radio-input` |
| Link | `vendor/filament/support/resources/css/components/link.css` | `.fi-link`, `.fi-link-badge-ctn` |
| Loading | `vendor/filament/support/resources/css/components/loading-indicator.css` | `.fi-loading-indicator` |
| Modal | `vendor/filament/support/resources/css/components/modal.css` | `.fi-modal`, `.fi-modal-window`, `.fi-modal-header`, `.fi-modal-footer`, `.fi-modal-slide-over` |
| Pagination | `vendor/filament/support/resources/css/components/pagination.css` | `.fi-pagination`, `.fi-pagination-item-btn`, `.fi-active`, `.fi-disabled` |
| Section | `vendor/filament/support/resources/css/components/section.css` | `.fi-section`, `.fi-section-header`, `.fi-section-content`, `.fi-section-footer` |
| Tabs | `vendor/filament/support/resources/css/components/tabs.css` | `.fi-tabs`, `.fi-tabs-item`, `.fi-active`, `.fi-vertical` |
| Toggle | `vendor/filament/support/resources/css/components/toggle.css` | `.fi-toggle` |

## Tables CSS

| Surface | Source file | Core selectors |
| --- | --- | --- |
| Container | `vendor/filament/tables/resources/css/container.css` | `.fi-ta-ctn` |
| Content/table | `vendor/filament/tables/resources/css/content.css`, `table.css` | `.fi-ta-content`, `.fi-ta`, `.fi-ta-table` |
| Rows/cells | `vendor/filament/tables/resources/css/row.css`, `cell.css`, `header-cell.css` | `.fi-ta-row`, `.fi-ta-cell`, `.fi-ta-header-cell` |
| Actions | `vendor/filament/tables/resources/css/actions.css` | `.fi-ta-actions` |
| Empty state | `vendor/filament/tables/resources/css/empty-state.css` | `.fi-ta-empty-state` |
| Column manager | `vendor/filament/tables/resources/css/column-manager.css` | `.fi-ta-col-manager` |
| Columns | `vendor/filament/tables/resources/css/columns/*.css` | `.fi-ta-text`, `.fi-ta-icon`, `.fi-ta-image`, `.fi-ta-checkbox`, `.fi-ta-color`, `.fi-ta-select`, `.fi-ta-toggle`, `.fi-ta-text-input` |
| Column layouts | `vendor/filament/tables/resources/css/columns/layout/*.css` | grid, panel, split, stack table layouts |
| Summaries | `vendor/filament/tables/resources/css/columns/summaries/*.css` | summary text/icon/count/range/value selectors |

## Forms CSS

| Surface | Source file | Core selectors |
| --- | --- | --- |
| Field wrapper | `vendor/filament/forms/resources/css/components/field.css` | `.fi-fo-field`, `.fi-fo-field-label-*`, `.fi-fo-field-content-*`, error list/message |
| Builder | `vendor/filament/forms/resources/css/components/builder.css` | `.fi-fo-builder` |
| Repeater | `vendor/filament/forms/resources/css/components/repeater.css` | `.fi-fo-repeater` |
| Rich editor | `vendor/filament/forms/resources/css/components/rich-editor.css` | `.fi-fo-rich-editor` |
| Markdown editor | `vendor/filament/forms/resources/css/components/markdown-editor.css` | `.fi-fo-markdown-editor` |
| Select | `vendor/filament/forms/resources/css/components/select.css` | `.fi-fo-select` |
| Date/time picker | `vendor/filament/forms/resources/css/components/date-time-picker.css` | `.fi-fo-date-time-picker` |
| File upload | `vendor/filament/forms/resources/css/components/file-upload.css`, `file-upload/filepond-plugin-media-preview.css` | `.fi-fo-file-upload`, FilePond preview hooks |
| Color picker | `vendor/filament/forms/resources/css/components/color-picker.css` | `.fi-fo-color-picker` |
| Tags input | `vendor/filament/forms/resources/css/components/tags-input.css` | `.fi-fo-tags-input` |
| Text input | `vendor/filament/forms/resources/css/components/text-input.css` | `.fi-fo-text-input` |
| Textarea | `vendor/filament/forms/resources/css/components/textarea.css` | `.fi-fo-textarea` |
| Toggle buttons | `vendor/filament/forms/resources/css/components/toggle-buttons.css` | `.fi-fo-toggle-btns` |
| Checkbox list | `vendor/filament/forms/resources/css/components/checkbox-list.css` | `.fi-fo-checkbox-list` |
| Radio | `vendor/filament/forms/resources/css/components/radio.css` | `.fi-fo-radio` |
| Key value | `vendor/filament/forms/resources/css/components/key-value.css` | `.fi-fo-key-value` |
| Slider | `vendor/filament/forms/resources/css/components/slider.css` | `.fi-fo-slider` |
| Code editor | `vendor/filament/forms/resources/css/components/code-editor.css` | `.fi-fo-code-editor` |

## Schemas, Infolists, Widgets, Notifications, Actions

| Package | Source files | Core selectors |
| --- | --- | --- |
| Schemas | `vendor/filament/schemas/resources/css/schema.css`, `components/*.css` | `.fi-sc`, `.fi-sc-section`, `.fi-sc-tabs`, `.fi-sc-wizard`, `.fi-sc-actions`, `.fi-sc-text`, `.fi-sc-fused-group`, `.fi-sc-flex` |
| Infolists | `vendor/filament/infolists/resources/css/components/*.css` | `.fi-in-entry-wrp`, `.fi-in-text`, `.fi-in-icon`, `.fi-in-image`, `.fi-in-color`, `.fi-in-code`, `.fi-in-key-value`, `.fi-in-repeatable` |
| Widgets | `vendor/filament/widgets/resources/css/*.css` | `.fi-wi`, `.fi-wi-stats-overview`, `.fi-wi-stats-overview-stat`, `.fi-wi-chart` |
| Notifications | `vendor/filament/notifications/resources/css/*.css` | `.fi-no`, `.fi-no-notification`, `.fi-no-database`, `.fi-no-notification-read-ctn`, `.fi-no-notification-unread-ctn` |
| Actions | `vendor/filament/actions/resources/css/actions.css` | `.fi-ac` |

## High-Value Defaults To Check First

- `.fi-body`: gray background, text color, antialiasing.
- `.fi-main`: max width and horizontal padding.
- `.fi-topbar`: height, background, shadow/ring, sticky container.
- `.fi-sidebar`: width, background, transform states, nav gaps.
- `.fi-header-heading` and `.fi-header-subheading`: type scale and color.
- `.fi-section`, `.fi-ta-ctn`, `.fi-input-wrp`, `.fi-dropdown-panel`, `.fi-modal-window`: border, radius, shadow, and spacing.
- `.fi-btn`, `.fi-icon-btn`, `.fi-badge`, `.fi-link`: color maps, focus/hover/disabled states.
