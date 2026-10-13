# Carousel

A slideshow driven by the Bootstrap JavaScript bundled in `tabler.js`, with no other library. Give it an `id`: the
controls and the indicators target it.

```twig {"preview":true}
<twig:Tabler:Carousel id="carousel-default" controls indicators="3">
    <twig:Tabler:Carousel:Item active><img class="d-block w-100" src="/examples/photo-1.jpg" alt="Office"></twig:Tabler:Carousel:Item>
    <twig:Tabler:Carousel:Item><img class="d-block w-100" src="/examples/photo-2.jpg" alt="Workspace"></twig:Tabler:Carousel:Item>
    <twig:Tabler:Carousel:Item><img class="d-block w-100" src="/examples/photo-3.jpg" alt="Meeting room"></twig:Tabler:Carousel:Item>
</twig:Tabler:Carousel>
```

`controls` adds the previous and next arrows, `indicators` takes the number of slides and renders one indicator per
slide. Mark exactly one `Carousel:Item` as `active`.

## Installation

::: installation

## Captions

Put a `Carousel:Caption` in a slide. `background` adds a dark overlay behind the text, so it stays readable on light
photos:

```twig {"preview":true}
<twig:Tabler:Carousel id="carousel-captions" controls>
    <twig:Tabler:Carousel:Item active>
        <img class="d-block w-100" src="/examples/photo-1.jpg" alt="">
        <twig:Tabler:Carousel:Caption background>
            <h3>Paris office</h3>
            <p>Our new headquarters, opened in March.</p>
        </twig:Tabler:Carousel:Caption>
    </twig:Tabler:Carousel:Item>
    <twig:Tabler:Carousel:Item>
        <img class="d-block w-100" src="/examples/photo-2.jpg" alt="">
        <twig:Tabler:Carousel:Caption background>
            <h3>Open space</h3>
            <p>Room for 40 people.</p>
        </twig:Tabler:Carousel:Caption>
    </twig:Tabler:Carousel:Item>
</twig:Tabler:Carousel>
```

## Indicator styles

`indicatorStyle` sets the look of the indicators: `default` (bars), `dots` or `thumb`. `vertical` stacks them on the
right:

```twig {"preview":true}
<twig:Tabler:Carousel id="carousel-dots" indicators="3" indicatorStyle="dots" class="mb-4">
    <twig:Tabler:Carousel:Item active><img class="d-block w-100" src="/examples/photo-1.jpg" alt=""></twig:Tabler:Carousel:Item>
    <twig:Tabler:Carousel:Item><img class="d-block w-100" src="/examples/photo-2.jpg" alt=""></twig:Tabler:Carousel:Item>
    <twig:Tabler:Carousel:Item><img class="d-block w-100" src="/examples/photo-3.jpg" alt=""></twig:Tabler:Carousel:Item>
</twig:Tabler:Carousel>
<twig:Tabler:Carousel id="carousel-vertical" indicators="3" indicatorStyle="dots" vertical>
    <twig:Tabler:Carousel:Item active><img class="d-block w-100" src="/examples/photo-1.jpg" alt=""></twig:Tabler:Carousel:Item>
    <twig:Tabler:Carousel:Item><img class="d-block w-100" src="/examples/photo-2.jpg" alt=""></twig:Tabler:Carousel:Item>
    <twig:Tabler:Carousel:Item><img class="d-block w-100" src="/examples/photo-3.jpg" alt=""></twig:Tabler:Carousel:Item>
</twig:Tabler:Carousel>
```

## Thumbnails

Thumbnails need an image per indicator, so compose them: override the `indicators` block with `Carousel:Indicators`
and one `Carousel:Indicator` per slide, each with its `image`:

```twig {"preview":true}
<twig:Tabler:Carousel id="carousel-thumbs">
    <twig:block name="indicators">
        <twig:Tabler:Carousel:Indicators target="carousel-thumbs" appearance="thumb">
            <twig:Tabler:Carousel:Indicator target="carousel-thumbs" slideTo="0" image="/examples/photo-1.jpg" active />
            <twig:Tabler:Carousel:Indicator target="carousel-thumbs" slideTo="1" image="/examples/photo-2.jpg" />
            <twig:Tabler:Carousel:Indicator target="carousel-thumbs" slideTo="2" image="/examples/photo-3.jpg" />
        </twig:Tabler:Carousel:Indicators>
    </twig:block>
    <twig:Tabler:Carousel:Item active><img class="d-block w-100" src="/examples/photo-1.jpg" alt=""></twig:Tabler:Carousel:Item>
    <twig:Tabler:Carousel:Item><img class="d-block w-100" src="/examples/photo-2.jpg" alt=""></twig:Tabler:Carousel:Item>
    <twig:Tabler:Carousel:Item><img class="d-block w-100" src="/examples/photo-3.jpg" alt=""></twig:Tabler:Carousel:Item>
</twig:Tabler:Carousel>
```

## Custom controls

Override the `controls` block with `Carousel:Control` to change the labels read by screen readers, or the markup:

```twig {"preview":true}
<twig:Tabler:Carousel id="carousel-controls">
    <twig:Tabler:Carousel:Item active><img class="d-block w-100" src="/examples/photo-1.jpg" alt=""></twig:Tabler:Carousel:Item>
    <twig:Tabler:Carousel:Item><img class="d-block w-100" src="/examples/photo-2.jpg" alt=""></twig:Tabler:Carousel:Item>
    <twig:block name="controls">
        <twig:Tabler:Carousel:Control target="carousel-controls" direction="prev" label="Previous photo" />
        <twig:Tabler:Carousel:Control target="carousel-controls" direction="next" label="Next photo" />
    </twig:block>
</twig:Tabler:Carousel>
```

