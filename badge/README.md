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

`variant` takes a theme color (`primary` `secondary` `success` `danger` `warning` `info` `dark` `light`) or one of
Tabler's colors: `blue` `azure` `indigo` `purple` `pink` `red` `orange` `yellow` `lime` `green` `teal` `cyan`, filled
with `text-bg-{variant}`:

```twig {"preview":true}
{% for variant in ['primary', 'secondary', 'success', 'danger', 'warning', 'info', 'dark', 'light'] %}
    <twig:Tabler:Badge variant="{{ variant }}">{{ variant|capitalize }}</twig:Tabler:Badge>
{% endfor %}
```

```twig {"preview":true}
{% for variant in ['blue', 'azure', 'indigo', 'purple', 'pink', 'red', 'orange', 'yellow', 'lime', 'green', 'teal', 'cyan'] %}
    <twig:Tabler:Badge variant="{{ variant }}">{{ variant|capitalize }}</twig:Tabler:Badge>
{% endfor %}
```

## White

`white` is a white badge with dark text (`text-bg-white`), for a dark or colored background. It is solid only: with
`light` the badge gets no color class, with `outline` only `badge-outline`, since a white tint or a white border is
unreadable on a light page.

```twig {"preview":true}
<div class="d-flex gap-2 p-3 rounded bg-dark">
    <twig:Tabler:Badge variant="white">New</twig:Tabler:Badge>
    <twig:Tabler:Badge variant="white" pill>12</twig:Tabler:Badge>
</div>
<div class="d-flex gap-2 p-3 mt-2 rounded bg-primary">
    <twig:Tabler:Badge variant="white" icon="check">Verified</twig:Tabler:Badge>
</div>
```

## Light

`light` uses a tinted background with colored text (`bg-{variant}-lt`) instead of a filled one:

```twig {"preview":true}
{% for variant in ['primary', 'secondary', 'success', 'danger', 'warning', 'info', 'dark', 'light', 'purple', 'teal'] %}
    <twig:Tabler:Badge variant="{{ variant }}" light="{{ true }}">{{ variant|capitalize }}</twig:Tabler:Badge>
{% endfor %}
```

## Outline

`outline` keeps the background transparent and draws a border in the variant color (`badge-outline text-{variant}`):

```twig {"preview":true}
{% for variant in ['primary', 'secondary', 'success', 'danger', 'warning', 'info', 'dark', 'purple', 'teal'] %}
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

## Icons

`icon` adds an icon before the label, rendered with [Icon](https://tabler-ux-components.silarhi.dev/components/content/icon/) (so a prefixed `lucide:…` name
works with `symfony/ux-icons`) and Tabler's `icon` class, hidden from assistive technology. The `icon` block replaces
it. With `iconOnly`, the badge needs no children: give it an `aria-label`.

```twig {"preview":true}
<twig:Tabler:Badge:List>
    <twig:Tabler:Badge variant="success" icon="check">Verified</twig:Tabler:Badge>
    <twig:Tabler:Badge variant="warning" light="{{ true }}" icon="clock">Pending</twig:Tabler:Badge>
    <twig:Tabler:Badge variant="danger" outline="{{ true }}" icon="alert-triangle">Failed</twig:Tabler:Badge>
    <twig:Tabler:Badge variant="info" light="{{ true }}" icon="star" iconOnly="{{ true }}" aria-label="Starred" />
</twig:Tabler:Badge:List>
```

## Icon only

`iconOnly` makes a square badge that holds only an icon (`badge-icononly`), from the `icon` prop or the children:

```twig {"preview":true}
<twig:Tabler:Badge:List>
    <twig:Tabler:Badge variant="warning" light="{{ true }}" iconOnly="{{ true }}" aria-label="Starred"><twig:Tabler:Icon name="star" /></twig:Tabler:Badge>
    <twig:Tabler:Badge variant="success" light="{{ true }}" iconOnly="{{ true }}" aria-label="Verified"><twig:Tabler:Icon name="check" /></twig:Tabler:Badge>
    <twig:Tabler:Badge variant="danger" light="{{ true }}" iconOnly="{{ true }}" aria-label="Locked"><twig:Tabler:Icon name="lock" /></twig:Tabler:Badge>
