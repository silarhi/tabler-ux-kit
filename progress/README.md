# Progress

A progress bar: a storage quota, an upload, a task completion rate.

```twig {"preview":true}
<div class="d-flex mb-2">
    <div>Storage</div>
    <div class="ms-auto">57%</div>
</div>
<twig:Tabler:Progress value="57" label="57% used" />
```

The `label` is visually hidden: show the value next to the bar yourself, as above.

## Installation

::: installation

## Variants

```twig {"preview":true}
{% for variant in ['primary', 'secondary', 'success', 'danger', 'warning', 'info', 'dark', 'light'] %}
    <twig:Tabler:Progress value="{{ 30 + loop.index * 8 }}" variant="{{ variant }}" class="mb-2" />
{% endfor %}
```

## Sizes

```twig {"preview":true}
{% for size in ['sm', 'md', 'lg', 'xl'] %}
    <twig:Tabler:Progress value="64" size="{{ size }}" class="mb-3" />
{% endfor %}
```

## Indeterminate

For work of unknown length, `indeterminate` animates the bar and ignores `value`:

```twig {"preview":true}
<twig:Tabler:Progress indeterminate size="sm" />
```

## Striped

`striped` draws diagonal stripes on the bar, `animated` also moves them:

```twig {"preview":true}
<twig:Tabler:Progress value="45" variant="info" striped="{{ true }}" class="mb-3" />
<twig:Tabler:Progress value="72" variant="success" animated="{{ true }}" label="Import: 72%" />
```

## Stacked

Put several `Progress:Bar` in one track to split it into segments. The children replace the single bar the props
render:

```twig {"preview":true}
<twig:Tabler:Progress size="lg">
    <twig:Tabler:Progress:Bar value="44" variant="primary" label="Databases: 44%" />
    <twig:Tabler:Progress:Bar value="19" variant="info" label="Backups: 19%" />
    <twig:Tabler:Progress:Bar value="9" variant="success" label="Logs: 9%" />
</twig:Tabler:Progress>
```

`separated` adds a gap between the bars:

```twig {"preview":true}
<twig:Tabler:Progress size="lg" separated="{{ true }}">
    <twig:Tabler:Progress:Bar value="44" variant="primary" label="Databases: 44%" />
    <twig:Tabler:Progress:Bar value="19" variant="info" label="Backups: 19%" />
    <twig:Tabler:Progress:Bar value="9" variant="success" label="Logs: 9%" />
</twig:Tabler:Progress>
```

## Labelled segments

`Progress:Stacked` follows Bootstrap 5.3's stacked markup (`progress-stacked`): each `Progress:Segment` is its own
track, sized to its share, with its own `role="progressbar"` and `aria-label`; the fill inside it has no role. Use it
when each segment needs a name,
such as the share of each file type in a storage quota. `separated` adds a gap between the segments
(`progress-separated`):

```twig {"preview":true}
<div class="mb-2">Storage: 72 GB of 100 GB</div>
<twig:Tabler:Progress:Stacked separated="{{ true }}">
    <twig:Tabler:Progress:Segment value="32" label="Photos: 32 GB" />
    <twig:Tabler:Progress:Segment value="28" variant="success" label="Videos: 28 GB" />
    <twig:Tabler:Progress:Segment value="12" variant="warning" label="Documents: 12 GB" />
</twig:Tabler:Progress:Stacked>
```

## Props

| Prop            | Type    | Default     | Description                                                                |
| --------------- | ------- | ----------- | -------------------------------------------------------------------------- |
| `value`         | int?    | `null`      | `0` to `100`: renders a single `Progress:Bar`; no bar when `null`          |
| `variant`       | string  | `'primary'` | Color of the single bar, see `Progress:Bar`                                |
| `size`          | string  | `'md'`      | `sm` `md` `lg` `xl` (`progress-*`)                                         |
| `label`         | string? | `null`      | Visually-hidden text of the single bar (not rendered with `indeterminate`) |
| `indeterminate` | bool    | `false`     | Renders a single indeterminate bar                                         |
| `striped`       | bool    | `false`     | Stripes on the single bar, see `Progress:Bar`                              |
| `animated`      | bool    | `false`     | Animated stripes on the single bar, see `Progress:Bar`                     |
| `separated`     | bool    | `false`     | Gap between stacked bars (`progress-separated`)                            |

Other attributes go to the root `<div class="progress">`.

## Sub-components

| Component          | Renders                                                                                                  |
| ------------------ | -------------------------------------------------------------------------------------------------------- |
| `Progress:Bar`     | `<div class="progress-bar" role="progressbar">`, with its width and `aria-value*` attributes             |
| `Progress:Stacked` | `<div class="progress-stacked">`: a row of `Progress:Segment`s; `separated` (default `false`) adds a gap |
| `Progress:Segment` | `<div class="progress" role="progressbar">` sized to its share, holding a `<div class="progress-bar">`   |

### `Progress:Bar` props

| Prop            | Type    | Default     | Description                                                                        |
| --------------- | ------- | ----------- | ---------------------------------------------------------------------------------- |
| `value`         | int?    | `null`      | `0` to `100`: sets the width and `aria-valuenow`                                   |
| `variant`       | string  | `'primary'` | `primary` `secondary` `success` `danger` `warning` `info` `dark` `light` (`bg-*`)  |
| `label`         | string? | `null`      | Visually-hidden text (`<span class="visually-hidden">`)                            |
| `indeterminate` | bool    | `false`     | Animated bar (`progress-bar-indeterminate`); ignores `value`                       |
| `striped`       | bool    | `false`     | Diagonal stripes (`progress-bar-striped`)                                          |
| `animated`      | bool    | `false`     | Animated stripes (`progress-bar-striped progress-bar-animated`); implies `striped` |

Other attributes go to the bar `<div>`. A `style` is added after the width, so it can override it.

### `Progress:Segment` props

| Prop       | Type    | Default     | Description                                                        |
| ---------- | ------- | ----------- | ------------------------------------------------------------------ |
| `value`    | int     | `0`         | Share of the whole, in percent: sets the width and `aria-valuenow` |
| `variant`  | string  | `'primary'` | Bar color, as for `Progress:Bar`                                   |
| `label`    | string? | `null`      | `aria-label` of the segment; defaults to "`value`% of total"       |
| `striped`  | bool    | `false`     | Diagonal stripes (`progress-bar-striped`)                          |
| `animated` | bool    | `false`     | Animated stripes (`progress-bar-animated`)                         |

Other attributes go to the `<div class="progress">`. A `style` attribute is merged after the width.

## Blocks

| Block                      | Default                                                                                              |
| -------------------------- | ---------------------------------------------------------------------------------------------------- |
| `bar`                      | A `Progress:Bar` from `value`, `variant`, `label`, `striped` and `animated`, or an indeterminate one |
| `content`                  | `bar`: replace it (with children) to stack bars                                                      |
| `content` (`Progress:Bar`) | The visually-hidden `label`, when it is set                                                          |

`Progress:Stacked` has an empty `content` block for its segments. `Progress:Segment` has no block.
