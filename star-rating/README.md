# StarRating

Shows a score as a row of stars: the rating of a review, a product or a supplier. The stars are read-only. Tabler's
interactive star rating, which lets the user pick a score, relies on a third-party JavaScript library and is not
covered.

```twig {"preview":true}
<div class="d-flex align-items-center gap-2">
    <twig:Tabler:StarRating value="4" />
    <span class="text-secondary">4.0 (128 reviews)</span>
</div>
```

## Installation

::: installation

## Values

`value` is the number of colored stars, `max` the total number of stars (5 by default). Stars are whole:
`value="3.5"` colors 3 stars. Round the score yourself and pass the exact one in `aria-label`:

```twig {"preview":true}
<div class="d-flex flex-column gap-2">
    <twig:Tabler:StarRating value="5" />
    <twig:Tabler:StarRating value="3" />
    <twig:Tabler:StarRating value="{{ 4.6|round }}" aria-label="4.6 out of 5" />
    <twig:Tabler:StarRating value="7" max="10" />
</div>
```

## Colors

`variant` colors the active stars, `yellow` by default. It takes the same colors as Legend: see
[the list](https://tabler-ux-components.silarhi.dev/components/data/legend/#colors). `icon` replaces the star with another Tabler icon. Change the
`aria-label` to match. `filled` uses the filled icons, which need the filled webfont: see
[Icon](https://tabler-ux-components.silarhi.dev/components/content/icon/#filled).

```twig {"preview":true}
<div class="d-flex flex-column gap-2">
    <twig:Tabler:StarRating value="4" variant="orange" />
    <twig:Tabler:StarRating value="4" filled />
    <twig:Tabler:StarRating value="4" variant="primary" />
    <twig:Tabler:StarRating value="3" variant="red" icon="heart" aria-label="3 of 5 hearts" />
    <twig:Tabler:StarRating value="2" variant="green" icon="thumb-up" aria-label="2 of 5" />
</div>
```

## Sizes

The stars follow the font size of the row, `0.75rem` by default. Pass a font size class such as `fs-3`. The
`--tblr-stars-gap` CSS variable sets the space between the stars.

```twig {"preview":true}
<div class="d-flex flex-column gap-2">
    <twig:Tabler:StarRating value="4" />
    <twig:Tabler:StarRating value="4" class="fs-3" />
    <twig:Tabler:StarRating value="4" class="fs-1" />
</div>
```

## Accessibility

The row gets `role="img"` and an `aria-label` such as "4 out of 5". Pass your own `aria-label` to replace it. The
star icons are hidden from assistive technology (`aria-hidden="true"`). Also show the score as text next to the stars,
so it does not rely on color alone:

```twig {"preview":true}
<div class="card">
    <div class="list-group list-group-flush">
        {% for review in [
            {author: 'Camille Martin', product: 'Wireless keyboard', score: 5, text: 'Quiet keys and the battery lasts for weeks.'},
            {author: 'Julien Petit', product: 'USB-C dock', score: 3, text: 'Works well, but the HDMI port only runs at 30 Hz.'},
            {author: 'Sarah Lefèvre', product: 'Office chair', score: 2, text: 'The armrest broke after two months.'},
        ] %}
            <div class="list-group-item">
                <div class="d-flex align-items-center mb-1">
                    <strong class="me-2">{{ review.product }}</strong>
                    <twig:Tabler:StarRating value="{{ review.score }}" />
                    <span class="ms-2 text-secondary small">{{ review.score }}/5</span>
                </div>
                <div>{{ review.text }}</div>
                <div class="text-secondary small">{{ review.author }}</div>
            </div>
        {% endfor %}
    </div>
</div>
```

## Composed

The tag content replaces the stars: place one `StarRating:Star` per star and color some with `active`. `value`,
`max`, `variant`, `icon` and `filled` are then ignored, so give each star its own `variant`, `icon` and `filled`. A
composed rating gets no default label, since it cannot count the stars: pass an `aria-label`, and it gets
`role="img"`.

```twig {"preview":true}
<twig:Tabler:StarRating aria-label="Delivery: 3 out of 4">
    <twig:Tabler:StarRating:Star active variant="azure" icon="truck" />
    <twig:Tabler:StarRating:Star active variant="azure" icon="truck" />
    <twig:Tabler:StarRating:Star active variant="azure" icon="truck" />
    <twig:Tabler:StarRating:Star icon="truck" />
</twig:Tabler:StarRating>
```

## Props

| Prop      | Type   | Default    | Description                                                              |
| --------- | ------ | ---------- | ------------------------------------------------------------------------ |
| `value`   | int    | `0`        | Number of active stars                                                   |
| `max`     | int    | `5`        | Total number of stars; `0` renders none                                  |
| `variant` | string | `'yellow'` | Color of the active stars, see [Colors](https://tabler-ux-components.silarhi.dev/components/data/legend/#colors) |
| `icon`    | string | `'star'`   | Tabler icon name of each star                                            |
| `filled`  | bool   | `false`    | Filled icons, see [Icon](https://tabler-ux-components.silarhi.dev/components/content/icon/#filled)               |

Other attributes go to the root `<div class="stars">`. It gets `role="img"` and an `aria-label` of "`value` out of
`max`", unless you pass your own.

### StarRating:Star

| Prop      | Type   | Default    | Description                                                      |
| --------- | ------ | ---------- | ---------------------------------------------------------------- |
| `active`  | bool   | `false`    | Colors the star with `variant`. Inactive stars stay gray         |
| `variant` | string | `'yellow'` | Color when active, see [Colors](https://tabler-ux-components.silarhi.dev/components/data/legend/#colors) |
| `icon`    | string | `'star'`   | Tabler icon name                                                 |
| `filled`  | bool   | `false`    | Filled icon, see [Icon](https://tabler-ux-components.silarhi.dev/components/content/icon/#filled)        |

Other attributes go to the star `<span>`.

## Sub-components

| Component         | Renders                         |
| ----------------- | ------------------------------- |
| `StarRating:Star` | `<span class="star">`, one star |

## Blocks

| Block                         | Default                                                    |
| ----------------------------- | ---------------------------------------------------------- |
| `content`                     | `max` × `StarRating:Star`, the first `value` ones `active` |
| `content` (`StarRating:Star`) | The `icon`, hidden from assistive technology               |
