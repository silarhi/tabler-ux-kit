# ButtonGroup

Joins its children into one bar with shared borders, Bootstrap's `btn-group`. The root gets `role="group"`: give it an
`aria-label` naming what the buttons control. Pass `variant="default"` to each `Button` for Tabler's neutral look,
since `Button` defaults to `primary`.

```twig {"preview":true}
<twig:Tabler:ButtonGroup aria-label="Invoice actions">
    <twig:Tabler:Button variant="default">Edit</twig:Tabler:Button>
    <twig:Tabler:Button variant="default">Duplicate</twig:Tabler:Button>
    <twig:Tabler:Button variant="default">Archive</twig:Tabler:Button>
</twig:Tabler:ButtonGroup>
```

## Installation

::: installation

## Radio toggles

`ButtonGroup:Toggle` renders a hidden `<input class="btn-check">` followed by its `<label class="btn">`. It is a radio
by default: give the toggles of one group the same `name`. `checked` selects one, `disabled` grays it out:

```twig {"preview":true}
<twig:Tabler:ButtonGroup aria-label="Report period">
    <twig:Tabler:ButtonGroup:Toggle id="period-day" name="period" value="day">Day</twig:Tabler:ButtonGroup:Toggle>
    <twig:Tabler:ButtonGroup:Toggle id="period-week" name="period" value="week" checked="{{ true }}">Week</twig:Tabler:ButtonGroup:Toggle>
    <twig:Tabler:ButtonGroup:Toggle id="period-month" name="period" value="month">Month</twig:Tabler:ButtonGroup:Toggle>
    <twig:Tabler:ButtonGroup:Toggle id="period-year" name="period" value="year" disabled="{{ true }}">Year</twig:Tabler:ButtonGroup:Toggle>
</twig:Tabler:ButtonGroup>
```

The `id` prop is required, since the label points to the input with `for`. The browser handles the selection: no
JavaScript is needed, and the value is submitted with the enclosing form.

## Checkboxes

`type="checkbox"` lets several toggles be on at once. The label comes from the children or from the `label` prop:

```twig {"preview":true}
<twig:Tabler:ButtonGroup aria-label="Notification channels">
    <twig:Tabler:ButtonGroup:Toggle id="channel-email" type="checkbox" name="channels[]" value="email" variant="primary" appearance="outline" checked="{{ true }}" label="Email" />
    <twig:Tabler:ButtonGroup:Toggle id="channel-sms" type="checkbox" name="channels[]" value="sms" variant="primary" appearance="outline" label="SMS" />
    <twig:Tabler:ButtonGroup:Toggle id="channel-push" type="checkbox" name="channels[]" value="push" variant="primary" appearance="outline" checked="{{ true }}" label="Push" />
</twig:Tabler:ButtonGroup>
```

## Variants and appearances

A toggle takes the same `variant` and `appearance` values as `Button`, but defaults to `variant="default"`, the
neutral button. The checked toggle shows the active state of its color:

```twig {"preview":true}
<div class="btn-list">
    <twig:Tabler:ButtonGroup aria-label="Status filter">
        <twig:Tabler:ButtonGroup:Toggle id="status-all" name="status" value="all" variant="primary" checked="{{ true }}">All</twig:Tabler:ButtonGroup:Toggle>
        <twig:Tabler:ButtonGroup:Toggle id="status-paid" name="status" value="paid" variant="primary">Paid</twig:Tabler:ButtonGroup:Toggle>
        <twig:Tabler:ButtonGroup:Toggle id="status-overdue" name="status" value="overdue" variant="primary">Overdue</twig:Tabler:ButtonGroup:Toggle>
    </twig:Tabler:ButtonGroup>
    <twig:Tabler:ButtonGroup aria-label="Customer type">
        <twig:Tabler:ButtonGroup:Toggle id="customer-all" name="customer" value="all" appearance="outline" checked="{{ true }}">All</twig:Tabler:ButtonGroup:Toggle>
        <twig:Tabler:ButtonGroup:Toggle id="customer-company" name="customer" value="company" appearance="outline">Companies</twig:Tabler:ButtonGroup:Toggle>
        <twig:Tabler:ButtonGroup:Toggle id="customer-person" name="customer" value="person" appearance="outline">Individuals</twig:Tabler:ButtonGroup:Toggle>
    </twig:Tabler:ButtonGroup>
    <twig:Tabler:ButtonGroup aria-label="Sort order">
        <twig:Tabler:ButtonGroup:Toggle id="sort-newest" name="sort" value="newest" appearance="ghost" checked="{{ true }}">Newest</twig:Tabler:ButtonGroup:Toggle>
        <twig:Tabler:ButtonGroup:Toggle id="sort-oldest" name="sort" value="oldest" appearance="ghost">Oldest</twig:Tabler:ButtonGroup:Toggle>
    </twig:Tabler:ButtonGroup>
</div>
```