## Fade, without autoplay

`fade` cross-fades the slides instead of sliding them. The carousel starts cycling on page load; pass
`ride="{{ false }}"` to wait for the user (see [boolean props](https://tabler-ux-components.silarhi.dev/getting-started/composition/#boolean-props)):

```twig {"preview":true}
<twig:Tabler:Carousel id="carousel-fade" fade ride="{{ false }}" controls>
    <twig:Tabler:Carousel:Item active><img class="d-block w-100" src="/examples/photo-1.jpg" alt=""></twig:Tabler:Carousel:Item>
    <twig:Tabler:Carousel:Item><img class="d-block w-100" src="/examples/photo-2.jpg" alt=""></twig:Tabler:Carousel:Item>
    <twig:Tabler:Carousel:Item><img class="d-block w-100" src="/examples/photo-3.jpg" alt=""></twig:Tabler:Carousel:Item>
</twig:Tabler:Carousel>
```

## Props

| Prop             | Type    | Default     | Description                                                               |
| ---------------- | ------- | ----------- | ------------------------------------------------------------------------- |
| `id`             | string? | `null`      | DOM id of the carousel; required for the controls and indicators to work  |
| `fade`           | bool    | `false`     | Cross-fades instead of sliding (`carousel-fade`)                          |
| `ride`           | bool    | `true`      | Starts cycling on page load (`data-bs-ride="carousel"`)                   |
| `controls`       | bool    | `false`     | Renders the previous and next `Carousel:Control`                          |
| `indicators`     | int?    | `null`      | Number of slides: renders that many indicators with `Carousel:Indicators` |
| `indicatorStyle` | string  | `'default'` | `default` `dots` `thumb`, passed to `Carousel:Indicators` as `appearance` |
| `vertical`       | bool    | `false`     | Stacks the indicators vertically (`carousel-indicators-vertical`)         |

Other attributes go to the root `<div class="carousel slide">`.

`Carousel:Item`:

| Prop     | Type | Default | Description                                              |
| -------- | ---- | ------- | -------------------------------------------------------- |
| `active` | bool | `false` | The slide shown first; exactly one item must be `active` |

`Carousel:Caption`:

| Prop         | Type | Default | Description                                                                   |
| ------------ | ---- | ------- | ----------------------------------------------------------------------------- |
| `background` | bool | `false` | Adds a `<div class="carousel-caption-background">` overlay before the caption |

`Carousel:Indicators`:

| Prop         | Type    | Default     | Description                                                                        |
| ------------ | ------- | ----------- | ---------------------------------------------------------------------------------- |
| `target`     | string? | `null`      | `id` of the carousel, passed to the generated indicators                           |
| `count`      | int?    | `null`      | Generates this many `Carousel:Indicator`, the first one active                     |
| `appearance` | string  | `'default'` | `default` `dots` (`carousel-indicators-dot`) `thumb` (`carousel-indicators-thumb`) |
| `vertical`   | bool    | `false`     | Stacks the indicators vertically (`carousel-indicators-vertical`)                  |

`Carousel:Indicator`:

| Prop      | Type    | Default | Description                                                                                     |
| --------- | ------- | ------- | ----------------------------------------------------------------------------------------------- |
| `target`  | string? | `null`  | `id` of the carousel                                                                            |
| `slideTo` | int     | `0`     | Zero-based index of the slide it shows                                                          |
| `active`  | bool    | `false` | Marks the current slide                                                                         |
| `image`   | string? | `null`  | Thumbnail URL, set as background image in a 4:3 box (`ratio ratio-4x3`), for `thumb` indicators |

Other attributes go to the `<button>`. A `style` attribute is merged after the thumbnail `background-image`, so it can
still override it.

`Carousel:Control`:

| Prop        | Type    | Default  | Description                                             |
| ----------- | ------- | -------- | ------------------------------------------------------- |
| `target`    | string? | `null`   | `id` of the carousel                                    |
| `direction` | string  | `'next'` | `prev` `next`                                           |
| `label`     | string? | `null`   | Visually hidden label; defaults to `Previous` or `Next` |

## Sub-components

| Component             | Renders                                                                        |
| --------------------- | ------------------------------------------------------------------------------ |
| `Carousel:Item`       | `<div class="carousel-item">`, one slide                                       |
| `Carousel:Caption`    | `<div class="carousel-caption">`, text over a slide                            |
| `Carousel:Indicators` | `<div class="carousel-indicators">`, the strip of indicators                   |
| `Carousel:Indicator`  | `<button data-bs-slide-to>`, one indicator                                     |
| `Carousel:Control`    | `<a class="carousel-control-prev">` or `-next`, an arrow with its hidden label |

## Blocks

| Block        | Default                                                                      |
| ------------ | ---------------------------------------------------------------------------- |
| `indicators` | `Carousel:Indicators` with `indicators` as `count`, when `indicators` is set |
| `content`    | The slides, inside `<div class="carousel-inner">`                            |
| `controls`   | The previous and next `Carousel:Control`, when `controls`                    |

`Carousel:Control` has a `content` block too: the arrow icon and the hidden label.
