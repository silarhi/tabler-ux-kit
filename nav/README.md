# Nav

A list of links between pages, sections or filters. Each item is a real link: the server renders the page with the
right item `active`.

```twig {"preview":true}
<twig:Tabler:Nav variant="pills">
    <twig:Tabler:Nav:Item href="/invoices" active>All</twig:Tabler:Nav:Item>
    <twig:Tabler:Nav:Item href="/invoices?status=unpaid">Unpaid</twig:Tabler:Nav:Item>
    <twig:Tabler:Nav:Item href="/invoices?status=paid">Paid</twig:Tabler:Nav:Item>
    <twig:Tabler:Nav:Item disabled>Archived</twig:Tabler:Nav:Item>
</twig:Tabler:Nav>
```

## Installation

::: installation

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

## Props

`Nav`:

| Prop        | Type   | Default     | Description                                                                       |
| ----------- | ------ | ----------- | --------------------------------------------------------------------------------- |
| `variant`   | string | `'default'` | `default` `tabs` (`nav-tabs`) `pills` (`nav-pills`) `underline` (`nav-underline`) |
| `vertical`  | bool   | `false`     | Stacks the items in a column (`flex-column`)                                      |
| `fill`      | bool   | `false`     | Items share the full width, in proportion to their content (`nav-fill`)           |
| `justified` | bool   | `false`     | Items share the full width equally (`nav-justified`)                              |

Other attributes go to the root `<ul class="nav">`.

`Nav:Item`:

| Prop       | Type    | Default | Description                                             |
| ---------- | ------- | ------- | ------------------------------------------------------- |
| `href`     | string? | `null`  | Link target; without it, the `<a>` has no `href`        |
| `active`   | bool    | `false` | The current item (`active`, with `aria-current="page"`) |
| `disabled` | bool    | `false` | Not clickable (`disabled`, with `aria-disabled="true"`) |

Other attributes go to the `<a class="nav-link">`, not to the `<li>`.

## Sub-components

| Component  | Renders                                                  |
| ---------- | -------------------------------------------------------- |
| `Nav:Item` | `<li class="nav-item">` around an `<a class="nav-link">` |
