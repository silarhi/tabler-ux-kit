# Tag

A small bordered label: an active filter, an assignee, a category on a ticket. Group tags with `Tag:List`, which
spaces them in a wrapping row.

```twig {"preview":true}
<twig:Tabler:Tag:List>
    <twig:Tabler:Tag label="Billing" dismissible />
    <twig:Tabler:Tag label="Refund request" dismissible />
    <twig:Tabler:Tag label="Priority" dismissible />
</twig:Tabler:Tag:List>
```

## Installation

::: installation

## Leading media

A tag can start with an icon (`icon`), a small avatar (`avatar`, an image URL), a status dot (`status`) or a checkbox
(`checkbox`, checked with `checked`). Set one of them at a time: when several are set, they all render, in the order
checkbox, avatar, icon, status dot.

```twig {"preview":true}
<twig:Tabler:Tag:List>
    <twig:Tabler:Tag label="Invoices" icon="file-invoice" />
    <twig:Tabler:Tag label="Jane Cooper" avatar="/examples/avatar-1.jpg" />
    <twig:Tabler:Tag label="Online" status="success" />
    <twig:Tabler:Tag label="Suspended" status="danger" />
    <twig:Tabler:Tag label="Unpaid only" checkbox checked />
</twig:Tabler:Tag:List>
```

The icon and the status dot are hidden from assistive technology (`aria-hidden="true"`), so the label has to say what
the status is. The checkbox gets the label as its `aria-label`.

## Badge

`badge` appends a small counter (`Tag:Badge`):

```twig {"preview":true}
<twig:Tabler:Tag:List>
    <twig:Tabler:Tag label="Open" badge="12" />
    <twig:Tabler:Tag label="Pending" badge="4" />
    <twig:Tabler:Tag label="Closed" badge="138" />
</twig:Tabler:Tag:List>
```

## Remove button

