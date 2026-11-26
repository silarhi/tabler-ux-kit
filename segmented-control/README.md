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

## In a form

A segmented control that picks a value is a radio group, not a tab list. Use `SegmentedControl:Option` segments: a
radio (or a checkbox with `type="checkbox"`) followed by its `<label class="nav-link">`, so the checked segment is
submitted with the form. Give the control `role="radiogroup"` and an `aria-label`, or put it in a `<fieldset>` with a
`<legend>`. The [form theme](https://tabler-ux-components.silarhi.dev/getting-started/form-theme/) renders an expanded `ChoiceType` this way with
`choice_style: 'segmented'`.

```twig {"preview":true}
<form>
    <twig:Tabler:SegmentedControl role="radiogroup" aria-label="Billing period">
        <twig:Tabler:SegmentedControl:Option id="billing-monthly" name="billing" value="monthly" label="Monthly" checked />
        <twig:Tabler:SegmentedControl:Option id="billing-yearly" name="billing" value="yearly" label="Yearly" />
        <twig:Tabler:SegmentedControl:Option id="billing-lifetime" name="billing" value="lifetime" icon="infinity" label="Lifetime" />
    </twig:Tabler:SegmentedControl>
</form>
```

Tabler hides the inputs of a segmented control with `display: none`, which takes them out of the keyboard order. The
option adds `btn-check d-block` to the input: hidden but focusable, so <kbd>Tab</kbd> reaches the group and the arrow
keys move the selection. Tabler draws no focus ring on the segment itself.

## Props

| Prop        | Type   | Default | Description                                    |
| ----------- | ------ | ------- | ---------------------------------------------- |
| `fullWidth` | bool   | `false` | Stretches to the container (`w-100`)           |
| `vertical`  | bool   | `false` | Stacks the segments (`nav-segmented-vertical`) |
| `size`      | string | `'md'`  | `sm` `md` `lg` (`nav-sm`, `nav-lg`)            |

Other attributes go to the root `<nav role="tablist">`: give it an `aria-label`. Pass `role="radiogroup"` for
`SegmentedControl:Option` radios.

## Sub-components

| Component                 | Renders                                                                                          |
| ------------------------- | ------------------------------------------------------------------------------------------------ |
| `SegmentedControl:Item`   | `<button type="button" class="nav-link" role="tab" data-bs-toggle="tab">`, with `aria-selected`  |
| `SegmentedControl:Option` | `<input class="nav-link-input btn-check d-block">` and its `<label class="nav-link">`, for forms |

`SegmentedControl:Item` takes one prop:

| Prop     | Type | Default | Description                                                                             |
| -------- | ---- | ------- | --------------------------------------------------------------------------------------- |
| `active` | bool | `false` | The selected segment (`active`, `aria-selected="true"`); the others get `tabindex="-1"` |

Its `type` is `button` unless you pass another one, such as `type="submit"`.

`SegmentedControl:Option` takes these props:

| Prop       | Type   | Default   | Description                                        |
| ---------- | ------ | --------- | -------------------------------------------------- |
| `id`       | string | required  | The input id, referenced by the label's `for`      |
| `name`     | string | `null`    | The input name, shared by the options of a control |
| `value`    | string | `null`    | The input value                                    |
| `type`     | string | `'radio'` | `radio` or `checkbox`                              |
| `checked`  | bool   | `false`   | The selected segment                               |
| `disabled` | bool   | `false`   | An inactive segment                                |
| `label`    | string | `null`    | The label text; children replace it                |
| `icon`     | string | `null`    | An icon before the label (`nav-link-icon`)         |

`class` and the attributes prefixed with `label:` go on the `<label>`; every other attribute (`required`,
`aria-describedby`, `data-*`…) goes on the `<input>`. The `icon` and `content` blocks hold the icon and the label.
