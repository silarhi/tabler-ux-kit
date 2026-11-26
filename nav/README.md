# Nav

A list of links between pages, sections or filters. Each item is a real link: the server renders the page with the
right item `active`.

```twig {"preview":true}
<twig:Tabler:Nav variant="tabs" items="{{ [
    {label: 'Profile', href: '/settings', icon: 'user', active: true},
    {label: 'Notifications', href: '/settings/notifications', icon: 'bell', badge: 4},
    {label: 'Billing', href: '/settings/billing', icon: 'credit-card'},
    {label: 'API keys', icon: 'key', disabled: true},
] }}" />
```

`items` is an array of `{label, href?, icon?, active?, disabled?, badge?, keep?}`, each rendered with `Nav:Item`.
`icon` puts a [Tabler icon](https://tabler.io/icons), or a UX Icons name (`lucide:house`), before the label, in a
`.nav-link-icon`; `badge` adds a [Badge](https://tabler-ux-components.silarhi.dev/components/content/badge/) after it.

## Installation

::: installation

## Composed

Pass `Nav:Item`s as children instead: they replace the `content` block.

```twig {"preview":true}
<twig:Tabler:Nav variant="pills">
    <twig:Tabler:Nav:Item href="/invoices" active>All</twig:Tabler:Nav:Item>
    <twig:Tabler:Nav:Item href="/invoices?status=unpaid">Unpaid</twig:Tabler:Nav:Item>
    <twig:Tabler:Nav:Item href="/invoices?status=paid">Paid</twig:Tabler:Nav:Item>
    <twig:Tabler:Nav:Item disabled>Archived</twig:Tabler:Nav:Item>
</twig:Tabler:Nav>
```

## Nav, Tabs or Navbar

- **Nav**: static navigation, each item links to a URL. Use it for sub-pages, settings sections, list filters.
- **[Tabs](https://tabler-ux-components.silarhi.dev/components/navigation/tabs/)**: switches between panes already in the page, with JavaScript, without
  loading a new page.
- **[Navbar](https://tabler-ux-components.silarhi.dev/components/layout/navbar/)**: the header or sidebar of the app, with the brand, the main menu and a
  collapse toggler.

A Nav with `variant="tabs"` looks like Tabs, but its items are links, not pane switchers.

## Variants

`variant` sets the look: `default` (plain links), `tabs`, `pills` or `underline`:

```twig {"preview":true}
{% for variant in ['default', 'tabs', 'pills', 'underline'] %}
    <twig:Tabler:Nav variant="{{ variant }}" class="mb-3">
        <twig:Tabler:Nav:Item href="/settings" active>Profile</twig:Tabler:Nav:Item>
        <twig:Tabler:Nav:Item href="/settings/security">Security</twig:Tabler:Nav:Item>
        <twig:Tabler:Nav:Item href="/settings/billing">Billing</twig:Tabler:Nav:Item>
    </twig:Tabler:Nav>
{% endfor %}
```

## Vertical

`vertical` stacks the items in a column, for a side menu:

```twig {"preview":true}
<twig:Tabler:Nav variant="pills" vertical>
    <twig:Tabler:Nav:Item href="/settings" active>Profile</twig:Tabler:Nav:Item>
    <twig:Tabler:Nav:Item href="/settings/security">Security</twig:Tabler:Nav:Item>
    <twig:Tabler:Nav:Item href="/settings/billing">Billing</twig:Tabler:Nav:Item>
</twig:Tabler:Nav>
```

## Fill and justified

`fill` makes the items take the full width, each in proportion to its text. `justified` gives them all the same width:

```twig {"preview":true}
<twig:Tabler:Nav variant="pills" fill class="mb-3">
    <twig:Tabler:Nav:Item href="/deployments" active>Deployments</twig:Tabler:Nav:Item>
    <twig:Tabler:Nav:Item href="/logs">Logs</twig:Tabler:Nav:Item>
    <twig:Tabler:Nav:Item href="/environment-variables">Environment variables</twig:Tabler:Nav:Item>
</twig:Tabler:Nav>
<twig:Tabler:Nav variant="pills" justified>
    <twig:Tabler:Nav:Item href="/deployments" active>Deployments</twig:Tabler:Nav:Item>
    <twig:Tabler:Nav:Item href="/logs">Logs</twig:Tabler:Nav:Item>
    <twig:Tabler:Nav:Item href="/environment-variables">Environment variables</twig:Tabler:Nav:Item>
</twig:Tabler:Nav>
```

## Overflow

`overflow` wraps the nav in a `.nav-overflow` with `data-bs-toggle="nav-overflow"`: `tabler.js` (1.7 or later) then
moves the items that do not fit into a More dropdown at the end of the bar, and back when there is room again. An item
marked `keep` (`nav-overflow-keep`) always stays in the bar, for the current section for example. A vertical nav never
overflows.

```twig {"preview":true}
<div style="max-width: 26rem">
    <twig:Tabler:Nav variant="underline" overflow items="{{ [
        {label: 'Overview', href: '/project', active: true, keep: true},
        {label: 'Deployments', href: '/project/deployments'},
        {label: 'Logs', href: '/project/logs'},
        {label: 'Analytics', href: '/project/analytics'},
        {label: 'Storage', href: '/project/storage'},
        {label: 'Settings', href: '/project/settings'},
    ] }}" />
</div>
```

The wrapper takes the width of its container, so put the nav in a box that sets it. Tabler reads its options from
the wrapper (`data-bs-more-text="…"` for the label of the More toggle, `data-bs-collapse-below`…): to set them, write
the `<div class="nav-overflow" data-bs-toggle="nav-overflow">` yourself around a `Nav` without `overflow`.

## Props

`Nav`:

| Prop        | Type   | Default     | Description                                                                                  |
| ----------- | ------ | ----------- | -------------------------------------------------------------------------------------------- |
| `variant`   | string | `'default'` | `default` `tabs` (`nav-tabs`) `pills` (`nav-pills`) `underline` (`nav-underline`)            |
| `vertical`  | bool   | `false`     | Stacks the items in a column (`flex-column`)                                                 |
| `fill`      | bool   | `false`     | Items share the full width, in proportion to their content (`nav-fill`)                      |
| `justified` | bool   | `false`     | Items share the full width equally (`nav-justified`)                                         |
| `items`     | array? | `null`      | `{label, href?, icon?, active?, disabled?, badge?, keep?}` entries, rendered with `Nav:Item` |
| `overflow`  | bool   | `false`     | Moves the items that do not fit into a More dropdown (`.nav-overflow` wrapper, Tabler 1.7+)  |

Other attributes go to the root `<ul class="nav">`.

`Nav:Item`:

| Prop       | Type    | Default | Description                                                                                 |
| ---------- | ------- | ------- | ------------------------------------------------------------------------------------------- |
| `href`     | string? | `null`  | Link target; without it, the `<a>` has no `href`                                            |
| `active`   | bool    | `false` | The current item (`active`, with `aria-current="page"`)                                     |
| `disabled` | bool    | `false` | Not clickable (`disabled`, with `aria-disabled="true"`)                                     |
| `icon`     | string? | `null`  | Leading Tabler icon or UX Icons name (`nav-link-icon`)                                      |
| `keep`     | bool    | `false` | Never moved into the More dropdown of an `overflow` nav (`nav-overflow-keep` on the `<li>`) |

Other attributes go to the `<a class="nav-link">`, not to the `<li>`.

## Sub-components

| Component  | Renders                                                  |
| ---------- | -------------------------------------------------------- |
| `Nav:Item` | `<li class="nav-item">` around an `<a class="nav-link">` |

## Blocks

| Block     | Default                                         |
| --------- | ----------------------------------------------- |
| `content` | A `Nav:Item` for each entry of the `items` prop |

The content of `Nav:Item` is its label, after the `icon`.