`dismissible` adds a remove button at the end (`Tag:Close`). Its `aria-label` is "Remove", followed by the label when
it is set: "Remove Wade Warren". The button does nothing on its own: wire it to your JavaScript (see [Blocks](#blocks)).

```twig {"preview":true}
<twig:Tabler:Tag:List>
    <twig:Tabler:Tag label="Wade Warren" avatar="/examples/avatar-2.jpg" dismissible />
    <twig:Tabler:Tag label="Esther Howard" avatar="/examples/avatar-3.jpg" dismissible />
    <twig:Tabler:Tag label="Paris office" icon="map-pin" dismissible />
</twig:Tabler:Tag:List>
```

## Selectable

The `checkbox` prop renders a checkbox without a `name` or a `value`. To submit the selection with a form, compose the
tag with `Tag:Check`, which takes any attribute of an `<input>`:

```twig {"preview":true}
<form method="get">
    <twig:Tabler:Tag:List>
        <twig:Tabler:Tag>
            <twig:Tabler:Tag:Check name="labels[]" value="bug" checked aria-label="Bug" />
            Bug
        </twig:Tabler:Tag>
        <twig:Tabler:Tag>
            <twig:Tabler:Tag:Check name="labels[]" value="feature" aria-label="Feature request" />
            Feature request
        </twig:Tabler:Tag>
        <twig:Tabler:Tag>
            <twig:Tabler:Tag:Check name="labels[]" value="question" aria-label="Question" />
            Question
        </twig:Tabler:Tag>
    </twig:Tabler:Tag:List>
</form>
```

`Tag:Check` is always a checkbox: a `type` attribute is ignored. Give it an `aria-label`, since the tag text is not a
`<label>` for it.

## Composed

Pass children to build the tag yourself. Children replace the whole content, so the props are ignored:

```twig {"preview":true}
<twig:Tabler:Tag:List>
    <twig:Tabler:Tag>
        <twig:Tabler:Tag:Avatar class="bg-primary-lt">JC</twig:Tabler:Tag:Avatar>
        Jane Cooper
        <twig:Tabler:Tag:Badge>Admin</twig:Tabler:Tag:Badge>
        <twig:Tabler:Tag:Close aria-label="Remove Jane Cooper" />
    </twig:Tabler:Tag>
    <twig:Tabler:Tag>
        <twig:Tabler:Tag:Status variant="warning" />
        Payment pending
    </twig:Tabler:Tag>
</twig:Tabler:Tag:List>
```

`Tag:Avatar` also shows initials, as above, and the remove button needs its own `aria-label`. The tag is a flex row:
each child element and each run of text is spaced by the tag's gap, so keep the text plain.

## Blocks

Override a block to change one part and keep the others. The `close` block is where to add a Stimulus action to the
remove button; set the `aria-label` yourself there:

```twig {"preview":true}
<twig:Tabler:Tag:List>
    <twig:Tabler:Tag label="Status: overdue" status="danger">
        <twig:block name="close">
            <twig:Tabler:Tag:Close aria-label="Remove the overdue filter" data-action="filters#remove" data-filter="status" />
        </twig:block>
    </twig:Tabler:Tag>
    <twig:Tabler:Tag label="Paris office" icon="map-pin">
        <twig:block name="badge"><twig:Tabler:Tag:Badge class="bg-primary-lt">3</twig:Tabler:Tag:Badge></twig:block>
    </twig:Tabler:Tag>
</twig:Tabler:Tag:List>
```

See [Composition](https://tabler-ux-components.silarhi.dev/getting-started/composition/) for how blocks work.

## Props

| Prop          | Type    | Default | Description                                                                             |
| ------------- | ------- | ------- | --------------------------------------------------------------------------------------- |
| `label`       | string? | `null`  | The tag text                                                                            |
| `icon`        | string? | `null`  | Leading Tabler icon or UX Icons name (`tag-icon`)                                       |
| `avatar`      | string? | `null`  | Leading avatar image URL, rendered with `Tag:Avatar`                                    |
| `status`      | string? | `null`  | Leading status dot color, rendered with `Tag:Status`: see its values below              |
| `checkbox`    | bool    | `false` | Leading checkbox, rendered with `Tag:Check`, labelled with `label`                      |
| `checked`     | bool    | `false` | Initial state of that checkbox                                                          |
| `badge`       | string? | `null`  | Counter at the end, rendered with `Tag:Badge`                                           |
| `dismissible` | bool    | `false` | Remove button, rendered with `Tag:Close`, labelled "Remove &lt;label&gt;" (or "Remove") |

Other attributes go to the root `<span class="tag">`.

## Sub-components

| Component    | Renders                                                                                          |
| ------------ | ------------------------------------------------------------------------------------------------ |
| `Tag:List`   | `<div class="tag-list">`: a wrapping row of tags (replaces Tabler's deprecated `tags-list`)      |
| `Tag:Avatar` | `<span class="avatar avatar-xs tag-avatar">`; `image` (default `null`) sets its background image |
| `Tag:Status` | `<span class="badge badge-dot">`, `aria-hidden="true"` by default; `variant` sets the color      |
| `Tag:Check`  | `<input type="checkbox" class="form-check-input tag-check">`; `checked` (default `false`)        |
| `Tag:Badge`  | `<span class="badge tag-badge">`                                                                 |
| `Tag:Close`  | `<button type="button" class="btn-close" aria-label="Remove">`: pass your own `aria-label`       |

`Tag:Status` takes a theme color (`primary` `secondary` `success` `danger` `warning` `info` `dark` `light` `muted`) or
a palette color (`blue` `azure` `indigo` `purple` `pink` `red` `orange` `yellow` `lime` `green` `teal` `cyan`). Any
other value renders no color class. On `Tag:Avatar`, a `style` attribute is merged after the `background-image`, so it
can still override it.

## Blocks

| Block     | Default                                                                 |
| --------- | ----------------------------------------------------------------------- |
| `leading` | The checkbox, avatar, icon and status dot, each when its prop is set    |
| `label`   | The `label` prop                                                        |
| `badge`   | `Tag:Badge` with the `badge` prop, when set                             |
| `close`   | `Tag:Close`, labelled "Remove &lt;label&gt;", when `dismissible` is set |
| `content` | `leading`, `label`, `badge` and `close`: replace it to compose freely   |
