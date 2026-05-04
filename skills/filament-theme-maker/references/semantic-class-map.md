# Filament Semantic Class Map

Use this when the task names a surface such as "button", "table row", "sidebar item", or "modal footer". It maps semantic `fi-*` classes to what they control and the safest override targets.

Always inspect the listed vendor CSS file before editing. This file tells you where to start; vendor CSS tells you exact utilities and cascade.

## Common Modifiers

| Class | Meaning | Usually affects |
| --- | --- | --- |
| `.fi-color` | Component is using a registered Filament color map | color variables, text/bg/ring/icon colors |
| `.fi-size-xs`, `.fi-size-sm`, `.fi-size-md`, `.fi-size-lg`, `.fi-size-xl` | Component size variant | padding, gap, font size, icon/button dimensions |
| `.fi-disabled` | Disabled component state | opacity, cursor, pointer events |
| `.fi-active` | Active navigation/tab/button-like state | background, text color, selected indicator |
| `.fi-selected` | Selected table/dropdown state | row background, selected markers |
| `.fi-focused` | JS-managed focus state | focus ring, selected calendar/list item styling |
| `.fi-hidden` | Filament-managed hidden state | display/visibility |
| `.fi-collapsible` | Can collapse | cursor, collapse button state |
| `.fi-collapsed` | Collapsed | hidden content, rotated chevron, transformed sidebar |
| `.fi-compact` | Compact density variant | smaller padding/gaps/radius |
| `.fi-secondary` | Secondary container variant | muted background/surface |
| `.fi-width-*` | Width token | max width, modal/page/simple layout width |
| `.fi-align-*` | Horizontal alignment | actions/modal/footer/header alignment |
| `.fi-vertical-align-*` | Vertical alignment | modal/header/form-field alignment |

## Actions

Vendor CSS: `vendor/filament/actions/resources/css/actions.css`

| Class | What it is | Override when |
| --- | --- | --- |
| `.fi-ac` | Generic actions flex container | action spacing, wrapping, button alignment |
| `.fi-width-full` | Full-width actions mode | actions should stretch across container |
| `.fi-align-start`, `.fi-align-left` | Start/left aligned actions | header/footer actions align incorrectly |
| `.fi-align-center` | Center aligned actions | centered modal or empty-state actions need spacing |
| `.fi-align-end`, `.fi-align-right` | End/right aligned actions | header actions or table actions need alignment |
| `.fi-align-between` | Space-between actions | split action groups |
| `.fi-align-justify` | Justified actions | equal-width action buttons |

## Panel Layout And Chrome

Vendor CSS: `vendor/filament/filament/resources/css/components/layout.css`, `page.css`, `header.css`, `topbar.css`, `sidebar.css`

| Class | What it is | Override when |
| --- | --- | --- |
| `.fi-body` | Panel body root | app background, base text color, global radius/token scope |
| `.fi-panel-{id}` | Panel-specific body class | scoping a theme to one panel |
| `.fi-body-has-navigation` | Panel has navigation | layout offsets depend on navigation |
| `.fi-body-has-topbar` | Panel topbar is rendered | sidebar top/height offsets |
| `.fi-body-has-top-navigation` | Top navigation mode | main container offsets |
| `.fi-body-has-sidebar-collapsible-on-desktop` | Desktop-collapsible sidebar mode | main width/sidebar collapsed behavior |
| `.fi-body-has-sidebar-fully-collapsible-on-desktop` | Fully collapsible desktop sidebar | collapsed transform/offset behavior |
| `.fi-layout` | Main authenticated layout wrapper | full-panel layout structure |
| `.fi-main-ctn` | Main content container beside nav | content offset, sidebar-open state, transition |
| `.fi-main-ctn-sidebar-open` | Main content when sidebar is open | mobile/sidebar overlay offset debugging |
| `.fi-main` | Actual main content max-width/padding | page horizontal padding, max width, edge-to-edge layouts |
| `.fi-width-*` | Page/simple/modal width token | page max width and modal width |
| `.fi-page` | Page wrapper | page full-height and sub-navigation state |
| `.fi-height-full` | Full-height page state | dashboards/tools that should stretch |
| `.fi-page-header-main-ctn` | Page header plus content vertical wrapper | vertical rhythm between header/content |
| `.fi-page-content` | Page content stack | gaps between widgets/content sections |
| `.fi-page-main` | Main page body when sub-navigation exists | sub-nav/content grid behavior |
| `.fi-page-has-sub-navigation` | Page with sub-navigation | page layout around sub-nav |
| `.fi-page-has-sub-navigation-start`, `.fi-page-has-sub-navigation-end` | Sub-nav side | left/right sub-nav spacing |
| `.fi-page-sub-navigation-sidebar` | Desktop sub-nav sidebar | nested page navigation styles |
| `.fi-page-sub-navigation-tabs` | Tab sub-navigation | page-level tabs |
| `.fi-page-sub-navigation-dropdown` | Mobile sub-nav dropdown | mobile page nav trigger |
| `.fi-header` | Page header layout | heading/action spacing and wrapping |
| `.fi-header-has-breadcrumbs` | Header with breadcrumbs | action alignment with breadcrumbs |
| `.fi-header-heading` | Page H1 | page title typography/color |
| `.fi-header-subheading` | Page subtitle | secondary header text |
| `.fi-header-actions-ctn` | Header actions container | header action spacing/alignment |
| `.fi-simple-layout` | Auth/simple page layout root | login screen background/layout |
| `.fi-simple-layout-header` | Simple layout top header | auth topbar/header |
| `.fi-simple-main-ctn` | Simple main outer container | login page vertical centering |
| `.fi-simple-main` | Simple page max-width container | login form width/surface |
| `.fi-simple-page-content` | Simple page content stack | auth page spacing |
| `.fi-simple-header` | Simple page header | login header layout |
| `.fi-simple-header-heading` | Simple page title | login heading type |
| `.fi-simple-header-subheading` | Simple page subtitle | login secondary text |

