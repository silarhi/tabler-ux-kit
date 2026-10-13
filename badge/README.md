# Badge

A short label next to other content: a status, a counter, a tag.

```twig {"preview":true}
<twig:Tabler:Badge:List>
    <twig:Tabler:Badge variant="success">Paid</twig:Tabler:Badge>
    <twig:Tabler:Badge variant="warning">Pending</twig:Tabler:Badge>
    <twig:Tabler:Badge variant="danger">Overdue</twig:Tabler:Badge>
</twig:Tabler:Badge:List>
```

## Installation

::: installation

## Variants

```twig {"preview":true}
{% for variant in ['primary', 'secondary', 'success', 'danger', 'warning', 'info', 'dark', 'light'] %}
    <twig:Tabler:Badge variant="{{ variant }}">{{ variant|capitalize }}</twig:Tabler:Badge>
{% endfor %}
```

## Light

`light` uses a tinted background with colored text (`bg-{variant}-lt`) instead of a filled one:

```twig {"preview":true}
{% for variant in ['primary', 'secondary', 'success', 'danger', 'warning', 'info', 'dark', 'light'] %}
    <twig:Tabler:Badge variant="{{ variant }}" light="{{ true }}">{{ variant|capitalize }}</twig:Tabler:Badge>
{% endfor %}
```

## Outline

`outline` keeps the background transparent and draws a border in the variant color (`badge-outline text-{variant}`):

```twig {"preview":true}
{% for variant in ['primary', 'secondary', 'success', 'danger', 'warning', 'info', 'dark'] %}
    <twig:Tabler:Badge variant="{{ variant }}" outline="{{ true }}">{{ variant|capitalize }}</twig:Tabler:Badge>
{% endfor %}
```

## Pill

`pill` fully rounds the corners, for counters:

```twig {"preview":true}
<twig:Tabler:Badge:List>
    <twig:Tabler:Badge variant="primary" pill="{{ true }}">3</twig:Tabler:Badge>
    <twig:Tabler:Badge variant="danger" pill="{{ true }}">12</twig:Tabler:Badge>
    <twig:Tabler:Badge variant="success" light="{{ true }}" pill="{{ true }}">New</twig:Tabler:Badge>
</twig:Tabler:Badge:List>
```

## Sizes

`size` is `sm`, `md` (the default) or `lg`.

```twig {"preview":true}
<twig:Tabler:Badge:List>
    <twig:Tabler:Badge variant="primary" size="sm">Small</twig:Tabler:Badge>
    <twig:Tabler:Badge variant="primary">Medium</twig:Tabler:Badge>
    <twig:Tabler:Badge variant="primary" size="lg">Large</twig:Tabler:Badge>
</twig:Tabler:Badge:List>
```

## Dots

`dot` renders a small dot with no text (`badge-dot`), as a status marker. Give it an `aria-label`:

```twig {"preview":true}
<twig:Tabler:Badge variant="success" dot="{{ true }}" aria-label="Online" /> api-1
<twig:Tabler:Badge variant="warning" dot="{{ true }}" aria-label="Degraded" /> api-2
<twig:Tabler:Badge variant="danger" dot="{{ true }}" aria-label="Offline" /> db-1
```

## Notifications

`notification` places the badge over the top end corner of its parent (`badge-notification`); the parent needs
`position-relative`. `blink` makes it pulse (`badge-blink`), for a live counter:

```twig {"preview":true}
<twig:Tabler:Button class="position-relative me-3">
    Inbox
    <twig:Tabler:Badge variant="danger" notification="{{ true }}">4</twig:Tabler:Badge>
</twig:Tabler:Button>
<twig:Tabler:Button class="position-relative">
    Alerts
    <twig:Tabler:Badge variant="danger" notification="{{ true }}" blink="{{ true }}" dot="{{ true }}" aria-label="New alerts" />
</twig:Tabler:Button>
```

## Icon only

`iconOnly` makes a square badge that holds only an icon (`badge-icononly`):

```twig {"preview":true}
<twig:Tabler:Badge:List>
    <twig:Tabler:Badge variant="warning" light="{{ true }}" iconOnly="{{ true }}" aria-label="Starred"><twig:Tabler:Icon name="star" /></twig:Tabler:Badge>
    <twig:Tabler:Badge variant="success" light="{{ true }}" iconOnly="{{ true }}" aria-label="Verified"><twig:Tabler:Icon name="check" /></twig:Tabler:Badge>
    <twig:Tabler:Badge variant="danger" light="{{ true }}" iconOnly="{{ true }}" aria-label="Locked"><twig:Tabler:Icon name="lock" /></twig:Tabler:Badge>
</twig:Tabler:Badge:List>
```

## Lists

`Badge:List` spaces several badges in a row and wraps them on narrow screens (`badge-list`):

```twig {"preview":true}
<twig:Tabler:Badge:List>
    <twig:Tabler:Badge variant="primary" light="{{ true }}">php</twig:Tabler:Badge>
    <twig:Tabler:Badge variant="primary" light="{{ true }}">symfony</twig:Tabler:Badge>
    <twig:Tabler:Badge variant="primary" light="{{ true }}">twig</twig:Tabler:Badge>
    <twig:Tabler:Badge variant="primary" light="{{ true }}">doctrine</twig:Tabler:Badge>
</twig:Tabler:Badge:List>
```

## Links

With `href`, the badge renders as an `<a>`:

```twig {"preview":true}
<twig:Tabler:Badge:List>
    <twig:Tabler:Badge href="/tags/php" variant="primary" light="{{ true }}">php</twig:Tabler:Badge>
    <twig:Tabler:Badge href="/tags/symfony" variant="primary" light="{{ true }}">symfony</twig:Tabler:Badge>
    <twig:Tabler:Badge href="/tags/twig" variant="primary" light="{{ true }}">twig</twig:Tabler:Badge>
</twig:Tabler:Badge:List>
```

## Props

| Prop           | Type    | Default     | Description                                                                                                 |
| -------------- | ------- | ----------- | ----------------------------------------------------------------------------------------------------------- |
| `variant`      | string  | `'primary'` | `primary` `secondary` `success` `danger` `warning` `info` `dark` `light`                                    |
| `light`        | bool    | `false`     | Tinted background (`bg-{variant}-lt`) instead of `text-bg-{variant}`                                        |
| `outline`      | bool    | `false`     | Transparent background and a colored border (`badge-outline text-{variant}`); takes precedence over `light` |
| `pill`         | bool    | `false`     | Fully rounded corners (`badge-pill`)                                                                        |
| `size`         | string  | `'md'`      | `sm` `md` `lg`                                                                                              |
| `dot`          | bool    | `false`     | Small dot with no text (`badge-dot`)                                                                        |
| `iconOnly`     | bool    | `false`     | Square badge holding only an icon (`badge-icononly`)                                                        |
| `notification` | bool    | `false`     | Over the top end corner of its parent (`badge-notification`)                                                |
| `blink`        | bool    | `false`     | Pulsing animation (`badge-blink`)                                                                           |
| `href`         | string? | `null`      | Renders an `<a href>` instead of a `<span>`                                                                 |

Other attributes go to the root `<span class="badge">` (or `<a>`). Any other `variant` value renders no color class.

## Sub-components

| Component    | Renders                                              |
| ------------ | ---------------------------------------------------- |
| `Badge:List` | `<div class="badge-list">`: a wrapping row of badges |

## Blocks

| Block     | Default                        |
| --------- | ------------------------------ |
| `content` | Empty: the children, the label |
