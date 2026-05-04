# Filament v5 Theme Component Surface Map

Use this map after checking the installed version and reading local vendor files. Paths below describe Filament v5 package structure; re-run `rg --files vendor/filament` after upgrades because package internals can move.

## Vendor Inspection Commands

- Docs index: `curl -Lsf https://filamentphp.com/docs/llms.txt`
- Component docs: `curl -Lsf https://filamentphp.com/docs/5.x/components/<slug>.md`
- Component props: `awk '/@props\\(\\[/{flag=1} flag{print} flag && /^\\]\\)/{flag=0}' vendor/filament/support/resources/views/components/<file>.blade.php`
- Hook scan: `rg -o "fi-[A-Za-z0-9:-]+" vendor/filament -g '*.blade.php' | sort -u`
- Color-map scan: `rg -n "function getColorMap|implements HasColor" vendor/filament -g '*.php'`

## Package Components

These are class-driven surfaces. Render them through Filament/Livewire APIs when building real UI, and audit them through existing real resources, widgets, forms, tables, actions, and simple/auth pages where possible.

| Docs slug | Surface | Inspect these files | Theme coverage |
| --- | --- | --- | --- |
| `components/action` | Actions, action groups, modals | `vendor/filament/actions/resources/views/components/group.blade.php`, `modals.blade.php`, `vendor/filament/support/resources/views/components/actions.blade.php` | trigger button/link/icon-button, grouped dropdown, modal, disabled, loading, destructive action, alignment, full-width action bar |
| `components/form` | Forms in Blade/Livewire | `vendor/filament/schemas/resources/views/components/form.blade.php`, `vendor/filament/forms/resources/views/components/*` | field wrapper, labels, help/error text, form actions, dense mode, inline labels, all field primitives used by the panel |
| `components/infolist` | Infolists | `vendor/filament/infolists/resources/views/components/entry-wrapper.blade.php`, `vendor/filament/infolists/src/View/Components/*` | entry labels, text/icon/image/color/key-value/repeatable entries, empty/placeholder values, columns |
| `components/notifications` | Toast/database notifications | `vendor/filament/notifications/resources/views/*.blade.php`, `vendor/filament/notifications/src/Notification.php` | success/warning/danger/info inline notifications, toast stack, database slide-over, close button, action buttons |
| `components/schema` | Schema layouts/primes | `vendor/filament/schemas/resources/views/components/*.blade.php` | grid, flex, fused group, section, tabs, wizard, callout, empty state, text, image, unordered list |
| `components/table` | Tables | `vendor/filament/tables/resources/views/**/*.blade.php` | container, header toolbar, search, filters, columns, badges, icons, row actions, bulk actions, grouped rows, summaries, empty state, pagination |
| `components/widget` | Widgets | `vendor/filament/widgets/resources/views/components/*.blade.php`, `vendor/filament/widgets/src/View/Components/*` | widget shell, stats overview, stat descriptions/icons/charts, chart widgets, responsive column spans |

## Support Blade Components

### Avatar

- Tag: `<x-filament::avatar />`
- Docs: `components/avatar`
- Vendor: `vendor/filament/support/resources/views/components/avatar.blade.php`
- Props: `circular`, `size`
- Hooks: `fi-avatar`, `fi-circular`, `fi-size-*`
- Cover: `sm`, `md`, `lg`, custom size class, circular and square, local broken-image fallback if the app may have missing avatars.

### Badge

- Tag: `<x-filament::badge>`
- Docs: `components/badge`
- Vendor: `vendor/filament/support/resources/views/components/badge.blade.php`, `BadgeComponent.php`
- Props: `color`, `deleteButton`, `disabled`, `href`, `icon`, `iconPosition`, `iconSize`, `keyBindings`, `loadingIndicator`, `size`, `tag`, `target`, `tooltip`, `type`
- Hooks: `fi-badge`, `fi-badge-label-ctn`, `fi-badge-label`, `fi-badge-delete-btn`, `fi-disabled`, `fi-size-*`
- Cover: every semantic color, `xs/sm/md/lg/xl`, icon before/after, link badge, disabled with tooltip, delete button, long text wrapping.

### Button and Button Group

