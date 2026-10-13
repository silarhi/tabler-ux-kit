# Tooltip

Wraps its children in a `<span>` carrying Bootstrap's tooltip data attributes. `tabler.js` initializes every
`data-bs-toggle="tooltip"` element on page load; for content added later (a Turbo frame, a Live Component render),
create the tooltip yourself with `Tooltip.getOrCreateInstance(element)` (`import { Tooltip } from '@tabler/core'`).

```twig {"preview":true}
<twig:Tabler:Tooltip title="Send the invoice to the customer">
    <twig:Tabler:Button variant="primary">Send</twig:Tabler:Button>
</twig:Tabler:Tooltip>
```

## Installation

::: installation

## Placements

```twig {"preview":true}
<div class="btn-list justify-content-center py-5">
    {% for placement in ['top', 'bottom', 'left', 'right'] %}
        <twig:Tabler:Tooltip title="Tooltip on {{ placement }}" placement="{{ placement }}">
            <twig:Tabler:Button variant="default">{{ placement|capitalize }}</twig:Tabler:Button>
        </twig:Tabler:Tooltip>
    {% endfor %}
</div>
```

The tooltip flips to the opposite side when there is no room for the requested one.

## On text

The wrapper is an inline `<span>`, so it works on a word or a date as well as on a button:

```twig {"preview":true}
<p>
    Last deployment:
    <twig:Tabler:Tooltip title="2026-10-12 14:32 UTC" class="text-decoration-underline">2 hours ago</twig:Tabler:Tooltip>
</p>
```

## On a disabled button

A disabled button fires no mouse event, but its wrapper still does. Make the wrapper focusable with `tabindex="0"`
and `d-inline-block`, so keyboard users get the tooltip too:

```twig {"preview":true}
<twig:Tabler:Tooltip title="Only admins can delete users" class="d-inline-block" tabindex="0">
    <twig:Tabler:Button variant="danger" disabled="{{ true }}">Delete user</twig:Tabler:Button>
</twig:Tabler:Tooltip>
```

## Props

| Prop        | Type   | Default | Description                                         |
| ----------- | ------ | ------- | --------------------------------------------------- |
| `title`     | string | —       | Tooltip text, required (`data-bs-title`)            |
| `placement` | string | `'top'` | `top` `bottom` `left` `right` (`data-bs-placement`) |

Other attributes go to the `<span>`, including Bootstrap options such as `data-bs-trigger`, `data-bs-delay` or
`data-bs-custom-class`. The title is escaped: it is plain text.