## Topbar

Vendor CSS: `vendor/filament/filament/resources/css/components/topbar.css`

| Class | What it is | Override when |
| --- | --- | --- |
| `.fi-topbar-ctn` | Sticky topbar container | z-index, sticky behavior, border/shadow envelope |
| `.fi-topbar` | Topbar nav surface | height, background, ring/shadow, padding |
| `.fi-topbar-start` | Logo/sidebar-toggle side | logo spacing and nav alignment |
| `.fi-topbar-end` | Search/notifications/user-menu side | right-side control spacing |
| `.fi-topbar-nav-groups` | Top navigation list | top nav gap |
| `.fi-topbar-item` | Top nav item wrapper | active state scoping |
| `.fi-topbar-item-btn` | Clickable top nav item | nav item background/radius/padding |
| `.fi-topbar-item-icon` | Top nav icon | icon color/size |
| `.fi-topbar-item-label` | Top nav label | label typography/color |
| `.fi-topbar-group-toggle-icon` | Top nav group chevron | group indicator color/rotation |
| `.fi-topbar-open-sidebar-btn`, `.fi-topbar-close-sidebar-btn` | Mobile sidebar controls | mobile topbar icons |
| `.fi-topbar-open-collapse-sidebar-btn`, `.fi-topbar-close-collapse-sidebar-btn` | Desktop sidebar collapse controls | collapse icon spacing/colors |
| `.fi-topbar-collapse-sidebar-btn-ctn` | Collapse button container | collapse button placement |
| `.fi-topbar-database-notifications-btn` | Topbar notification trigger | notification trigger styling |

## Sidebar

Vendor CSS: `vendor/filament/filament/resources/css/components/sidebar.css`

| Class | What it is | Override when |
| --- | --- | --- |
| `.fi-sidebar` | Sidebar surface | background, width, transform, top offset |
| `.fi-main-sidebar` | Main sidebar instance | distinguish from nested/sidebar-like surfaces |
| `.fi-sidebar-open` | Sidebar open state | transform/overlay behavior |
| `.fi-sidebar-close-overlay` | Mobile overlay behind sidebar | overlay color/opacity |
| `.fi-sidebar-header-ctn` | Header outer wrapper | sticky/header border |
| `.fi-sidebar-header` | Logo/collapse button row | sidebar header height/padding |
| `.fi-sidebar-header-logo-ctn` | Logo area | brand logo spacing |
| `.fi-sidebar-nav` | Scrollable navigation area | nav padding/gap |
| `.fi-sidebar-nav-groups` | Group list | group spacing |
| `.fi-sidebar-group` | Navigation group wrapper | group state, grouped spacing |
| `.fi-sidebar-group-btn` | Group label/collapse button | group heading styles |
| `.fi-sidebar-group-label` | Group label text | group heading typography |
| `.fi-sidebar-group-collapse-btn` | Inline group collapse button | chevron/button treatment |
| `.fi-sidebar-group-dropdown-trigger-btn` | Collapsed sidebar group trigger | collapsed nav dropdown trigger |
| `.fi-sidebar-group-items` | Group item list | item list gap |
| `.fi-sidebar-item` | Sidebar item wrapper | active/recursive state |
| `.fi-sidebar-item-has-url` | Clickable item state | cursor/hover scope |
| `.fi-sidebar-item-has-active-child-items` | Parent item with active child | parent active color/background |
| `.fi-sidebar-item-btn` | Clickable item surface | nav item padding, radius, hover, active bg |
| `.fi-sidebar-item-icon` | Nav item icon | icon color, size |
| `.fi-sidebar-item-label` | Nav item label | label typography/color |
| `.fi-sidebar-item-badge-ctn` | Nav item badge wrapper | badge placement |
| `.fi-sidebar-sub-group-items` | Recursive child item list | child indentation |
| `.fi-sidebar-item-grouped-border` | Tree border wrapper | recursive grouped border |
| `.fi-sidebar-item-grouped-border-part*` | Tree border pieces | nested nav guide lines |
| `.fi-sidebar-footer` | Footer controls area | footer spacing and top border |
| `.fi-sidebar-database-notifications-btn*` | Sidebar notification trigger parts | sidebar notification styling |

