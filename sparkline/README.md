# Sparkline

A tiny inline SVG chart, drawn by `tabler.js` from data attributes: no chart library needed. Requires Tabler 1.6+.

```twig {"preview":true}
<twig:Tabler:Sparkline values="3,4,2,6,5,8,7" variant="primary" aria-label="Requests per minute, last 7 hours" />
```

`tabler.js` draws the sparklines already in the page when it loads. For content added later (a Turbo frame, a Live
Component render), draw it with `tabler.Sparkline.getOrCreateInstance(element)`.

## Installation

::: installation

## Accessibility

The SVG that `tabler.js` draws is hidden from assistive technology: give the sparkline an `aria-label` describing the
data. It then gets `role="img"`.

## Values

`values` takes a comma-separated string or a Twig array:

```twig {"preview":true}
{% set latency = [124, 118, 131, 97, 102, 140, 126] %}
<twig:Tabler:Sparkline values="{{ latency }}" variant="indigo" aria-label="P99 latency, last 7 days" />
```

## Types

`type` picks the chart: `line` (the default), `bar`, `tristate` and `circle`:

```twig {"preview":true}
<div class="d-flex gap-4 align-items-center">
    <twig:Tabler:Sparkline values="120,132,101,134,90,230,210" variant="primary" aria-label="Latency trend" />
    <twig:Tabler:Sparkline type="bar" values="8,12,6,14,10,16,9" variant="azure" aria-label="Deploys per day" />
    <twig:Tabler:Sparkline type="tristate" values="1,1,-1,0,1,-1,1,1" variant="green" aria-label="Health checks: 5 up, 2 down, 1 skipped" />
    <twig:Tabler:Sparkline type="circle" values="72" variant="teal" aria-label="Disk usage: 72%" />
</div>
```

- **`line`**: a polyline through the values.
- **`bar`**: one bar per value, from zero. Negative values are drawn in red, below a gray zero line.
- **`tristate`**: win/loss bars. A positive value draws an upper bar, a negative one a red lower bar, zero a small
  tick.
- **`circle`**: a progress ring for the first value, out of `max`. Always square.

## Line options

`fill` tints the area under the line. `spot` marks one value with a dot: the `last`, the `min` or the `max`:

```twig {"preview":true}
<div class="d-flex gap-4">
    <twig:Tabler:Sparkline values="3,4,2,6,5,8,7" variant="primary" fill="{{ true }}" aria-label="Requests, with fill" />
    <twig:Tabler:Sparkline values="3,4,2,6,5,8,7" variant="primary" spot="last" aria-label="Requests, last value marked" />
    <twig:Tabler:Sparkline values="3,4,2,6,5,8,7" variant="red" spot="min" aria-label="Requests, minimum marked" />
    <twig:Tabler:Sparkline values="3,4,2,6,5,8,7" variant="green" spot="max" aria-label="Requests, maximum marked" />
</div>
```

## Range and threshold

By default the chart fits its values. `min` and `max` fix the range, to compare charts or to show a percentage on its
full scale. `threshold` draws a dashed guide line at that value:

```twig {"preview":true}
<div class="d-flex gap-4">
    <twig:Tabler:Sparkline values="62,64,61,63,65" variant="primary" aria-label="CPU, auto range" />
    <twig:Tabler:Sparkline values="62,64,61,63,65" variant="primary" min="0" max="100" aria-label="CPU, 0 to 100%" />
    <twig:Tabler:Sparkline values="62,64,61,63,65" variant="primary" min="0" max="100" threshold="80" aria-label="CPU, alert at 80%" />
</div>
```

## Bars

Bars below the `threshold` are drawn in red, like negative values. `barGap` sets the space between the bars and
`barRadius` their corner rounding, both in SVG units (2 by default):

```twig {"preview":true}
<div class="d-flex gap-4">
    <twig:Tabler:Sparkline type="bar" values="4,-2,3,5,-1,6" variant="green" aria-label="Net new users per day" />
    <twig:Tabler:Sparkline type="bar" values="180,220,310,260,190,340" variant="azure" threshold="250" aria-label="Response time, SLO at 250 ms" />
    <twig:Tabler:Sparkline type="bar" values="8,12,6,14,10,16" variant="purple" barGap="4" barRadius="0" aria-label="Deploys per day" />
</div>
```

## Circle

The ring shows the first value out of `max` (100 by default), from `min` (0 by default). `label` prints a text in the
center; `auto` prints the percentage:

```twig {"preview":true}
<div class="d-flex gap-4 align-items-center">
    <twig:Tabler:Sparkline type="circle" values="72" size="lg" label="auto" variant="green" aria-label="Uptime goal: 72% reached" />
    <twig:Tabler:Sparkline type="circle" values="38" max="64" size="lg" label="auto" variant="orange" aria-label="Memory: 38 of 64 GB" />
    <twig:Tabler:Sparkline type="circle" values="9" max="12" size="lg" label="9/12" variant="primary" aria-label="9 of 12 nodes healthy" />
</div>
```

`label` works on every type, and the text is centered over the chart. On the other types, `auto` prints the last
value.

## Sizes

`size` is `sm`, `md` (the default) or `lg`. `square` makes the width equal to the height:

```twig {"preview":true}
<div class="d-flex gap-4 align-items-center">
    <twig:Tabler:Sparkline values="3,4,2,6,5,8,7" size="sm" variant="primary" aria-label="Small" />
    <twig:Tabler:Sparkline values="3,4,2,6,5,8,7" variant="primary" aria-label="Medium" />
    <twig:Tabler:Sparkline values="3,4,2,6,5,8,7" size="lg" variant="primary" aria-label="Large" />
    <twig:Tabler:Sparkline type="bar" values="3,4,2,6" size="lg" square="{{ true }}" variant="primary" aria-label="Large, square" />
</div>
```

## Colors

`variant` sets the text color the chart draws with: it takes the same colors as Legend, see
[the list](https://tabler-ux-components.silarhi.dev/components/data/legend/#colors).

```twig {"preview":true}
<div class="d-flex flex-wrap gap-3">
    {% for color in ['primary', 'success', 'danger', 'warning', 'muted', 'purple', 'pink', 'orange', 'lime', 'cyan'] %}
        <twig:Tabler:Sparkline values="3,4,2,6,5,8,7" variant="{{ color }}" aria-label="{{ color }} trend" />
    {% endfor %}
</div>
```

## Disabled

`disabled` greys the chart out:

```twig {"preview":true}
<div class="d-flex gap-4 align-items-center">
    <twig:Tabler:Sparkline values="3,4,2,6,5,8,7" variant="primary" fill="{{ true }}" disabled="{{ true }}" aria-label="Requests (paused)" />
    <twig:Tabler:Sparkline type="circle" values="40" size="lg" label="auto" variant="primary" disabled="{{ true }}" aria-label="Sync: 40% (paused)" />
</div>
```

## Props

| Prop        | Type          | Default  | Description                                                                                      |
| ----------- | ------------- | -------- | ------------------------------------------------------------------------------------------------ |
| `values`    | array\|string | required | The numbers to draw: an array or a comma-separated string                                        |
| `type`      | string        | `'line'` | `line` `bar` `tristate` `circle`                                                                 |
| `variant`   | string?       | `null`   | Text color the chart draws with (`text-{color}`), see [Colors](https://tabler-ux-components.silarhi.dev/components/data/legend/#colors)  |
| `size`      | string        | `'md'`   | `sm` `md` `lg` (`sparkline-sm`, `sparkline-lg`)                                                  |
| `square`    | bool          | `false`  | Width equal to the height (`sparkline-square`), always on for `circle`                           |
| `fill`      | bool          | `false`  | Tinted area under a line                                                                         |
| `spot`      | string?       | `null`   | Marks one value of a line: `last` `min` `max`                                                    |
| `min`       | number?       | `null`   | Bottom of the value range; for `circle`, the 0% value                                            |
| `max`       | number?       | `null`   | Top of the value range; for `circle`, the 100% value                                             |
| `threshold` | number?       | `null`   | Dashed guide line at this value; bars below it are drawn in red                                  |
| `label`     | string?       | `null`   | Text centered over the chart; `auto` prints the percentage of a circle, the last value otherwise |
| `barGap`    | number?       | `null`   | Space between bars, in SVG units (`tabler.js` default: 2)                                        |
| `barRadius` | number?       | `null`   | Bar corner rounding, in SVG units (`tabler.js` default: 2)                                       |
| `disabled`  | bool          | `false`  | Greys the chart out (`sparkline-disabled`)                                                       |

The props become `data-bs-*` attributes of a `<span class="sparkline" data-bs-toggle="sparkline">`. Other attributes
go to that element too; with an `aria-label`, it gets `role="img"`.
