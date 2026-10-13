# Legend

Names the series of a chart or a progress bar: a colored dot, a label and an optional value. Requires Tabler 1.6+.

```twig {"preview":true}
<twig:Tabler:Legend:List>
    <twig:Tabler:Legend variant="blue" label="Allowed" value="339.0k" />
    <twig:Tabler:Legend variant="red" label="Denied" value="1.2k" />
    <twig:Tabler:Legend variant="yellow" label="Rate limited" value="842" />
</twig:Tabler:Legend:List>
```

Use the `label` prop rather than the tag content: the dot, the label and the value all render inside the `content`
block, and the tag content replaces it (see [Composed](#composed)).

## Installation

::: installation

## Large

`size="lg"` puts the label on top and a big value below. `unit` adds a small unit after the value:

```twig {"preview":true}
<twig:Tabler:Legend:List divided="{{ true }}">
    <twig:Tabler:Legend variant="primary" size="lg" label="P99" value="124" unit="ms" />
    <twig:Tabler:Legend variant="azure" size="lg" label="P95" value="76" unit="ms" />
    <twig:Tabler:Legend variant="teal" size="lg" label="P50" value="31" unit="ms" />
</twig:Tabler:Legend:List>
```

## Colors

`variant` takes the theme colors and the palette colors. [Signal](https://tabler-ux-components.silarhi.dev/components/data/signal/) and
[Sparkline](https://tabler-ux-components.silarhi.dev/components/data/sparkline/) accept the same list.

| Kind    | Colors                                                                                       |
| ------- | -------------------------------------------------------------------------------------------- |
| Theme   | `primary` `secondary` `success` `danger` `warning` `info` `dark` `light` `muted`             |
| Palette | `blue` `azure` `indigo` `purple` `pink` `red` `orange` `yellow` `lime` `green` `teal` `cyan` |

```twig {"preview":true}
<twig:Tabler:Legend:List>
    {% for color in ['primary', 'secondary', 'success', 'danger', 'warning', 'info', 'dark', 'light', 'muted'] %}
        <twig:Tabler:Legend variant="{{ color }}" label="{{ color }}" />
    {% endfor %}
</twig:Tabler:Legend:List>
<twig:Tabler:Legend:List class="mt-3">
    {% for color in ['blue', 'azure', 'indigo', 'purple', 'pink', 'red', 'orange', 'yellow', 'lime', 'green', 'teal', 'cyan'] %}
        <twig:Tabler:Legend variant="{{ color }}" label="{{ color }}" />
    {% endfor %}
</twig:Tabler:Legend:List>
```

## Links and buttons

With `href`, the legend renders an `<a>`, with `button` a `<button type="button">`, for example to toggle a chart
series. `active` keeps the hover background, `off` dims a hidden series:

```twig {"preview":true}
<twig:Tabler:Legend:List>
    <twig:Tabler:Legend variant="green" label="Passed" value="128" href="?status=passed" active="{{ true }}" />
    <twig:Tabler:Legend variant="red" label="Failed" value="4" href="?status=failed" />
    <twig:Tabler:Legend variant="yellow" label="Skipped" value="12" button="{{ true }}" off="{{ true }}" data-series="skipped" />
</twig:Tabler:Legend:List>
```

## Lists

`Legend:List` lays the items out in a row. `vertical` stacks them in a column, `divided` draws a line between them:

```twig {"preview":true}
<twig:Tabler:Legend:List vertical="{{ true }}">
    <twig:Tabler:Legend variant="primary" label="This week" value="2.4M" />
    <twig:Tabler:Legend variant="secondary" label="Last week" value="2.1M" />
</twig:Tabler:Legend:List>
<twig:Tabler:Legend:List vertical="{{ true }}" divided="{{ true }}" class="mt-3">
    <twig:Tabler:Legend variant="green" label="2xx" value="98.1%" />
    <twig:Tabler:Legend variant="orange" label="4xx" value="1.6%" />
    <twig:Tabler:Legend variant="red" label="5xx" value="0.3%" />
</twig:Tabler:Legend:List>
```

## Composed

The tag content replaces the `content` block: place `Legend:Dot`, the label and `Legend:Value` yourself. Put
`Legend:Unit` inside the value, or pass `unit` to `Legend:Value`:

```twig {"preview":true}
<twig:Tabler:Legend variant="indigo" button="{{ true }}">
    <twig:Tabler:Legend:Dot />
    Memory
    <twig:Tabler:Legend:Value>
        3.2 <twig:Tabler:Legend:Unit>GB</twig:Tabler:Legend:Unit>
    </twig:Tabler:Legend:Value>
</twig:Tabler:Legend>
```

## Dot alone

`Legend:Dot` takes the color of its legend. On its own, give it a `variant`, for example to mark a series in a
sentence or a table cell:

```twig {"preview":true}
<p class="mb-0">
    <twig:Tabler:Legend:Dot variant="azure" class="me-1" /> api-eu-1 is the reference region.
</p>
```

## Blocks

Override the `dot`, `label` or `value` block and keep the others:

```twig {"preview":true}
<twig:Tabler:Legend variant="danger" label="Errors" value="0.3" unit="%">
    <twig:block name="label"><strong>Errors</strong></twig:block>
</twig:Tabler:Legend>
```

## Props

| Prop      | Type    | Default | Description                                                                    |
| --------- | ------- | ------- | ------------------------------------------------------------------------------ |
| `variant` | string? | `null`  | Color of the dot, see [Colors](#colors)                                        |
| `size`    | string  | `'md'`  | `md`, or `lg`: label on top, big value below (`legend-lg`)                     |
| `label`   | string? | `null`  | The series name                                                                |
| `value`   | string? | `null`  | Rendered with `Legend:Value`, when set                                         |
| `unit`    | string? | `null`  | Unit after the value, rendered with `Legend:Unit`                              |
| `href`    | string? | `null`  | Renders an `<a href>` instead of a `<span>`                                    |
| `button`  | bool    | `false` | Renders a `<button type="button">` instead of a `<span>` (ignored with `href`) |
| `active`  | bool    | `false` | Keeps the hover background (`active`)                                          |
| `off`     | bool    | `false` | Dims the item, for a hidden series (`legend-off`)                              |

Other attributes go to the root element.

### Legend:List

| Prop       | Type | Default | Description                                            |
| ---------- | ---- | ------- | ------------------------------------------------------ |
| `vertical` | bool | `false` | Stacks the items in a column (`legend-list-vertical`)  |
| `divided`  | bool | `false` | Draws a line between the items (`legend-list-divided`) |

### Legend:Dot

| Prop      | Type    | Default | Description                                                               |
| --------- | ------- | ------- | ------------------------------------------------------------------------- |
| `variant` | string? | `null`  | Color, see [Colors](#colors). Not needed inside a legend, which colors it |

### Legend:Value

| Prop   | Type    | Default | Description                                         |
| ------ | ------- | ------- | --------------------------------------------------- |
| `unit` | string? | `null`  | Unit after the content, rendered with `Legend:Unit` |

## Sub-components

| Component      | Renders                                                              |
| -------------- | -------------------------------------------------------------------- |
| `Legend:List`  | `<div class="legend-list">`, around the legend items                 |
| `Legend:Dot`   | `<span class="legend-dot">`, the colored marker                      |
| `Legend:Value` | `<span class="legend-value">`, the muted value next to the label     |
| `Legend:Unit`  | `<span class="legend-unit">`, a small unit after the value (ms, GB…) |

## Blocks

| Block     | Default                                                               |
| --------- | --------------------------------------------------------------------- |
| `dot`     | `Legend:Dot`                                                          |
| `label`   | The `label` prop, when set                                            |
| `value`   | `Legend:Value` with the `value` and `unit` props, when `value` is set |
| `content` | `dot`, `label` and `value`: replace it to compose freely              |