- Tags: `<x-filament::button>`, `<x-filament::button.group>`
- Docs: `components/button`
- Vendor: `vendor/filament/support/resources/views/components/button/index.blade.php`, `button/group.blade.php`, `ButtonComponent.php`
- Props: `badge`, `badgeColor`, `badgeSize`, `color`, `disabled`, `form`, `href`, `icon`, `iconPosition`, `iconSize`, `keyBindings`, `labeledFrom`, `labelSrOnly`, `loadingIndicator`, `outlined`, `size`, `tag`, `target`, `tooltip`, `type`
- Hooks: `fi-btn`, `fi-btn-group`, `fi-btn-badge-ctn`, `fi-outlined`, `fi-processing`, `fi-disabled`, `fi-size-*`, `fi-labeled-from-*`
- Cover: solid and outlined for all colors, all sizes, anchor buttons, icon before/after, badge, disabled, tooltip, label-sr-only/labeled-from, grouped buttons.

### Breadcrumbs

- Tag: `<x-filament::breadcrumbs />`
- Docs: `components/breadcrumbs`
- Vendor: `vendor/filament/support/resources/views/components/breadcrumbs.blade.php`
- Props: `breadcrumbs`
- Hooks: `fi-breadcrumbs`, `fi-breadcrumbs-list`, `fi-breadcrumbs-item`, `fi-breadcrumbs-item-label`, `fi-breadcrumbs-item-separator`, `fi-ltr`, `fi-rtl`
- Cover: linked ancestors, terminal label, overflow/long labels, LTR and RTL separator if the app supports RTL.

### Callout

- Tag: `<x-filament::callout>`
- Docs: `components/callout`
- Vendor: `vendor/filament/support/resources/views/components/callout.blade.php`, `CalloutComponent.php`, `CalloutComponent/IconComponent.php`
- Props: `color`, `controls`, `description`, `footer`, `heading`, `icon`, `iconColor`, `iconSize`
- Hooks: `fi-callout`, `fi-callout-main`, `fi-callout-icon`, `fi-callout-text`, `fi-callout-heading`, `fi-callout-description`, `fi-callout-controls`, `fi-callout-footer`
- Cover: all colors, no icon, heading-only, description, controls slot, footer slot, custom icon color and size.

### Checkbox

- Tag: `<x-filament::input.checkbox />`
- Docs: `components/checkbox`
- Vendor: `vendor/filament/support/resources/views/components/input/checkbox.blade.php`
- Props: `valid`, `alpineValid`
- Hooks: `fi-checkbox-input`, `fi-valid`, `fi-invalid`
- Cover: checked, unchecked, invalid, disabled, focus ring, label adjacency.

### Dropdown

- Tags: `<x-filament::dropdown>`, `dropdown.header`, `dropdown.list`, `dropdown.list.item`
- Docs: `components/dropdown`
- Vendor: `vendor/filament/support/resources/views/components/dropdown/**/*.blade.php`, `DropdownComponent/HeaderComponent.php`, `DropdownComponent/ItemComponent.php`, `DropdownComponent/ItemComponent/IconComponent.php`
- Dropdown props: `availableHeight`, `availableWidth`, `flip`, `maxHeight`, `offset`, `placement`, `shift`, `size`, `sizePadding`, `teleport`, `trigger`, `width`
- Item props: `badge`, `badgeColor`, `badgeTooltip`, `color`, `disabled`, `href`, `icon`, `iconColor`, `image`, `keyBindings`, `loadingIndicator`, `tag`, `target`, `tooltip`
- Hooks: `fi-dropdown`, `fi-dropdown-trigger`, `fi-dropdown-panel`, `fi-dropdown-list`, `fi-dropdown-header`, `fi-dropdown-list-item`, `fi-dropdown-list-item-label`, `fi-dropdown-list-item-image`, `fi-dropdown-list-item-badge-placeholder`, `fi-width-*`, `fi-scrollable`
- Cover: placements, `xs/md` widths, max height scrolling, header, all item colors, disabled item, icon color, image item, badge item, anchor item.

### Empty State

- Tag: `<x-filament::empty-state>`
- Docs: `components/empty-state`
- Vendor: `vendor/filament/support/resources/views/components/empty-state.blade.php`
- Props: `compact`, `contained`, `description`, `footer`, `heading`, `headingTag`, `icon`, `iconColor`, `iconSize`
- Hooks: `fi-empty-state`, `fi-empty-state-not-contained`, `fi-compact`, `fi-empty-state-content`, `fi-empty-state-icon-bg`, `fi-empty-state-text-ctn`, `fi-empty-state-heading`, `fi-empty-state-description`, `fi-empty-state-footer`, `fi-color-*`
- Cover: contained/uncontained, compact, description, icon colors/sizes, footer actions.

### Fieldset

