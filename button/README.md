# Button

Renders a `<button type="button">`, or an `<a role="button">` when `href` is set.

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

Put an icon before the label, with the `icon` class so Tabler spaces it. `iconOnly` removes the label padding: give
the button an `aria-label`.

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

| Prop          | Type    | Default     | Description                                                                                                  |
| ------------- | ------- | ----------- | ------------------------------------------------------------------------------------------------------------ |
| `variant`     | string  | `'primary'` | `default` (neutral) `primary` `secondary` `success` `danger` `warning` `info` `dark` `light`                 |
| `appearance`  | string  | `'filled'`  | `filled` `outline` `ghost` `link` (`btn-link`) `action` (`btn-action`); `link` and `action` ignore `variant` |
| `size`        | string  | `'md'`      | `sm` `md` `lg` `xl`                                                                                          |
| `href`        | string? | `null`      | Renders `<a href role="button">` instead of `<button>`                                                       |
| `type`        | string  | `'button'`  | `button` `submit` `reset`, ignored for links                                                                 |
| `pill`        | bool    | `false`     | Fully rounded corners (`btn-pill`)                                                                           |
| `square`      | bool    | `false`     | No border radius (`btn-square`)                                                                              |
| `iconOnly`    | bool    | `false`     | Icon-only button (`btn-icon`)                                                                                |
| `loading`     | bool    | `false`     | Spinner instead of the label (`btn-loading`)                                                                 |
| `block`       | bool    | `false`     | Full width (`w-100`)                                                                                         |
| `disabled`    | bool    | `false`     | `disabled` attribute on `<button>`; `disabled` class, `aria-disabled` and `tabindex` on `<a>`                |
| `floating`    | bool    | `false`     | Pinned to the bottom corner of the viewport (`btn-floating`)                                                 |
| `animateIcon` | string? | `null`      | Animates the icon on hover: `pulse` `rotate` `shake` `tada` `move-start` (`btn-animate-icon-*`)              |

Other attributes go to the `<button>` or `<a>`. The children are the label.