</twig:Tabler:Badge:List>
```

## Tooltip

`tooltip` sets the `title` and `data-bs-toggle="tooltip"` on the badge itself, which `tabler.js` turns into a Bootstrap
tooltip. Unlike a [Tooltip](https://tabler-ux-components.silarhi.dev/components/overlays/tooltip/), it adds no wrapper, so the badge stays a direct child of a
button group or an input group. A `dot` or `iconOnly` badge, which has no text, also gets it as its `aria-label`.
Attributes you pass yourself (`title`, `data-bs-toggle`, `aria-label`) win over the generated ones:

```twig {"preview":true}
<twig:Tabler:Badge variant="success" light="{{ true }}" tooltip="Paid on 3 March">Paid</twig:Tabler:Badge>
<twig:Tabler:Badge variant="warning" light="{{ true }}" icon="clock" iconOnly="{{ true }}" tooltip="Due in 3 days" />
<twig:Tabler:Badge variant="danger" dot="{{ true }}" tooltip="Overdue" /> INV-0042
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

Its `items` renders a badge for each entry, an array of Badge props: `text` (the label, escaped), and the optional
`variant`, `icon`, `light`, `outline`, `pill`, `size`, `href` and `tooltip`:

```twig {"preview":true}
<twig:Tabler:Badge:List items="{{ [
    {text: 'PHP', variant: 'primary', icon: 'brand-php'},
    {text: 'Symfony', variant: 'dark'},
    {text: 'Twig', variant: 'success', light: true},
    {text: 'Tabler', variant: 'info', outline: true, href: '#'},
] }}" />
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

| Prop           | Type    | Default     | Description                                                                                                                                                                                                    |
| -------------- | ------- | ----------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `variant`      | string  | `'primary'` | `primary` `secondary` `success` `danger` `warning` `info` `dark` `light`, a Tabler color `blue` `azure` `indigo` `purple` `pink` `red` `orange` `yellow` `lime` `green` `teal` `cyan`, or `white` (solid only) |
| `light`        | bool    | `false`     | Tinted background (`bg-{variant}-lt`) instead of `text-bg-{variant}`                                                                                                                                           |
| `outline`      | bool    | `false`     | Transparent background and a colored border (`badge-outline text-{variant}`); takes precedence over `light`                                                                                                    |
| `pill`         | bool    | `false`     | Fully rounded corners (`badge-pill`)                                                                                                                                                                           |
| `size`         | string  | `'md'`      | `sm` `md` `lg`                                                                                                                                                                                                 |
| `dot`          | bool    | `false`     | Small dot with no text (`badge-dot`)                                                                                                                                                                           |
| `iconOnly`     | bool    | `false`     | Square badge holding only an icon (`badge-icononly`)                                                                                                                                                           |
| `notification` | bool    | `false`     | Over the top end corner of its parent (`badge-notification`)                                                                                                                                                   |
| `blink`        | bool    | `false`     | Pulsing animation (`badge-blink`)                                                                                                                                                                              |
| `href`         | string? | `null`      | Renders an `<a href>` instead of a `<span>`                                                                                                                                                                    |
| `icon`         | string? | `null`      | Leading icon name, rendered with `Icon` (`icon`)                                                                                                                                                               |
| `tooltip`      | string? | `null`      | Tooltip text (`title`, `data-bs-toggle="tooltip"`); the `aria-label` of a `dot` or `iconOnly` badge                                                                                                            |

Other attributes go to the root `<span class="badge">` (or `<a>`), and win over the generated `title`,
`data-bs-toggle` and `aria-label`. Any other `variant` value renders no color class.

`Badge:List`:

| Prop    | Type   | Default | Description                                                                                                 |
| ------- | ------ | ------- | ----------------------------------------------------------------------------------------------------------- |
| `items` | array? | `null`  | Badges to render: `{text, variant?, icon?, light?, outline?, pill?, size?, href?, tooltip?}`, `Badge` props |

## Sub-components

| Component    | Renders                                              |
| ------------ | ---------------------------------------------------- |
| `Badge:List` | `<div class="badge-list">`: a wrapping row of badges |

## Blocks

| Block     | Default                                                      |
| --------- | ------------------------------------------------------------ |
| `icon`    | A `Tabler:Icon` named `icon` with the `icon` class, when set |
| `content` | Empty: the children, the label                               |

The `content` block of `Badge:List` renders a `Badge` for each entry of `items`; the children replace it.