- Tag: `<x-filament::fieldset>`
- Docs: `components/fieldset`
- Vendor: `vendor/filament/support/resources/views/components/fieldset.blade.php`
- Props: `contained`, `label`, `labelHidden`, `required`
- Hooks: `fi-fieldset`, `fi-fieldset-not-contained`, `fi-fieldset-label-hidden`, `fi-fieldset-label-required-mark`
- Cover: contained/uncontained, required mark, hidden label, nested inputs and checkboxes.

### Icon Button

- Tag: `<x-filament::icon-button />`
- Docs: `components/icon-button`
- Vendor: `vendor/filament/support/resources/views/components/icon-button.blade.php`, `IconButtonComponent.php`
- Props: `badge`, `badgeColor`, `badgeSize`, `color`, `disabled`, `href`, `icon`, `iconSize`, `keyBindings`, `label`, `loadingIndicator`, `size`, `tag`, `target`, `tooltip`, `type`
- Hooks: `fi-icon-btn`, `fi-icon-btn-badge-ctn`, `fi-disabled`, `fi-size-*`
- Cover: all colors, all sizes, anchor, disabled, tooltip, badge, accessible label, focus/hover.

### Input and Select

- Tags: `<x-filament::input>`, `<x-filament::input.select>`
- Docs: `components/input`, `components/select`
- Vendor: `vendor/filament/support/resources/views/components/input/index.blade.php`, `input/select.blade.php`
- Props: `inlinePrefix`, `inlineSuffix`
- Hooks: `fi-input`, `fi-input-has-inline-prefix`, `fi-input-has-inline-suffix`, `fi-select-input`, `fi-select-input-has-inline-prefix`
- Cover: text, number, email, disabled, invalid via wrapper, inline prefix/suffix, long values, select with multiple options.

### Input Wrapper

- Tag: `<x-filament::input.wrapper>`
- Docs: `components/input-wrapper`
- Vendor: `vendor/filament/support/resources/views/components/input/wrapper.blade.php`, `InputComponent/WrapperComponent/IconComponent.php`
- Props: `disabled`, `valid`, `alpineDisabled`, `alpineValid`, `inlinePrefix`, `inlineSuffix`, `prefix`, `suffix`, `prefixIcon`, `prefixIconColor`, `prefixActions`, `suffixIcon`, `suffixIconColor`, `suffixActions`
- Hooks: `fi-input-wrp`, `fi-disabled`, `fi-invalid`, `fi-inline`, `fi-input-wrp-prefix`, `fi-input-wrp-suffix`, `fi-input-wrp-label`, `fi-input-wrp-actions`, `fi-input-wrp-content-ctn`
- Cover: prefix/suffix text, prefix/suffix icons with colors, disabled wrapper, invalid wrapper, inline affixes, action slots if used in app forms.

### Link

- Tag: `<x-filament::link>`
- Docs: `components/link`
- Vendor: `vendor/filament/support/resources/views/components/link.blade.php`, `LinkComponent.php`
- Props: `badge`, `badgeColor`, `badgeSize`, `color`, `disabled`, `href`, `icon`, `iconPosition`, `iconSize`, `keyBindings`, `labelSrOnly`, `loadingIndicator`, `size`, `tag`, `target`, `tooltip`, `type`, `weight`
- Hooks: `fi-link`, `fi-link-badge-ctn`, `fi-disabled`, `fi-size-*`, `fi-font-*`
- Cover: all colors, sizes, font weights, icon before/after, badge, button tag, disabled, tooltip, anchor target.

### Loading Indicator

- Tag: `<x-filament::loading-indicator />`
- Docs: `components/loading-indicator`
- Vendor: `vendor/filament/support/resources/views/components/loading-indicator.blade.php`
- Cover: small/medium/large dimensions, semantic colors, inline inside buttons/badges/actions.

### Modal

- Tag: `<x-filament::modal>`
- Docs: `components/modal`
- Vendor: `vendor/filament/support/resources/views/components/modal/index.blade.php`, `ModalComponent.php`, `ModalComponent/IconComponent.php`
- Props: `alignment`, `autofocus`, `closeButton`, `closeByClickingAway`, `closeByEscaping`, `description`, `extraModalWindowAttributeBag`, `extraModalOverlayAttributeBag`, `footer`, `footerActions`, `footerActionsAlignment`, `header`, `heading`, `icon`, `iconColor`, `id`, `slideOver`, `slideOverPosition`, `stickyFooter`, `stickyHeader`, `teleport`, `trigger`, `visible`, `width`
- Hooks: `fi-modal`, `fi-modal-trigger`, `fi-modal-window-ctn`, `fi-modal-window`, `fi-modal-header`, `fi-modal-heading`, `fi-modal-description`, `fi-modal-content`, `fi-modal-footer`, `fi-modal-close-btn`, `fi-modal-slide-over`, `fi-modal-has-sticky-header`, `fi-modal-has-sticky-footer`, `fi-align-*`, `fi-width-*`
- Cover: standard modal, slide-over, sticky header/footer, every likely width, centered alignment, icon colors, close button disabled, click-away/escape disabled, footer actions.

