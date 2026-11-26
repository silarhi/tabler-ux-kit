# TextShimmer

A short label, such as "Thinking…", with a band of full color sweeping across it while a task runs. The animation is
CSS only (`.text-shimmer`). Requires Tabler 1.7+.

```twig {"preview":true}
<twig:Tabler:TextShimmer label="Thinking…" />
```

The label itself has to say what is going on: when the user prefers reduced motion, the sweep stops and the text shows
in its full color.

## Installation

::: installation

## Loader

`loader` puts a small spinner before the label (`TextShimmer:Loader`). It sits inside the shimmer, so it takes the
color of the text and dims with it. The tag content replaces only the label, so the loader stays. `live` adds
`role="status"` and `aria-live="polite"`, so screen readers announce the label and its changes:

```twig {"preview":true}
<div class="d-flex flex-column gap-2">
    <twig:Tabler:TextShimmer label="Thinking…" loader="{{ true }}" live="{{ true }}" />
    <twig:Tabler:TextShimmer loader="{{ true }}" live="{{ true }}" class="text-primary">Reading <strong>report.pdf</strong>…</twig:Tabler:TextShimmer>
</div>
```

## Colors

The shimmer is a mask, so the text keeps its own color: combine it with any text color class.

```twig {"preview":true}
<div class="d-flex flex-column gap-2">
    <twig:Tabler:TextShimmer label="Thinking…" />
    <twig:Tabler:TextShimmer label="Thinking…" class="text-secondary" />
    <twig:Tabler:TextShimmer label="Thinking…" class="text-primary" />
    <twig:Tabler:TextShimmer label="Thinking…" class="text-green" />
</div>
```

## Speed and contrast

`--tblr-text-shimmer-duration` sets how long one sweep takes, `--tblr-text-shimmer-opacity` how much the text is
dimmed between sweeps:

```twig {"preview":true}
<div class="d-flex flex-column gap-2">
    <twig:Tabler:TextShimmer label="Fast sweep" style="--tblr-text-shimmer-duration: 1s" />
    <twig:Tabler:TextShimmer label="Slow sweep" style="--tblr-text-shimmer-duration: 4s" />
    <twig:Tabler:TextShimmer label="Less contrast" style="--tblr-text-shimmer-opacity: 0.7" />
</div>
```

## Composed

Place `TextShimmer:Loader` yourself, without the `loader` prop. `tag="div"` renders a block:

```twig {"preview":true}
<twig:Tabler:TextShimmer tag="div" live="{{ true }}" class="text-secondary">
    <twig:Tabler:TextShimmer:Loader />
    Uploading 3 files…
</twig:Tabler:TextShimmer>
```

## Props

| Prop     | Type    | Default  | Description                                                                 |
| -------- | ------- | -------- | --------------------------------------------------------------------------- |
| `tag`    | string  | `'span'` | The element: `span` for inline text, `div` for a block                      |
| `label`  | string? | `null`   | The label                                                                   |
| `loader` | bool    | `false`  | Puts a small spinner before the label (`TextShimmer:Loader`)                |
| `live`   | bool    | `false`  | Announces the label and its changes (`role="status"`, `aria-live="polite"`) |

Other attributes go to the root element.

## Sub-components

| Component            | Renders                                                 |
| -------------------- | ------------------------------------------------------- |
| `TextShimmer:Loader` | `<span class="text-shimmer-loader" aria-hidden="true">` |

## Blocks

| Block     | Default                                       |
| --------- | --------------------------------------------- |
| `loader`  | `TextShimmer:Loader`, when `loader` is set    |
| `content` | The `label` prop; the tag content replaces it |