## Global Search

Vendor CSS: `vendor/filament/filament/resources/css/components/global-search.css`

| Class | What it is | Override when |
| --- | --- | --- |
| `.fi-global-search-ctn` | Search outer container | width in topbar/sidebar |
| `.fi-global-search` | Search component root | position and result dropdown context |
| `.fi-global-search-field` | Input field wrapper in Blade | input spacing with icon |
| `.fi-global-search-results-ctn` | Results floating panel | width, max height, border/shadow |
| `.fi-global-search-no-results-message` | Empty results text | empty state text color |
| `.fi-global-search-results` | Results list | list padding/gap |
| `.fi-global-search-result-group` | Result group wrapper | grouped result spacing |
| `.fi-global-search-result-group-header` | Group heading | group label typography |
| `.fi-global-search-result-group-results` | Group result list | group item spacing |
| `.fi-global-search-result` | Single result row wrapper | row hover/selected state |
| `.fi-global-search-result-has-actions` | Result with inline actions | result link/action layout |
| `.fi-global-search-result-link` | Clickable result body | row padding/background |
| `.fi-global-search-result-heading` | Result title | title typography |
| `.fi-global-search-result-details` | Details group | metadata layout |
| `.fi-global-search-result-detail` | Single detail | metadata spacing |
| `.fi-global-search-result-detail-label` | Detail label | metadata label color |
| `.fi-global-search-result-detail-value` | Detail value | metadata value color |
| `.fi-global-search-result-actions` | Inline result actions | action placement |

## Button

Vendor CSS: `vendor/filament/support/resources/css/components/button.css`

| Class | What it is | Override when |
| --- | --- | --- |
| `.fi-btn` | Button root | base display, radius, padding, typography, focus ring, default bg |
| `.fi-btn.fi-color` | Colored button | semantic bg/text/hover/focus colors |
| `.fi-btn.fi-outlined` | Outlined button variant | outline ring, transparent bg, outlined hover |
| `.fi-btn.fi-disabled`, `.fi-btn[disabled]` | Disabled button | opacity, cursor, pointer events |
| `.fi-force-enabled` | Forces interactive styling despite disabled-like state | action components need active treatment |
| `.fi-processing` | Processing/loading state | wait cursor, opacity |
| `.fi-size-xs`, `.fi-size-sm`, `.fi-size-lg`, `.fi-size-xl` | Button size variants | padding/gap/font tweaks |
| `.fi-labeled-from-sm`, `.fi-labeled-from-md`, `.fi-labeled-from-lg`, `.fi-labeled-from-xl`, `.fi-labeled-from-2xl` | Button hidden until breakpoint, paired with icon button | responsive icon-to-text actions |
| `.fi-btn-badge-ctn` | Absolute badge wrapper | badge position/background around button |
| `.fi-btn-group` | Grouped button wrapper | group ring, shadow, radius |
| `.fi-btn-group > .fi-btn` | Grouped button child | remove inner radius/rings, separators |
| `.fi-icon` inside `.fi-btn` | Button icon | icon color and transitions |

Best targets:
- Shape/density: `.fi-btn`, `.fi-btn.fi-size-*`, `.fi-btn-group`.
- Semantic color: `.fi-btn.fi-color:not(.fi-outlined)` or `.fi-btn.fi-outlined.fi-color`.
- Icon color: `.fi-btn > .fi-icon` and `.fi-btn.fi-color > .fi-icon`.
- Badge placement: `.fi-btn .fi-btn-badge-ctn`.

## Icon Button

Vendor CSS: `vendor/filament/support/resources/css/components/icon-button.css`

| Class | What it is | Override when |
| --- | --- | --- |
| `.fi-icon-btn` | Icon-only button root | size, negative margins, radius, icon color, focus ring |
| `.fi-icon-btn.fi-color` | Semantic icon button | text/hover/focus colors |
| `.fi-icon-btn.fi-disabled`, `.fi-icon-btn[disabled]` | Disabled state | opacity/cursor/pointer events |
| `.fi-icon-btn.fi-size-*` | Size variant | button box and margin |
| `.fi-icon-btn-badge-ctn` | Badge wrapper | badge position/background |
| `.fi-icon-btn:has(+ .fi-btn.fi-labeled-from-*)` | Responsive companion icon button | hide icon button at labeled breakpoint |

Best targets:
- Icon-only action density: `.fi-icon-btn`.
- Semantic color: `.fi-icon-btn.fi-color`.
- Responsive action pairs: `.fi-icon-btn:has(+ .fi-btn.fi-labeled-from-*)`.

## Badge

Vendor CSS: `vendor/filament/support/resources/css/components/badge.css`

