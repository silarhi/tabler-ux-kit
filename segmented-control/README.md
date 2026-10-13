# SegmentedControl

A row of segments where one is selected, rendered as Tabler's `nav-segmented`. Each segment is a Bootstrap tab
(`data-bs-toggle="tab"`), so `tabler.js` moves the selection on click. Segments are `<button type="button">`, so they
never submit an enclosing form.

```twig {"preview":true}
<twig:Tabler:SegmentedControl aria-label="Period">
    <twig:Tabler:SegmentedControl:Item active="{{ true }}">Day</twig:Tabler:SegmentedControl:Item>
    <twig:Tabler:SegmentedControl:Item>Week</twig:Tabler:SegmentedControl:Item>
    <twig:Tabler:SegmentedControl:Item>Month</twig:Tabler:SegmentedControl:Item>
</twig:Tabler:SegmentedControl>
```

To show a panel per segment, add `data-bs-target="#pane-id"` to each item; attributes are forwarded to the
`<button>`. Without a target, the control only switches its selected segment: listen to Bootstrap's `shown.bs.tab`
event to react to it.

## Installation

::: installation

## Icons

Put an icon before the label with the `nav-link-icon` class:

```twig {"preview":true}
<twig:Tabler:SegmentedControl aria-label="Layout">
    <twig:Tabler:SegmentedControl:Item active="{{ true }}">
        <twig:Tabler:Icon name="layout-grid" class="nav-link-icon" /> Grid
    </twig:Tabler:SegmentedControl:Item>
    <twig:Tabler:SegmentedControl:Item>
        <twig:Tabler:Icon name="list" class="nav-link-icon" /> List
    </twig:Tabler:SegmentedControl:Item>
</twig:Tabler:SegmentedControl>
```

## Full width

`fullWidth` stretches the control, and its segments, to the width of the container. A segment takes the native
`disabled` attribute:

```twig {"preview":true}
<twig:Tabler:SegmentedControl fullWidth="{{ true }}" aria-label="Invoice status">
    <twig:Tabler:SegmentedControl:Item active="{{ true }}">All</twig:Tabler:SegmentedControl:Item>
    <twig:Tabler:SegmentedControl:Item>Paid</twig:Tabler:SegmentedControl:Item>
    <twig:Tabler:SegmentedControl:Item>Overdue</twig:Tabler:SegmentedControl:Item>
    <twig:Tabler:SegmentedControl:Item disabled>Draft</twig:Tabler:SegmentedControl:Item>
</twig:Tabler:SegmentedControl>
```

## Sizes

```twig {"preview":true}
{% for size in ['sm', 'md', 'lg'] %}
    <div class="mb-3">
        <twig:Tabler:SegmentedControl size="{{ size }}" aria-label="Period">
            <twig:Tabler:SegmentedControl:Item active="{{ true }}">Day</twig:Tabler:SegmentedControl:Item>
            <twig:Tabler:SegmentedControl:Item>Week</twig:Tabler:SegmentedControl:Item>
            <twig:Tabler:SegmentedControl:Item>Month</twig:Tabler:SegmentedControl:Item>
        </twig:Tabler:SegmentedControl>
    </div>
{% endfor %}
```

## Vertical

`vertical` stacks the segments in a column:

```twig {"preview":true}
<twig:Tabler:SegmentedControl vertical="{{ true }}" aria-label="Settings section">
    <twig:Tabler:SegmentedControl:Item active="{{ true }}">
        <twig:Tabler:Icon name="user" class="nav-link-icon" /> Profile
    </twig:Tabler:SegmentedControl:Item>
    <twig:Tabler:SegmentedControl:Item>
        <twig:Tabler:Icon name="bell" class="nav-link-icon" /> Notifications
    </twig:Tabler:SegmentedControl:Item>
    <twig:Tabler:SegmentedControl:Item>
        <twig:Tabler:Icon name="credit-card" class="nav-link-icon" /> Billing
    </twig:Tabler:SegmentedControl:Item>
</twig:Tabler:SegmentedControl>
```

## Props

| Prop        | Type   | Default | Description                                    |
| ----------- | ------ | ------- | ---------------------------------------------- |
| `fullWidth` | bool   | `false` | Stretches to the container (`w-100`)           |
| `vertical`  | bool   | `false` | Stacks the segments (`nav-segmented-vertical`) |
| `size`      | string | `'md'`  | `sm` `md` `lg` (`nav-sm`, `nav-lg`)            |

Other attributes go to the root `<nav role="tablist">`: give it an `aria-label`.

## Sub-components

| Component               | Renders                                                                                         |
| ----------------------- | ----------------------------------------------------------------------------------------------- |
| `SegmentedControl:Item` | `<button type="button" class="nav-link" role="tab" data-bs-toggle="tab">`, with `aria-selected` |

`SegmentedControl:Item` takes one prop:

| Prop     | Type | Default | Description                                                                             |
| -------- | ---- | ------- | --------------------------------------------------------------------------------------- |
| `active` | bool | `false` | The selected segment (`active`, `aria-selected="true"`); the others get `tabindex="-1"` |

Its `type` is `button` unless you pass another one, such as `type="submit"`.