## Sizes

`size` sizes every button of the group (`btn-group-sm`, `btn-group-lg`). Toggles have no size of their own:

```twig {"preview":true}
<div class="btn-list align-items-center">
    <twig:Tabler:ButtonGroup size="sm" aria-label="Small">
        <twig:Tabler:Button variant="default">Previous</twig:Tabler:Button>
        <twig:Tabler:Button variant="default">Next</twig:Tabler:Button>
    </twig:Tabler:ButtonGroup>
    <twig:Tabler:ButtonGroup aria-label="Medium">
        <twig:Tabler:Button variant="default">Previous</twig:Tabler:Button>
        <twig:Tabler:Button variant="default">Next</twig:Tabler:Button>
    </twig:Tabler:ButtonGroup>
    <twig:Tabler:ButtonGroup size="lg" aria-label="Large">
        <twig:Tabler:Button variant="default">Previous</twig:Tabler:Button>
        <twig:Tabler:Button variant="default">Next</twig:Tabler:Button>
    </twig:Tabler:ButtonGroup>
</div>
```

## Vertical

`vertical` stacks the buttons (`btn-group-vertical`, instead of `btn-group`):

```twig {"preview":true}
<twig:Tabler:ButtonGroup vertical="{{ true }}" aria-label="Account sections">
    <twig:Tabler:ButtonGroup:Toggle id="section-profile" name="section" value="profile" checked="{{ true }}">Profile</twig:Tabler:ButtonGroup:Toggle>
    <twig:Tabler:ButtonGroup:Toggle id="section-security" name="section" value="security">Security</twig:Tabler:ButtonGroup:Toggle>
    <twig:Tabler:ButtonGroup:Toggle id="section-billing" name="section" value="billing">Billing</twig:Tabler:ButtonGroup:Toggle>
</twig:Tabler:ButtonGroup>
```

## Icons

Put an icon in the toggle and add the `btn-icon` class. The `class` attribute goes to the `<label>`, the visible
button; every other attribute goes to the `<input>`, so `aria-label` names the input that receives focus:

```twig {"preview":true}
<twig:Tabler:ButtonGroup aria-label="Text alignment">
    <twig:Tabler:ButtonGroup:Toggle id="align-left" name="align" value="left" class="btn-icon" aria-label="Align left" checked="{{ true }}">
        <twig:Tabler:Icon name="align-left" class="icon" />
    </twig:Tabler:ButtonGroup:Toggle>
    <twig:Tabler:ButtonGroup:Toggle id="align-center" name="align" value="center" class="btn-icon" aria-label="Align center">
        <twig:Tabler:Icon name="align-center" class="icon" />
    </twig:Tabler:ButtonGroup:Toggle>
    <twig:Tabler:ButtonGroup:Toggle id="align-right" name="align" value="right" class="btn-icon" aria-label="Align right">
        <twig:Tabler:Icon name="align-right" class="icon" />
    </twig:Tabler:ButtonGroup:Toggle>
</twig:Tabler:ButtonGroup>
```

## Dropdowns