| Class | What it is | Override when |
| --- | --- | --- |
| `.fi-badge` | Badge root | bg, text, ring, radius, padding, truncation |
| `.fi-badge.fi-color` | Semantic badge | semantic bg/text/ring |
| `.fi-badge.fi-disabled`, `.fi-badge[disabled]` | Disabled badge | opacity/cursor/pointer events |
| `.fi-badge.fi-size-xs`, `.fi-badge.fi-size-sm` | Compact badge sizes | min width, padding, tracking |
| `.fi-badge-label-ctn` | Grid wrapper around label | label layout/truncation context |
| `.fi-badge-label` | Actual label | truncate/wrap behavior |
| `.fi-wrapped` | Wrapped badge/label state | text wrapping instead of truncation |
| `.fi-badge-delete-btn` | Delete affordance | delete icon hit area and color |
| `.fi-icon` inside `.fi-badge` | Badge icon | shrink and icon color |

Best targets:
- Badge surface: `.fi-badge`.
- Status colors: `.fi-badge.fi-color`.
- Long labels: `.fi-badge-label`, `.fi-wrapped`.
- Remove button: `.fi-badge-delete-btn`.

## Link

Vendor CSS: `vendor/filament/support/resources/css/components/link.css`

| Class | What it is | Override when |
| --- | --- | --- |
| `.fi-link` | Link root | inline-flex, gap, font weight, color |
| `.fi-link.fi-color` | Semantic link | semantic text and hover colors |
| `.fi-link.fi-disabled` | Disabled link | opacity/cursor/pointer events |
| `.fi-link.fi-size-*` | Link size variant | font size/gap |
| `.fi-font-*` | Weight variant | font-weight |
| `.fi-link-badge-ctn` | Badge wrapper | badge placement next to link |
| `.fi-icon` inside `.fi-link` | Link icon | icon color/size |

Best targets:
- Text link color: `.fi-link` or `.fi-link.fi-color`.
- Inline action spacing: `.fi-link`, `.fi-link-badge-ctn`.

## Input, Select, Checkbox, Wrapper

Vendor CSS: `vendor/filament/support/resources/css/components/input/*.css`

| Class | What it is | Override when |
| --- | --- | --- |
| `.fi-input-wrp` | Input wrapper surface | ring, bg, shadow, radius, focus ring |
| `.fi-input-wrp.fi-invalid` | Invalid wrapper | danger ring and focus ring |
| `.fi-input-wrp.fi-disabled` | Disabled wrapper | disabled bg/ring |
| `.fi-input-wrp-prefix` | Prefix slot | prefix border, padding, icon/text placement |
| `.fi-input-wrp-prefix-has-content` | Prefix is visible | display prefix |
| `.fi-input-wrp-prefix-has-label` | Prefix includes label text | inline padding adjustment |
| `.fi-input-wrp-content-ctn` | Input content flex cell | min-width/flex behavior |
| `.fi-input-wrp-content-ctn-ps` | Content padding-start compensation | spacing when prefix is absent/present |
| `.fi-input-wrp-suffix` | Suffix slot | suffix border, padding, icon/text placement |
| `.fi-input-wrp-suffix-has-label` | Suffix includes label text | inline padding adjustment |
| `.fi-input-wrp-actions` | Prefix/suffix actions group | icon button/action gap |
| `.fi-input-wrp-label` | Prefix/suffix text | affix label color/type |
| `.fi-inline` | Inline affix mode | no border, tighter spacing |
| `.fi-input` | Native input | padding, text, placeholder, disabled state |
| `.fi-input-has-inline-prefix` | Input adjusted for inline prefix | padding-left/start |
| `.fi-input-has-inline-suffix` | Input adjusted for inline suffix | padding-right/end |
| `.fi-select-input` | Native select | select padding/icon appearance |
| `.fi-select-input-has-inline-prefix` | Select adjusted for inline prefix | prefix spacing |
| `.fi-checkbox-input` | Checkbox input | size, border, checked color, focus ring |
| `.fi-checkbox-input.fi-valid` | Valid checkbox state | normal ring/color |
| `.fi-checkbox-input.fi-invalid` | Invalid checkbox state | danger border/ring |
| `.fi-radio-input` | Radio input | radio size, border, checked/focus color |

Best targets:
- Field surface/radius/ring: `.fi-input-wrp`.
- Invalid state: `.fi-input-wrp.fi-invalid`, `.fi-checkbox-input.fi-invalid`.
- Text field density: `.fi-input`.
- Affix styling: `.fi-input-wrp-prefix`, `.fi-input-wrp-suffix`, `.fi-input-wrp-label`.

## Dropdown

Vendor CSS: `vendor/filament/support/resources/css/components/dropdown/**/*.css`

