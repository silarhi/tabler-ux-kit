# Popover

Wraps its children in a `<span>` carrying Bootstrap's popover data attributes; a click on the children toggles it.
`tabler.js` initializes every `data-bs-toggle="popover"` element on page load; for content added later (a Turbo frame,
a Live Component render), create the popover yourself with `Popover.getOrCreateInstance(element)`
(`import { Popover } from '@tabler/core'`).

```twig {"preview":true}
<twig:Tabler:Popover title="Deployment #318" content="Deployed to production by Jane Doe, 12 minutes ago.">
    <twig:Tabler:Button variant="default">Details</twig:Tabler:Button>
</twig:Tabler:Popover>
```

## Installation

::: installation

## Placements

`title` is optional:

```twig {"preview":true}
<div class="btn-list justify-content-center py-5">
    {% for placement in ['top', 'bottom', 'left', 'right'] %}
        <twig:Tabler:Popover content="Popover on {{ placement }}." placement="{{ placement }}">
            <twig:Tabler:Button variant="default">{{ placement|capitalize }}</twig:Tabler:Button>
        </twig:Tabler:Popover>
    {% endfor %}
</div>
```

The popover flips to the opposite side when there is no room for the requested one.

## Dismiss on next click

By default, only a click on the trigger closes the popover. With `data-bs-trigger="focus"`, any click elsewhere does.
The focus must land on the wrapper itself, so make it focusable with `tabindex="0"` and `role="button"`, and style it
as a button:

```twig {"preview":true}
<twig:Tabler:Popover title="Retry policy" content="Failed jobs are retried 3 times, 5 minutes apart." placement="bottom" data-bs-trigger="focus" tabindex="0" role="button" class="btn">
    What happens on failure?
</twig:Tabler:Popover>
```

## Props

| Prop        | Type    | Default | Description                                         |
| ----------- | ------- | ------- | --------------------------------------------------- |
| `content`   | string  | —       | Body text, required (`data-bs-content`)             |
| `title`     | string? | `null`  | Heading (`data-bs-title`)                           |
| `placement` | string  | `'top'` | `top` `bottom` `left` `right` (`data-bs-placement`) |

Other attributes go to the `<span>`, including Bootstrap options such as `data-bs-trigger` or
`data-bs-custom-class`. The title and the content are escaped: they are plain text.
