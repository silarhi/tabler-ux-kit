# Tabs

A tab bar that switches between panes already in the page, with the Bootstrap JavaScript bundled in `tabler.js`.

```twig {"preview":true}
<twig:Tabler:Tabs>
    <twig:Tabler:Tabs:Item target="tab-overview" active>Overview</twig:Tabler:Tabs:Item>
    <twig:Tabler:Tabs:Item target="tab-activity">Activity</twig:Tabler:Tabs:Item>
    <twig:Tabler:Tabs:Item target="tab-settings">Settings</twig:Tabler:Tabs:Item>
</twig:Tabler:Tabs>
<twig:Tabler:Tabs:Content class="pt-3">
    <twig:Tabler:Tabs:Pane id="tab-overview" active>Jane Cooper is an admin since March 2024.</twig:Tabler:Tabs:Pane>
    <twig:Tabler:Tabs:Pane id="tab-activity">Signed in 2 hours ago from Paris.</twig:Tabler:Tabs:Pane>
    <twig:Tabler:Tabs:Pane id="tab-settings">Two-factor authentication is enabled.</twig:Tabler:Tabs:Pane>
</twig:Tabler:Tabs:Content>
```

`Tabs` renders the bar, `Tabs:Content` the panes. Each `Tabs:Item` targets the `id` of a `Tabs:Pane`, without the `#`.
Mark the first tab and its pane `active`.

## Installation

::: installation

## Tabs, Nav or Navbar

- **Tabs**: switches between panes in the page, without loading a new page.
- **[Nav](https://tabler-ux-components.silarhi.dev/components/navigation/nav/)**: static navigation, each item links to a URL. Use it when each tab is its own
  page.
- **[Navbar](https://tabler-ux-components.silarhi.dev/components/layout/navbar/)**: the header or sidebar of the app.

## Pills

`pills` swaps the tabs for pills:

```twig {"preview":true}
<twig:Tabler:Tabs pills>
    <twig:Tabler:Tabs:Item target="pills-monthly" active>Monthly</twig:Tabler:Tabs:Item>
    <twig:Tabler:Tabs:Item target="pills-yearly">Yearly</twig:Tabler:Tabs:Item>
</twig:Tabler:Tabs>
<twig:Tabler:Tabs:Content class="pt-3">
    <twig:Tabler:Tabs:Pane id="pills-monthly" active>€29 per user, billed every month.</twig:Tabler:Tabs:Pane>
    <twig:Tabler:Tabs:Pane id="pills-yearly">€290 per user, billed once a year.</twig:Tabler:Tabs:Pane>
</twig:Tabler:Tabs:Content>
```

## Underline, bordered and fill

`underline` swaps the tabs for underlined links. `bordered` draws a border under the whole bar and underlines the active
tab. `fill` makes the tabs share the full width. The panes are left out of this example:

```twig {"preview":true}
<twig:Tabler:Tabs underline class="mb-3">
    <twig:Tabler:Tabs:Item target="underline-members" active>Members</twig:Tabler:Tabs:Item>
    <twig:Tabler:Tabs:Item target="underline-invitations">Invitations</twig:Tabler:Tabs:Item>
    <twig:Tabler:Tabs:Item target="underline-roles">Roles</twig:Tabler:Tabs:Item>
</twig:Tabler:Tabs>
<twig:Tabler:Tabs bordered class="mb-3">
    <twig:Tabler:Tabs:Item target="bordered-members" active>Members</twig:Tabler:Tabs:Item>
    <twig:Tabler:Tabs:Item target="bordered-invitations">Invitations</twig:Tabler:Tabs:Item>
    <twig:Tabler:Tabs:Item target="bordered-roles">Roles</twig:Tabler:Tabs:Item>
</twig:Tabler:Tabs>
<twig:Tabler:Tabs pills fill>
    <twig:Tabler:Tabs:Item target="fill-members" active>Members</twig:Tabler:Tabs:Item>
    <twig:Tabler:Tabs:Item target="fill-invitations">Invitations</twig:Tabler:Tabs:Item>
    <twig:Tabler:Tabs:Item target="fill-roles">Roles</twig:Tabler:Tabs:Item>
</twig:Tabler:Tabs>
```

`pills` wins over `underline` when both are set. `bordered` and `fill` combine with any style.

## In a card

`card` fits the tab bar in a card header. Put the panes in the card body:

```twig {"preview":true}
<div class="card">
    <div class="card-header">
        <twig:Tabler:Tabs card>
            <twig:Tabler:Tabs:Item target="card-details" active>Details</twig:Tabler:Tabs:Item>
            <twig:Tabler:Tabs:Item target="card-history">History</twig:Tabler:Tabs:Item>
        </twig:Tabler:Tabs>
    </div>
    <div class="card-body">
        <twig:Tabler:Tabs:Content>
            <twig:Tabler:Tabs:Pane id="card-details" active>Invoice INV-0142, €1,250.00, due on November 1.</twig:Tabler:Tabs:Pane>
            <twig:Tabler:Tabs:Pane id="card-history">Sent on October 2, paid on October 9.</twig:Tabler:Tabs:Pane>
        </twig:Tabler:Tabs:Content>
    </div>
</div>
```

## Props

`Tabs`:

| Prop        | Type | Default | Description                                                              |
| ----------- | ---- | ------- | ------------------------------------------------------------------------ |
| `pills`     | bool | `false` | Pills (`nav-pills`) instead of tabs (`nav-tabs`)                         |
| `underline` | bool | `false` | Underlined links (`nav-underline`) instead of tabs; ignored with `pills` |
| `bordered`  | bool | `false` | Border under the whole bar, active tab underlined (`nav-bordered`)       |
| `fill`      | bool | `false` | Tabs share the full width (`nav-fill`)                                   |
| `card`      | bool | `false` | Tab bar for a card header (`card-header-tabs`)                           |

Other attributes go to the root `<ul class="nav" role="tablist">`.

`Tabs:Item`:

| Prop     | Type   | Default    | Description                            |
| -------- | ------ | ---------- | -------------------------------------- |
| `target` | string | (required) | `id` of the pane it shows, without `#` |
| `active` | bool   | `false`    | The tab selected first                 |

Other attributes go to the `<a class="nav-link" data-bs-toggle="tab">`, not to the `<li>`.

`Tabs:Pane`:

| Prop     | Type   | Default    | Description                                      |
| -------- | ------ | ---------- | ------------------------------------------------ |
| `id`     | string | (required) | DOM id, matching the `target` of its `Tabs:Item` |
| `active` | bool   | `false`    | The pane shown first (`active show`)             |

Other attributes go to the `<div class="tab-pane">`. `Tabs:Content` has no props: attributes go to its
`<div class="tab-content">`.

## Sub-components

| Component      | Renders                                                                     |
| -------------- | --------------------------------------------------------------------------- |
| `Tabs:Item`    | `<li class="nav-item">` around an `<a href="#target" data-bs-toggle="tab">` |
| `Tabs:Content` | `<div class="tab-content">`, the container of the panes                     |
| `Tabs:Pane`    | `<div class="tab-pane" role="tabpanel">`, one pane                          |