| Class | What it is | Override when |
| --- | --- | --- |
| `.fi-dropdown` | Dropdown root | positioning context |
| `.fi-dropdown-trigger` | Trigger wrapper | trigger display context |
| `.fi-dropdown-panel` | Floating panel | bg, border/ring, shadow, radius, width, scroll |
| `.fi-scrollable` | Scrollable panel state | max-height/overflow |
| `.fi-dropdown-header` | Header row | header padding, icon/text color |
| `.fi-dropdown-list` | Item list | list padding/gap |
| `.fi-dropdown-list-item` | Item root | item padding, radius, text, hover, disabled |
| `.fi-dropdown-list-item.fi-color` | Semantic item | semantic text/icon hover colors |
| `.fi-dropdown-list-item.fi-disabled` | Disabled item | opacity/pointer events |
| `.fi-dropdown-list-item-label` | Item label | truncation/typography |
| `.fi-dropdown-list-item-image` | Item image/avatar | image size/radius |
| `.fi-dropdown-list-item-badge-placeholder` | Deferred badge loading placeholder | loading badge placement |

Best targets:
- Panel surface: `.fi-dropdown-panel`.
- Item hover/color: `.fi-dropdown-list-item`, `.fi-dropdown-list-item.fi-color`.
- Header styling: `.fi-dropdown-header`.

## Modal

Vendor CSS: `vendor/filament/support/resources/css/components/modal.css`

| Class | What it is | Override when |
| --- | --- | --- |
| `.fi-modal` | Modal root | open/slide-over/width/alignment state scope |
| `.fi-modal-open` | Open modal state | overlay/window z-index and visibility |
| `.fi-modal-slide-over` | Slide-over variant | full-height side panel behavior |
| `.fi-modal-slide-over-from-start`, `.fi-modal-slide-over-from-end` | Slide-over side | entrance transform and side alignment |
| `.fi-modal-close-overlay` | Backdrop | overlay color/opacity |
| `.fi-modal-window-ctn` | Fixed grid centering container | alignment, click-away cursor, padding |
| `.fi-clickable` | Click-away container state | cursor pointer outside window |
| `.fi-modal-window` | Modal surface | bg, ring, shadow, radius, width, overflow |
| `.fi-modal-window-has-close-btn` | Window has close button | header spacing/close placement |
| `.fi-modal-window-has-content` | Window has content | content spacing |
| `.fi-modal-window-has-footer` | Window has footer | footer spacing |
| `.fi-modal-window-has-icon` | Window has icon | icon/content indentation |
| `.fi-modal-header` | Header area | padding, alignment, gap |
| `.fi-modal-icon-ctn` | Icon wrapper | icon alignment |
| `.fi-modal-icon-bg` | Icon background | icon bubble padding/bg |
| `.fi-modal-heading` | Heading | heading type/color |
| `.fi-modal-description` | Description | secondary type/color |
| `.fi-modal-content` | Body content | padding/gap/flex |
| `.fi-modal-footer` | Footer area | padding, border, sticky behavior |
| `.fi-modal-footer-actions` | Footer action group | action alignment/gap |
| `.fi-modal-close-btn` | Close icon button | close position |
| `.fi-modal-has-sticky-header`, `.fi-modal-has-sticky-footer` | Sticky region states | max-height/rounded region behavior |
| `.fi-transition-enter*`, `.fi-transition-leave*` | Transition states | animation transforms/opacity |

Best targets:
- Modal surface: `.fi-modal-window`.
- Backdrop: `.fi-modal-close-overlay`.
- Header/footer spacing: `.fi-modal-header`, `.fi-modal-footer`.
- Slide-over: `.fi-modal.fi-modal-slide-over > .fi-modal-window-ctn > .fi-modal-window`.

## Section

Vendor CSS: `vendor/filament/support/resources/css/components/section.css`

| Class | What it is | Override when |
| --- | --- | --- |
| `.fi-section` | Section root | contained card surface, layout, base spacing |
| `.fi-section-not-contained` | Uncontained variant | removes card surface; content becomes plain layout |
| `.fi-section-has-header` | Header exists | border between header/content |
| `.fi-section-has-content-before` | Content ordered before aside header | aside ordering |
| `.fi-aside` | Aside layout | header/content grid |
| `.fi-compact` | Compact section | smaller padding/radius/gaps |
| `.fi-collapsible` | Collapsible section | header cursor |
| `.fi-collapsed` | Collapsed section | hide content, rotate collapse button |
| `.fi-divided` | Divided content | divide-y and child padding |
| `.fi-secondary` | Secondary section | muted background |
| `.fi-section-header` | Header row | header padding/gap |
| `.fi-section-header-text-ctn` | Header text wrapper | heading/description grid |
| `.fi-section-header-heading` | Heading | section title type/color |
| `.fi-section-header-description` | Description | section secondary type/color |
| `.fi-section-header-after-ctn` | Right-side header slot | badge/action alignment |
| `.fi-section-collapse-btn` | Collapse icon button | chevron rotation/margins |
| `.fi-section-content-ctn` | Content/footer wrapper | borders and collapsed hiding |
| `.fi-section-content` | Content area | padding/gap |
| `.fi-section-footer` | Footer area | top border/padding |