To put a dropdown in a group, give the `Dropdown` the `btn-group` class and `role="group"`. For a split button, put a
`Dropdown:Toggle` with `split` right after the main button, followed by its `Dropdown:Menu`: the group wraps the
dropdown, so no `Dropdown` is needed.

```twig {"preview":true}
<div class="btn-list">
    <twig:Tabler:ButtonGroup aria-label="Order actions">
        <twig:Tabler:Button variant="default">Edit</twig:Tabler:Button>
        <twig:Tabler:Button variant="default">Print</twig:Tabler:Button>
        <twig:Tabler:Dropdown class="btn-group" role="group">
            <twig:Tabler:Dropdown:Toggle>More</twig:Tabler:Dropdown:Toggle>
            <twig:Tabler:Dropdown:Menu>
                <twig:Tabler:Dropdown:Item href="/orders/1042/refund">Refund</twig:Tabler:Dropdown:Item>
                <twig:Tabler:Dropdown:Item href="/orders/1042/cancel" class="text-danger">Cancel order</twig:Tabler:Dropdown:Item>
            </twig:Tabler:Dropdown:Menu>
        </twig:Tabler:Dropdown>
    </twig:Tabler:ButtonGroup>
    <twig:Tabler:ButtonGroup aria-label="Save options">
        <twig:Tabler:Button variant="primary">Save</twig:Tabler:Button>
        <twig:Tabler:Dropdown:Toggle variant="primary" split="{{ true }}" aria-label="More save options" />
        <twig:Tabler:Dropdown:Menu>
            <twig:Tabler:Dropdown:Item>Save as draft</twig:Tabler:Dropdown:Item>
            <twig:Tabler:Dropdown:Item>Save and send</twig:Tabler:Dropdown:Item>
        </twig:Tabler:Dropdown:Menu>
    </twig:Tabler:ButtonGroup>
</div>
```

## Props

| Prop       | Type   | Default | Description                                     |
| ---------- | ------ | ------- | ----------------------------------------------- |
| `vertical` | bool   | `false` | Stacks the buttons (`btn-group-vertical`)       |
| `size`     | string | `'md'`  | `sm` `md` `lg` (`btn-group-sm`, `btn-group-lg`) |

Other attributes go to the root `<div class="btn-group">`. `role="group"` is a default: pass `role` to replace it.

## Sub-components

| Component            | Renders                                                                          |
| -------------------- | -------------------------------------------------------------------------------- |
| `ButtonGroup:Toggle` | `<input class="btn-check" autocomplete="off">` followed by `<label class="btn">` |

`ButtonGroup:Toggle` takes these props:

| Prop         | Type    | Default     | Description                                                                                  |
| ------------ | ------- | ----------- | -------------------------------------------------------------------------------------------- |
| `id`         | string  |             | Input `id`, referenced by the label's `for`. Required                                        |
| `name`       | string? | `null`      | Input `name`, shared by the radios of one group                                              |
| `value`      | string? | `null`      | Input `value`                                                                                |
| `type`       | string  | `'radio'`   | `radio` `checkbox`                                                                           |
| `checked`    | bool    | `false`     | Selected state (`checked` attribute)                                                         |
| `disabled`   | bool    | `false`     | Inactive state (`disabled` attribute)                                                        |
| `label`      | string? | `null`      | Label text, rendered in the `content` block                                                  |
| `variant`    | string  | `'default'` | `default` (neutral) `primary` `secondary` `success` `danger` `warning` `info` `dark` `light` |
| `appearance` | string  | `'filled'`  | `filled` `outline` `ghost`                                                                   |

The `class` attribute goes to the `<label>`, and so do the attributes prefixed with `label:`, such as `label:title` or
`label:data-bs-toggle="tooltip"` for a tooltip on the visible button. Other attributes (`aria-label`, `data-*`,
`required`, `form`…) go to the `<input>`.

## Blocks

| Component            | Block     | Default                          |
| -------------------- | --------- | -------------------------------- |
| `ButtonGroup`        | `content` | Empty: the children, the buttons |
| `ButtonGroup:Toggle` | `content` | The `label` prop                 |
