# Signal

Shows a level with stepped bars: a priority, a signal strength, a coverage. Requires Tabler 1.6+.

```twig {"preview":true}
<twig:Tabler:Signal value="2" variant="orange" aria-label="Priority: high" />
```

## Installation

::: installation

## Levels

`value` is the number of lit bars, `max` the total number of bars, from 2 to 5 (3 by default):

```twig {"preview":true}
<div class="d-flex gap-4 align-items-end">
    <twig:Tabler:Signal value="1" max="2" variant="primary" aria-label="Level 1 of 2" />
    <twig:Tabler:Signal value="2" max="3" variant="primary" aria-label="Level 2 of 3" />
    <twig:Tabler:Signal value="3" max="4" variant="primary" aria-label="Level 3 of 4" />
    <twig:Tabler:Signal value="4" max="5" variant="primary" aria-label="Level 4 of 5" />
</div>
```

## Colors

`variant` takes the same colors as Legend: see [the list](https://tabler-ux-components.silarhi.dev/components/data/legend/#colors).

```twig {"preview":true}
<div class="d-flex gap-4">
    <twig:Tabler:Signal value="1" variant="green" aria-label="Load: low" />
    <twig:Tabler:Signal value="2" variant="yellow" aria-label="Load: medium" />
    <twig:Tabler:Signal value="3" variant="red" aria-label="Load: high" />
    <twig:Tabler:Signal value="2" variant="muted" aria-label="Load: unknown" />
</div>
```

## Accessibility

Give a standalone signal an `aria-label` stating the level: it then gets `role="img"`. Without one, the signal is
treated as decoration next to a text label and gets `aria-hidden="true"`:

```twig {"preview":true}
<span class="d-inline-flex align-items-center gap-2">
    <twig:Tabler:Signal value="3" max="4" variant="success" />
    Good coverage
</span>
```

## Composed

The tag content replaces the bars: place one `Signal:Bar` per bar and light some with `active`. `value` and `max` are
then ignored:

```twig {"preview":true}
<twig:Tabler:Signal variant="danger" aria-label="Severity: 1 of 4">
    <twig:Tabler:Signal:Bar active="{{ true }}" />
    <twig:Tabler:Signal:Bar />
    <twig:Tabler:Signal:Bar />
    <twig:Tabler:Signal:Bar />
</twig:Tabler:Signal>
```

## Props

| Prop      | Type    | Default | Description                                                          |
| --------- | ------- | ------- | -------------------------------------------------------------------- |
| `value`   | int     | `0`     | Number of lit bars                                                   |
| `max`     | int     | `3`     | Total number of bars, 2 to 5                                         |
| `variant` | string? | `null`  | Color of the lit bars, see [Colors](https://tabler-ux-components.silarhi.dev/components/data/legend/#colors) |

Other attributes go to the root `<span class="signal">`. With an `aria-label`, it gets `role="img"`, otherwise
`aria-hidden="true"`.

### Signal:Bar

| Prop     | Type | Default | Description               |
| -------- | ---- | ------- | ------------------------- |
| `active` | bool | `false` | Lights the bar (`active`) |

## Sub-components

| Component    | Renders                              |
| ------------ | ------------------------------------ |
| `Signal:Bar` | `<span class="signal-bar">`, one bar |

## Blocks

| Block     | Default                                               |
| --------- | ----------------------------------------------------- |
| `content` | `max` × `Signal:Bar`, the first `value` ones `active` |