Best targets:
- Card surface: `.fi-section:not(.fi-section-not-contained):not(.fi-aside)`.
- Inner padding: `.fi-section-content`, `.fi-section-header`, `.fi-section-footer`.
- Aside card surface: `.fi-section.fi-aside > .fi-section-content-ctn`.

## Tabs

Vendor CSS: `vendor/filament/support/resources/css/components/tabs.css`

| Class | What it is | Override when |
| --- | --- | --- |
| `.fi-tabs` | Tabs nav root | tab list spacing/surface |
| `.fi-contained` | Contained tabs variant | background/ring/radius/padding |
| `.fi-vertical` | Vertical tabs variant | stacked tab layout |
| `.fi-tabs-item` | Single tab trigger | padding, radius, typography, hover |
| `.fi-tabs-item.fi-active` | Active tab | selected bg/text/ring |
| `.fi-tabs-item-label` | Tab label | label truncation/type |
| `.fi-tabs-item-badge-placeholder` | Deferred badge placeholder | loading badge layout |

Best targets:
- Tab list surface: `.fi-tabs.fi-contained`.
- Trigger state: `.fi-tabs-item`, `.fi-tabs-item.fi-active`.

## Callout, Empty State, Fieldset, Avatar, Breadcrumbs, Loading

Vendor CSS: `vendor/filament/support/resources/css/components/*.css`

| Class | What it is | Override when |
| --- | --- | --- |
| `.fi-callout` | Callout root | semantic message surface |
| `.fi-callout-main` | Callout main row | icon/text/control layout |
| `.fi-callout-icon` | Callout icon | icon color/size |
| `.fi-callout-text` | Text stack | heading/description layout |
| `.fi-callout-heading` | Heading | title type/color |
| `.fi-callout-description` | Description | secondary text |
| `.fi-callout-controls` | Control slot | dismiss/action placement |
| `.fi-callout-footer` | Footer slot | footer spacing |
| `.fi-empty-state` | Empty state root | centered empty surface |
| `.fi-empty-state-not-contained` | Uncontained empty state | removes container treatment |
| `.fi-empty-state-content` | Empty content stack | spacing/align |
| `.fi-empty-state-icon-bg` | Icon bubble | icon background/size |
| `.fi-empty-state-heading` | Heading | title type |
| `.fi-empty-state-description` | Description | secondary text |
| `.fi-empty-state-footer` | Footer actions | action placement |
| `.fi-fieldset` | Fieldset root | border/ring/padding |
| `.fi-fieldset-not-contained` | Uncontained fieldset | plain fieldset layout |
| `.fi-fieldset-label-hidden` | Hidden label state | accessible hidden label |
| `.fi-fieldset-label-required-mark` | Required asterisk | required mark color |
| `.fi-avatar` | Avatar image | size/object/radius |
| `.fi-circular` | Circular avatar | border-radius full |
| `.fi-breadcrumbs` | Breadcrumb nav | nav typography |
| `.fi-breadcrumbs-list` | Breadcrumb list | list flex/gap |
| `.fi-breadcrumbs-item` | Breadcrumb item | item layout |
| `.fi-breadcrumbs-item-label` | Breadcrumb text/link | label color/hover |
| `.fi-breadcrumbs-item-separator` | Separator icon | separator color/size |
| `.fi-loading-indicator` | Spinner icon | loading color/size |

## Pagination

Vendor CSS: `vendor/filament/support/resources/css/components/pagination.css`

| Class | What it is | Override when |
| --- | --- | --- |
| `.fi-pagination` | Pagination nav root | pagination layout/padding |
| `.fi-simple` | Simple paginator variant | previous/next only layout |
| `.fi-pagination-overview` | "Showing x to y" text | overview type/color |
| `.fi-pagination-records-per-page-select-ctn` | Per-page select wrapper | records-per-page layout |
| `.fi-pagination-records-per-page-select` | Per-page select label | compact/full select visibility |
| `.fi-pagination-previous-btn`, `.fi-pagination-next-btn` | Previous/next buttons | edge button styling |
| `.fi-pagination-items` | Numeric item list | item list surface/gap |
| `.fi-pagination-item` | Numeric item wrapper | item state wrapper |
| `.fi-pagination-item-btn` | Numeric item button | active/hover/disabled treatment |
| `.fi-pagination-item-icon` | Item icon | prev/next/first/last icon |
| `.fi-pagination-item-label` | Item label | number/ellipsis label |

## Forms Package

Vendor CSS: `vendor/filament/forms/resources/css/components/*.css`

