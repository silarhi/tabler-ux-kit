# Button

Renders a `<button type="button">`, an `<a role="button">` when `href` is set, or the element named by
[`tag`](#other-elements).

```twig {"preview":true}
<div class="btn-list">
    <twig:Tabler:Button variant="default">Cancel</twig:Tabler:Button>
    <twig:Tabler:Button variant="primary">Save changes</twig:Tabler:Button>
</div>
```

## Installation

::: installation

## Variants

`variant` sets the color. `default` is Tabler's neutral button, a plain `.btn`:

```twig {"preview":true}
<div class="btn-list">
    {% for variant in ['default', 'primary', 'secondary', 'success', 'danger', 'warning', 'info', 'dark', 'light'] %}
        <twig:Tabler:Button variant="{{ variant }}">{{ variant|capitalize }}</twig:Tabler:Button>
    {% endfor %}
</div>
```

## Appearances

`appearance` switches between a filled background, an `outline` border and a `ghost` button that only shows its
background on hover. `link` looks like a link (`btn-link`) and ignores `variant`:

```twig {"preview":true}
{% for appearance in ['filled', 'outline', 'ghost'] %}
    <div class="btn-list mb-2">
        {% for variant in ['default', 'primary', 'success', 'danger'] %}
            <twig:Tabler:Button variant="{{ variant }}" appearance="{{ appearance }}">{{ appearance|capitalize }}</twig:Tabler:Button>
        {% endfor %}
    </div>
{% endfor %}
<div class="btn-list">
    <twig:Tabler:Button appearance="link">Link</twig:Tabler:Button>
</div>
```

`action` is a quiet, square icon button for a card header or a table row (`btn-action`): it ignores `variant` and only
shows a background on hover. Give it an `aria-label`, and group several in
[ButtonActions](https://tabler-ux-components.silarhi.dev/components/actions/button-actions/):

```twig {"preview":true}
<twig:Tabler:ButtonActions>
    <twig:Tabler:Button appearance="action" aria-label="Edit"><twig:Tabler:Icon name="edit" /></twig:Tabler:Button>
    <twig:Tabler:Button appearance="action" aria-label="Share"><twig:Tabler:Icon name="share" /></twig:Tabler:Button>
    <twig:Tabler:Button appearance="action" aria-label="Delete"><twig:Tabler:Icon name="trash" /></twig:Tabler:Button>
</twig:Tabler:ButtonActions>
```

## Sizes

```twig {"preview":true}
<div class="btn-list">
    <twig:Tabler:Button size="sm">Small</twig:Tabler:Button>
    <twig:Tabler:Button size="md">Medium</twig:Tabler:Button>
    <twig:Tabler:Button size="lg">Large</twig:Tabler:Button>
    <twig:Tabler:Button size="xl">Extra large</twig:Tabler:Button>
</div>
```

## Icons

`icon` adds an icon before the label and `iconEnd` one after it. They are rendered with
[Icon](https://tabler-ux-components.silarhi.dev/components/content/icon/), so a name with an icon set prefix (`lucide:circle-check`) works with
`symfony/ux-icons`, and get Tabler's `icon` class (`icon icon-end` for the trailing one), which sizes and spaces them.
Both are hidden from assistive technology. `iconOnly` removes the label padding (`btn-icon`): with `icon`, the button
needs no children, but give it an `aria-label` (or a [`tooltip`](#tooltip), which becomes its label):

```twig {"preview":true}
<div class="btn-list">
    <twig:Tabler:Button icon="plus">New user</twig:Tabler:Button>
    <twig:Tabler:Button variant="default" iconEnd="arrow-right">Next step</twig:Tabler:Button>
    <twig:Tabler:Button variant="default" appearance="outline" icon="download" animateIcon="move-start">Export</twig:Tabler:Button>
    <twig:Tabler:Button variant="success" icon="lucide:circle-check">Approve</twig:Tabler:Button>
    <twig:Tabler:Button variant="danger" icon="trash" iconOnly="{{ true }}" aria-label="Delete" />
</div>
```

The `icon` and `iconEnd` blocks replace the generated icons. You can also put the icon in the children yourself, with
the `icon` class:

```twig {"preview":true}
<div class="btn-list">
    <twig:Tabler:Button variant="primary">
        <twig:Tabler:Icon name="plus" class="icon" /> New user
    </twig:Tabler:Button>
    <twig:Tabler:Button variant="default" appearance="outline">
        <twig:Tabler:Icon name="download" class="icon" /> Export
    </twig:Tabler:Button>
    <twig:Tabler:Button variant="danger" iconOnly="{{ true }}" aria-label="Delete">
        <twig:Tabler:Icon name="trash" class="icon" />
    </twig:Tabler:Button>
    <twig:Tabler:Button variant="default" appearance="ghost" iconOnly="{{ true }}" aria-label="Settings">
        <twig:Tabler:Icon name="settings" class="icon" />
    </twig:Tabler:Button>
</div>
```

`animateIcon` animates the icon when the button is hovered:

```twig {"preview":true}
<div class="btn-list">
    <twig:Tabler:Button variant="default" animateIcon="pulse"><twig:Tabler:Icon name="heart" class="icon" /> Pulse</twig:Tabler:Button>
    <twig:Tabler:Button variant="default" animateIcon="rotate"><twig:Tabler:Icon name="refresh" class="icon" /> Rotate</twig:Tabler:Button>
    <twig:Tabler:Button variant="default" animateIcon="shake"><twig:Tabler:Icon name="bell" class="icon" /> Shake</twig:Tabler:Button>
    <twig:Tabler:Button variant="default" animateIcon="tada"><twig:Tabler:Icon name="star" class="icon" /> Tada</twig:Tabler:Button>
    <twig:Tabler:Button variant="default" animateIcon="move-start"><twig:Tabler:Icon name="arrow-left" class="icon" /> Move start</twig:Tabler:Button>
</div>
```

## Triggers

`modal`, `offcanvas` and `collapse` take the id of the element the button opens, and set Bootstrap's data API:
`data-bs-toggle`, `data-bs-target="#<id>"` and `aria-controls`, plus `aria-expanded="false"` for `collapse` (Bootstrap
updates it on toggle). They work on a link too: Bootstrap reads `data-bs-target` on an `<a>` and prevents its
navigation; set its `href` to `#<id>` so the link still points to the target without JavaScript.

```twig {"preview":true}
<div class="btn-list mb-3">
    <twig:Tabler:Button variant="danger" icon="trash" modal="button-delete-user">Delete user</twig:Tabler:Button>
    <twig:Tabler:Button variant="default" icon="menu-2" offcanvas="button-menu">Menu</twig:Tabler:Button>
    <twig:Tabler:Button variant="default" appearance="outline" icon="filter" collapse="button-filters">Filters</twig:Tabler:Button>
</div>
<div class="collapse" id="button-filters">
    <div class="card card-body">Status, owner and creation date filters.</div>
</div>

<twig:Tabler:Modal id="button-delete-user" title="Delete Jane Doe?" text="She loses access to the workspace immediately." />
<twig:Tabler:Offcanvas id="button-menu" title="Menu" text="Dashboard, projects and settings." />
```

Bootstrap reads a single `data-bs-toggle`, so set only one of them: when several are set, `modal` wins over
`offcanvas`, which wins over `collapse`. An attribute you pass yourself (`data-bs-target=".filters"`,
`aria-expanded="true"`…) wins over the generated one.

## Tooltip

`tooltip` sets the `title` and `data-bs-toggle="tooltip"`, which `tabler.js` turns into a Bootstrap tooltip. On an
`iconOnly` button, it is also the `aria-label`, unless you pass one:

```twig {"preview":true}
<div class="btn-list">
    <twig:Tabler:Button variant="default" tooltip="Saves a draft, visible only to you">Save draft</twig:Tabler:Button>
    <twig:Tabler:Button variant="default" appearance="ghost" icon="settings" iconOnly="{{ true }}" tooltip="Settings" />
    <twig:Tabler:Button variant="default" appearance="ghost" icon="bell" iconOnly="{{ true }}" tooltip="Notifications" aria-label="Notifications, 3 unread" />
</div>
```

A trigger takes precedence: with `modal`, `offcanvas` or `collapse`, `tooltip` only sets the `title`, a native browser
tooltip, since the button cannot carry two `data-bs-toggle`. For a Bootstrap tooltip on a trigger, wrap the button in
a [Tooltip](https://tabler-ux-components.silarhi.dev/components/overlays/tooltip/).

## Shapes

`pill` rounds the corners fully, `square` removes the radius:

```twig {"preview":true}
<div class="btn-list">
    <twig:Tabler:Button variant="primary" pill="{{ true }}">Pill</twig:Tabler:Button>
    <twig:Tabler:Button variant="primary" square="{{ true }}">Square</twig:Tabler:Button>
    <twig:Tabler:Button variant="primary" pill="{{ true }}" iconOnly="{{ true }}" aria-label="Like">
        <twig:Tabler:Icon name="heart" class="icon" />
    </twig:Tabler:Button>
</div>
```

## States

`loading` replaces the label with a spinner. `disabled` sets the `disabled` attribute on a `<button>`; on a link it
adds the `disabled` class, `aria-disabled="true"` and `tabindex="-1"`.

```twig {"preview":true}
<div class="btn-list">
    <twig:Tabler:Button variant="primary" loading="{{ true }}">Deploying</twig:Tabler:Button>
    <twig:Tabler:Button variant="primary" disabled="{{ true }}">Disabled button</twig:Tabler:Button>
    <twig:Tabler:Button href="/invoices" variant="secondary" disabled="{{ true }}">Disabled link</twig:Tabler:Button>
</div>
```

## Links and form buttons

With `href`, the button renders an `<a>` and `type` is ignored. Without it, `type` sets the button type, `button` by
default:

```twig {"preview":true}
<div class="btn-list">
    <twig:Tabler:Button href="/users/42" variant="secondary" appearance="ghost">View profile</twig:Tabler:Button>
    <twig:Tabler:Button type="submit" variant="primary">Create invoice</twig:Tabler:Button>
</div>
```

## Other elements

`tag` picks the element: `button`, `a`, `label` or `span`. Left `null` (the default), it is an `<a>` with `href` and a
`<button>` without; an explicit `tag` wins over `href`. A `label` or a `span` gets no `type`, `href` nor `role`, and
`disabled` sets the `disabled` class and `aria-disabled="true"` on it.

A `label` is the styled trigger of a file input: clicking it opens the file picker, which a `<button>` cannot do. Put
the input inside, hidden with `visually-hidden` so it stays focusable. The `disabled` class only blocks the pointer:
disable the input too.

```twig {"preview":true}
<div class="btn-list">
    <twig:Tabler:Button tag="label" icon="upload">
        <input type="file" name="import" accept=".csv" class="visually-hidden">
        Import a CSV file
    </twig:Tabler:Button>
    <twig:Tabler:Button tag="label" variant="default" appearance="outline" disabled="{{ true }}">
        <input type="file" name="attachment" class="visually-hidden" disabled>
        Attach a file
    </twig:Tabler:Button>
</div>
```

## Full width

```twig {"preview":true}
<twig:Tabler:Button variant="primary" block="{{ true }}">Sign in</twig:Tabler:Button>
```

## Floating

`floating` pins the button to the bottom corner of the viewport (`btn-floating`), for the main action of a page:

```twig {"preview":true}
<twig:Tabler:Button variant="primary" floating="{{ true }}" iconOnly="{{ true }}" aria-label="New ticket">
    <twig:Tabler:Icon name="plus" class="icon" />
</twig:Tabler:Button>
```

## Confetti

Confetti needs no component: `tabler.js` binds it to any element with `data-bs-toggle="confetti"`, and attributes are
forwarded to the button:

```twig {"preview":true}
<twig:Tabler:Button variant="success" data-bs-toggle="confetti" data-bs-count="150">Celebrate</twig:Tabler:Button>
```

## Props

| Prop          | Type    | Default     | Description                                                                                                   |
| ------------- | ------- | ----------- | ------------------------------------------------------------------------------------------------------------- |
| `variant`     | string  | `'primary'` | `default` (neutral) `primary` `secondary` `success` `danger` `warning` `info` `dark` `light`                  |
| `appearance`  | string  | `'filled'`  | `filled` `outline` `ghost` `link` (`btn-link`) `action` (`btn-action`); `link` and `action` ignore `variant`  |
| `size`        | string  | `'md'`      | `sm` `md` `lg` `xl`                                                                                           |
| `href`        | string? | `null`      | Renders `<a href role="button">` instead of `<button>`, unless `tag` names another element                    |
| `tag`         | string? | `null`      | `button` `a` `label` `span`; `null` for `<a>` with `href`, else `<button>`                                    |
| `type`        | string  | `'button'`  | `button` `submit` `reset`, only on a `<button>`                                                               |
| `pill`        | bool    | `false`     | Fully rounded corners (`btn-pill`)                                                                            |
| `square`      | bool    | `false`     | No border radius (`btn-square`)                                                                               |
| `iconOnly`    | bool    | `false`     | Icon-only button (`btn-icon`)                                                                                 |
| `loading`     | bool    | `false`     | Spinner instead of the label (`btn-loading`)                                                                  |
| `block`       | bool    | `false`     | Full width (`w-100`)                                                                                          |
| `disabled`    | bool    | `false`     | `disabled` attribute on `<button>`; `disabled` class and `aria-disabled` on the others, `tabindex` on `<a>`   |
| `floating`    | bool    | `false`     | Pinned to the bottom corner of the viewport (`btn-floating`)                                                  |
| `animateIcon` | string? | `null`      | Animates the icon on hover: `pulse` `rotate` `shake` `tada` `move-start` (`btn-animate-icon-*`)               |
| `icon`        | string? | `null`      | Leading icon name, rendered with `Icon` (`icon`)                                                              |
| `iconEnd`     | string? | `null`      | Trailing icon name, rendered with `Icon` (`icon icon-end`)                                                    |
| `modal`       | string? | `null`      | Id of the modal to open (`data-bs-toggle="modal"`, `data-bs-target`, `aria-controls`)                         |
| `offcanvas`   | string? | `null`      | Id of the offcanvas to open (`data-bs-toggle="offcanvas"`, `data-bs-target`, `aria-controls`)                 |
| `collapse`    | string? | `null`      | Id of the element to toggle (`data-bs-toggle="collapse"`, `data-bs-target`, `aria-controls`, `aria-expanded`) |
| `tooltip`     | string? | `null`      | Tooltip text (`title`, `data-bs-toggle="tooltip"` unless a trigger is set); `aria-label` of an `iconOnly` one |

Other attributes go to the root element, and win over the generated `role`, `data-bs-*`, `aria-*` and `title`.
The children are the label.

## Blocks

| Block     | Default                                                                    |
| --------- | -------------------------------------------------------------------------- |
| `icon`    | A `Tabler:Icon` named `icon` with the `icon` class, when set               |
| `content` | Empty: the children, the label                                             |
| `iconEnd` | A `Tabler:Icon` named `iconEnd` with the `icon icon-end` classes, when set |