### Pagination

- Tags: `<x-filament::pagination>`, `pagination.item`
- Docs: `components/pagination`
- Vendor: `vendor/filament/support/resources/views/components/pagination/index.blade.php`, `pagination/item.blade.php`
- Props: `paginator`, `pageOptions`, `currentPageOptionProperty`, `extremeLinks`; item props: `active`, `ariaLabel`, `disabled`, `icon`, `label`
- Hooks: `fi-pagination`, `fi-simple`, `fi-pagination-overview`, `fi-pagination-records-per-page-select-ctn`, `fi-pagination-previous-btn`, `fi-pagination-next-btn`, `fi-pagination-items`, `fi-pagination-item`, `fi-pagination-item-btn`, `fi-active`, `fi-disabled`
- Cover: length-aware paginator, simple paginator if used, first/last links, page-size select, active/disabled items, previous/next buttons.

### Section

- Tag: `<x-filament::section>`
- Docs: `components/section`
- Vendor: `vendor/filament/support/resources/views/components/section/index.blade.php`, `SectionComponent/IconComponent.php`
- Props: `afterHeader`, `aside`, `collapsed`, `collapseId`, `collapsible`, `compact`, `contained`, `contentBefore`, `description`, `divided`, `footer`, `hasContentEl`, `heading`, `headingTag`, `icon`, `iconColor`, `iconSize`, `persistCollapsed`, `secondary`
- Hooks: `fi-section`, `fi-section-not-contained`, `fi-section-has-content-before`, `fi-section-has-header`, `fi-aside`, `fi-compact`, `fi-collapsible`, `fi-collapsed`, `fi-divided`, `fi-secondary`, `fi-section-header`, `fi-section-content`, `fi-section-footer`
- Cover: normal, compact, uncontained, aside, content-before, collapsible collapsed/expanded, divided, secondary, after-header slot, footer slot.

### Tabs

- Tags: `<x-filament::tabs>`, `tabs.item`
- Docs: `components/tabs`
- Vendor: `vendor/filament/support/resources/views/components/tabs/index.blade.php`, `tabs/item.blade.php`
- Tabs props: `contained`, `label`, `vertical`
- Item props: `active`, `alpineActive`, `alpineDeferredBadgeData`, `alpineDeferredBadgeLoading`, `badge`, `badgeColor`, `badgeTooltip`, `badgeIcon`, `badgeIconPosition`, `href`, `icon`, `iconColor`, `iconPosition`, `tag`, `target`, `type`
- Hooks: `fi-tabs`, `fi-contained`, `fi-vertical`, `fi-tabs-item`, `fi-tabs-item-label`, `fi-active`, `fi-tabs-item-badge-placeholder`
- Cover: contained/uncontained, vertical/horizontal, active, Alpine-active if used, badges, badge icons, icons before/after, anchor tabs.

## Color-Mapped Components

Inspect every class implementing `Filament\Support\View\Components\Contracts\HasColor`. Important classes usually include:

- Support: `BadgeComponent`, `ButtonComponent`, `IconButtonComponent`, `LinkComponent`, `ToggleComponent`, `DropdownComponent/HeaderComponent`, `DropdownComponent/ItemComponent`, `CalloutComponent/IconComponent`, `SectionComponent/IconComponent`, `InputComponent/WrapperComponent/IconComponent`, `ModalComponent/IconComponent`.
- Schemas: `TextComponent`, `IconComponent`.
- Infolists: `TextEntryComponent/ItemComponent`, `TextEntryComponent/ItemComponent/IconComponent`, `IconEntryComponent/IconComponent`.
- Tables: `TextColumnComponent/ItemComponent`, `TextColumnComponent/ItemComponent/IconComponent`, `IconColumnComponent/IconComponent`, `Columns/Summarizers/CountComponent/IconComponent`.
- Widgets: `ChartWidgetComponent`, `StatsOverviewWidgetComponent/StatComponent/DescriptionComponent`, `StatsOverviewWidgetComponent/StatComponent/StatsOverviewWidgetStatChartComponent`.

Do not assume docs-only `ColorMaps` helper classes exist in the installed vendor tree. If docs mention a class that is absent locally, document the mismatch and extend/rebind the actual local component class instead.