| Class prefix | What it is | Override when |
| --- | --- | --- |
| `.fi-fo-field*` | Generic form field layout, label, content, error message/list | labels, inline labels, validation spacing |
| `.fi-fo-builder*` | Builder field blocks, block picker, add-between controls, previews | builder block cards and controls |
| `.fi-fo-repeater*` | Repeater item surfaces, headers, collapse/reorder actions, table/simple variants | nested item card/table styling |
| `.fi-fo-rich-editor*` | Rich editor toolbar/content/attachments | rich text editor surface |
| `.fi-fo-markdown-editor*` | Markdown editor surface/toolbar | markdown editor styling |
| `.fi-fo-select*` | JS select field wrapper/options | searchable select/dropdown style |
| `.fi-fo-date-time-picker*` | Date/time picker panel, calendar, time inputs, trigger | calendar picker styling |
| `.fi-fo-file-upload*` | File upload, FilePond, image editor/cropper controls | upload/dropzone/editor styling |
| `.fi-fo-color-picker*` | Color picker preview/panel | color picker surface |
| `.fi-fo-tags-input*` | Tags input list/options | tag chips and input layout |
| `.fi-fo-text-input*` | Text input field-specific wrappers | text input extras |
| `.fi-fo-textarea*` | Textarea field-specific wrappers | textarea sizing |
| `.fi-fo-toggle-btns*` | Toggle button groups/options | segmented controls |
| `.fi-fo-checkbox-list*` | Checkbox list, option rows, search input | multi-checkbox layouts |
| `.fi-fo-radio*` | Radio group/options | radio option layout |
| `.fi-fo-key-value*` | Key-value table/wrapper/actions | key-value table styling |
| `.fi-fo-slider*` | Slider track/thumb/input | range controls |
| `.fi-fo-code-editor*` | Code editor shell | code editor surface |

For detailed form fixes, read the exact CSS file and search for the full prefix, for example `rg "fi-fo-repeater" vendor/filament/forms/resources/css/components/repeater.css`.

## Schemas Package

Vendor CSS: `vendor/filament/schemas/resources/css/**/*.css`

| Class | What it is | Override when |
| --- | --- | --- |
| `.fi-sc` | Schema root/grid | schema gaps and density |
| `.fi-sc-form` | Schema form wrapper | form-level dense mode |
| `.fi-dense` | Dense schema/form mode | compact schema spacing |
| `.fi-sc-section` | Schema Section wrapper around support Section | schema-specific labels/above/below content |
| `.fi-sc-section-label-ctn`, `.fi-sc-section-label` | Section label area | schema section side labels |
| `.fi-sc-tabs` | Schema tabs wrapper | schema tab panels/dropdown overflow |
| `.fi-sc-wizard` | Wizard root | wizard layout |
| `.fi-sc-actions` | Schema actions wrapper | action spacing inside schemas |
| `.fi-sc-text` | Schema text prime | text color/type |
| `.fi-sc-icon` | Schema icon prime | icon size/color |
| `.fi-sc-image` | Schema image prime | image radius/size |
| `.fi-sc-unordered-list` | Schema list prime | list marker/spacing |
| `.fi-sc-fused-group` | Fused field group | joined input radius/borders |
| `.fi-sc-flex` | Flex layout component | flex gap/alignment |

## Tables Package

Vendor CSS: `vendor/filament/tables/resources/css/**/*.css`

| Class | What it is | Override when |
| --- | --- | --- |
| `.fi-ta-ctn` | Whole table card/container | table border, radius, shadow, loading pulse |
| `.fi-ta-ctn-with-header` | Table has header | overflow/header treatment |
| `.fi-loading` | Table loading state | loading pulse/opacity |
| `.fi-ta-header-ctn` | Header container offset | header border seams |
| `.fi-ta-header` | Header block | heading/description/actions layout |
| `.fi-ta-header-adaptive-actions-position` | Responsive action positioning | header action layout |
| `.fi-ta-header-heading` | Header title | title typography |
| `.fi-ta-header-description` | Header description | secondary text |
| `.fi-ta-header-toolbar` | Search/filter/action toolbar | toolbar padding/gap/border |
| `.fi-ta-filters*` | Filter form and filter areas | filters dropdown/above/below content |
| `.fi-ta-selection-indicator` | Selected records bar | selected row action bar |
| `.fi-ta-filter-indicators` | Active filter badges bar | active filter summary |
| `.fi-ta-reorder-indicator` | Reordering banner | reorder mode styling |
| `.fi-ta-main` | Table main flex child | min-width and layout |
| `.fi-ta-content` | Scrollable table content area | overflow and table body surface |
| `.fi-ta` | Table wrapper/root | table-level styles |
| `.fi-ta-table` | Actual table element | table layout |
| `.fi-ta-row` | Table row | hover, clickable, striped, selected |
| `.fi-clickable` | Clickable row state | hover background |
| `.fi-striped` | Striped row state | alternating bg |
| `.fi-ta-group-header-row` | Group header row | group bg |
| `.fi-ta-group-header-cell` | Group header cell | group cell padding |
| `.fi-ta-group-header` | Group header content | collapsible group layout |
| `.fi-ta-group-heading` | Group title | group heading type |
| `.fi-ta-group-description` | Group description | group subtext |
| `.fi-selected` | Selected row state | selection bg and left marker |
| `.fi-ta-reordering` | Table in reorder mode | reorder cursor scope |
| `.fi-ta-row-not-reorderable` | Non-reorderable row | cursor exception |
| `.fi-ta-cell` | Body cell | cell padding/alignment |
| `.fi-ta-header-cell` | Header cell | heading alignment/sort controls |
| `.fi-ta-actions` | Table action group | row/header action spacing |
| `.fi-ta-empty-state` | Table empty state | empty table surface |
| `.fi-ta-col-manager*` | Column manager dropdown/content | column toggle panel |
| `.fi-ta-text*` | Text column | text stacks, lists, badges |
| `.fi-ta-icon*` | Icon column | icon alignment/color |
| `.fi-ta-image*` | Image column | image sizing/radius |
| `.fi-ta-checkbox*` | Checkbox column | checkbox cell styling |
| `.fi-ta-color*` | Color column | swatch styling |
| `.fi-ta-select*` | Select column | inline select surface |
| `.fi-ta-toggle*` | Toggle column | toggle cell |
| `.fi-ta-text-input*` | Text input column | inline input surface |

