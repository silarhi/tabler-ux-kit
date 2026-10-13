# Status

The state of something at a glance: a server, a deployment, a user.

```twig {"preview":true}
<twig:Tabler:Status variant="success" label="Online" />
<twig:Tabler:Status variant="secondary" label="Offline" />
```

## Installation

::: installation

## Variants

`variant` takes a theme color, or `muted`:

```twig {"preview":true}
{% for variant in ['primary', 'secondary', 'success', 'danger', 'warning', 'info', 'dark', 'light', 'muted'] %}
    <twig:Tabler:Status variant="{{ variant }}" label="{{ variant|capitalize }}" />
{% endfor %}
```

It also takes a palette color:

```twig {"preview":true}
{% for color in ['blue', 'azure', 'indigo', 'purple', 'pink', 'red', 'orange', 'yellow', 'lime', 'green', 'teal', 'cyan'] %}
    <twig:Tabler:Status variant="{{ color }}" label="{{ color|capitalize }}" />
{% endfor %}
```

## Dot

`dot` adds a leading dot; `animated` makes it pulse, for something live or in progress:

```twig {"preview":true}
<twig:Tabler:Status variant="success" dot="{{ true }}" label="Deployed" />
<twig:Tabler:Status variant="danger" dot="{{ true }}" animated="{{ true }}" label="Live" />
```

## Lite

`lite` replaces the tinted background with a neutral border, and the text takes the body color: only the dot keeps the
variant color (`status-lite`):

```twig {"preview":true}
<twig:Tabler:Status variant="success" lite="{{ true }}" dot="{{ true }}" label="Paid" />
<twig:Tabler:Status variant="warning" lite="{{ true }}" dot="{{ true }}" label="Pending" />
<twig:Tabler:Status variant="danger" lite="{{ true }}" dot="{{ true }}" label="Overdue" />
```

## Indicator

`Status:Indicator` is a larger, standalone marker (`status-indicator`), e.g. next to a service name on an uptime page.
`animated` makes it pulse. Without an `aria-label`, it is hidden from assistive technology (`aria-hidden="true"`), so
put the state in the text next to it. With an `aria-label`, it gets `role="img"`:

```twig {"preview":true}
<div class="d-flex align-items-center gap-2 mb-2">
    <twig:Tabler:Status:Indicator variant="green" animated="{{ true }}" />
    API: operational
</div>
<div class="d-flex align-items-center gap-2 mb-2">
    <twig:Tabler:Status:Indicator variant="orange" animated="{{ true }}" />
    Database: degraded performance
</div>
<div class="d-flex align-items-center gap-2">
    <twig:Tabler:Status:Indicator variant="red" aria-label="Outage" />
    Search
</div>
```

## Composed

Pass children for rich content, and add the dot with `Status:Dot`. Children replace the whole content, so the `dot`
and `label` props are ignored:

```twig {"preview":true}
<twig:Tabler:Status variant="warning">
    <twig:Tabler:Status:Dot animated="{{ true }}" />
    Deploying <strong>v2.4.0</strong>
</twig:Tabler:Status>
```

## Blocks

To keep the dot and change only the text, override the `label` block:

```twig {"preview":true}
<twig:Tabler:Status variant="info" dot="{{ true }}" label="Queued">
    <twig:block name="label">Queued, position <strong>3</strong></twig:block>
</twig:Tabler:Status>
```

See [Composition](https://tabler-ux-components.silarhi.dev/getting-started/composition/) for how blocks work.

## Props

| Prop       | Type    | Default     | Description                                                                                                                                                                                        |
| ---------- | ------- | ----------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `variant`  | string  | `'primary'` | `primary` `secondary` `success` `danger` `warning` `info` `dark` `light` `muted`, or a palette color: `blue` `azure` `indigo` `purple` `pink` `red` `orange` `yellow` `lime` `green` `teal` `cyan` |
| `dot`      | bool    | `false`     | Leading dot, rendered with `Status:Dot`                                                                                                                                                            |
| `animated` | bool    | `false`     | Pulses the dot (needs `dot`)                                                                                                                                                                       |
| `lite`     | bool    | `false`     | Neutral border and text, only the dot keeps the color (`status-lite`)                                                                                                                              |
| `label`    | string? | `null`      | The status text                                                                                                                                                                                    |

Other attributes go to the root `<span class="status">`.

`Status:Indicator`:

| Prop       | Type    | Default | Description                                        |
| ---------- | ------- | ------- | -------------------------------------------------- |
| `variant`  | string? | `null`  | Any `variant` of `Status` (`status-{variant}`)     |
| `animated` | bool    | `false` | Pulses the indicator (`status-indicator-animated`) |

Other attributes go to the root `<span class="status-indicator">`.

## Sub-components

| Component          | Renders                                                                                       |
| ------------------ | --------------------------------------------------------------------------------------------- |
| `Status:Dot`       | `<span class="status-dot">`; its `animated` prop (default `false`) adds `status-dot-animated` |
| `Status:Indicator` | `<span class="status-indicator">` with three circles: a larger standalone marker              |

## Blocks

| Block     | Default                                                   |
| --------- | --------------------------------------------------------- |
| `dot`     | `Status:Dot`, animated when `animated`, when `dot` is set |
| `label`   | The `label` prop, when set                                |
| `content` | `dot` and `label`: replace it to compose freely           |