Best targets:
- Overall table card: `.fi-ta-ctn`.
- Row hover/selection: `.fi-ta-row`, `.fi-ta-row.fi-clickable`, `.fi-ta-row.fi-selected`.
- Header toolbar density: `.fi-ta-header-toolbar`.
- Filters: `.fi-ta-filters`, `.fi-ta-filter-indicators`.

## Infolists Package

Vendor CSS: `vendor/filament/infolists/resources/css/components/*.css`

| Class | What it is | Override when |
| --- | --- | --- |
| `.fi-in-entry-wrp` | Entry wrapper | label/content layout and gap |
| `.fi-in-text*` | Text entry | text lists, badges, icons, wrapping |
| `.fi-in-icon*` | Icon entry | icon alignment/color |
| `.fi-in-image*` | Image entry | image size/radius |
| `.fi-in-color*` | Color entry | color swatch |
| `.fi-in-code*` | Code entry | code block surface |
| `.fi-in-key-value*` | Key-value entry | key-value table/list |
| `.fi-in-repeatable*` | Repeatable entry | repeated item container |

## Widgets Package

Vendor CSS: `vendor/filament/widgets/resources/css/*.css`

| Class | What it is | Override when |
| --- | --- | --- |
| `.fi-wi` | Widgets grid wrapper | dashboard widget grid gap |
| `.fi-wi-widget` | Widget wrapper | individual widget grid span wrapper |
| `.fi-wi-stats-overview` | Stats overview grid | stats grid gap |
| `.fi-wi-stats-overview-stat` | Single stat card | stat surface, padding, ring |
| `.fi-wi-stats-overview-stat-value` | Stat value | metric typography |
| `.fi-wi-stats-overview-stat-label` | Stat label | label typography |
| `.fi-wi-stats-overview-stat-description` | Stat description | semantic up/down text |
| `.fi-wi-stats-overview-stat-chart` | Inline stat chart | chart dimensions/color |
| `.fi-wi-chart` | Chart widget | chart card/body/filter layout |
| `.fi-account-widget*` | Built-in account widget | account widget layout |
| `.fi-filament-info-widget*` | Built-in info widget | info widget layout |

## Notifications

Vendor CSS: `vendor/filament/notifications/resources/css/*.css`

| Class | What it is | Override when |
| --- | --- | --- |
| `.fi-no` | Toast notification stack | toast positioning/alignment |
| `.fi-no-notification` | Notification root | notification card surface |
| `.fi-no-notification-icon` | Notification icon | status icon color/size |
| `.fi-no-notification-main` | Main content/action layout | content alignment |
| `.fi-no-notification-text` | Text stack | title/body/date spacing |
| `.fi-no-notification-title` | Title | notification title type |
| `.fi-no-notification-date` | Date | timestamp type/color |
| `.fi-no-notification-body` | Body | body text/prose |
| `.fi-no-database` | Database notification modal wrapper | database notification slide-over scope |
| `.fi-no-notification-read-ctn` | Read database notification wrapper | read row bg |
| `.fi-no-notification-unread-ctn` | Unread database notification wrapper | unread row bg/accent |

## Menus And Misc Panel Components

| Class | What it is | Override when |
| --- | --- | --- |
| `.fi-logo`, `.fi-logo-light`, `.fi-logo-dark` | Panel logo image variants | logo height/display |
| `.fi-user-menu`, `.fi-user-menu-trigger`, `.fi-user-menu-trigger-text`, `.fi-user-avatar` | User menu | user menu trigger/avatar/text |
| `.fi-simple-user-menu-ctn` | Simple layout user menu | auth/simple user switcher |
| `.fi-tenant-menu`, `.fi-tenant-menu-trigger`, `.fi-tenant-avatar`, `.fi-tenant-menu-trigger-text`, `.fi-tenant-menu-trigger-tenant-name`, `.fi-tenant-menu-trigger-current-tenant-label` | Tenant menu | tenant switcher trigger |
| `.fi-theme-switcher`, `.fi-theme-switcher-btn` | Theme switcher | light/dark/system switcher |
| `.fi-resource-relation-manager` | Resource relation manager wrapper | relation manager page spacing |
