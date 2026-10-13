# Trending

Shows how a value changed: the number, an arrow and a color, on one line. Use it next to a KPI in a card, in a table
cell or in a sentence.

```twig {"preview":true}
<div class="d-flex gap-4">
    <twig:Tabler:Trending value="8" />
    <twig:Tabler:Trending value="-3.5" />
    <twig:Tabler:Trending value="0" />
</div>
```

## Installation

::: installation

## Directions

The direction comes from the sign of `value`. A positive number goes up (green, arrow up), a zero stays neutral (gray,
minus), a negative number goes down (red, arrow down). `value` takes a number or a string, and renders as written, so
keep the sign in it: `+12`, `-4.2`. The minus sign `−` (U+2212) reads as down too, and a zero with a decimal comma,
such as `0,0`, as neutral. A value that is not a number, such as `N/A`, is neutral.

```twig {"preview":true}
<div class="d-flex gap-4">
    <twig:Tabler:Trending value="+12" />
    <twig:Tabler:Trending value="{{ -4.2 }}" />
    <twig:Tabler:Trending value="0.0" />
</div>
```

## Units

`unit` is the text after the value, `%` by default. Pass `unit=""` for a count, and start the unit with a space when
it needs one: `unit=" ms"`.

```twig {"preview":true}
<div class="d-flex gap-4">
    <twig:Tabler:Trending value="+1.2K" unit="" />
    <twig:Tabler:Trending value="-38" unit=" ms" />
    <twig:Tabler:Trending value="+2" unit=" pts" />
</div>
```

## Forcing the direction

`direction` (`up`, `down` or `neutral`) overrides the direction read from the value. Use it for an unsigned value, or
for a change too small to count:

```twig {"preview":true}
<div class="d-flex gap-4">
    <twig:Tabler:Trending value="14" direction="down" />
    <twig:Tabler:Trending value="+0.1" direction="neutral" />
</div>
```

## Accessibility

The arrow is hidden from assistive technology (`aria-hidden="true"`). A visually-hidden prefix spells out the
direction instead: "Increased by", "Decreased by" or "No change,". Screen readers read "Increased by 8%". Pass
`label` to replace the prefix, for example with more context or a translation:

```twig {"preview":true}
<div class="d-flex gap-4">
    <twig:Tabler:Trending value="6" label="Up from last week by" />
    <twig:Tabler:Trending value="-2" label="Down from last week by" />
</div>
```

## In a card

```twig {"preview":true}
<div class="row row-cards">
    <div class="col-sm-6">
        <div class="card">
            <div class="card-body">
                <div class="subheader">Sales</div>
                <div class="d-flex align-items-baseline">
                    <div class="h1 mb-0 me-2">75%</div>
                    <twig:Tabler:Trending value="7" class="me-auto" />
                </div>
                <div class="text-secondary">Conversion rate, last 7 days</div>
            </div>
        </div>
    </div>
    <div class="col-sm-6">
        <div class="card">
            <div class="card-body">
                <div class="subheader">Active users</div>
                <div class="d-flex align-items-baseline">
                    <div class="h1 mb-0 me-2">2,986</div>
                    <twig:Tabler:Trending value="-4" class="me-auto" />
                </div>
                <div class="text-secondary">Compared to the previous 7 days</div>
            </div>
        </div>
    </div>
</div>
```

## Composed

Override the `icon` block to change the arrow, or the `value` block to format the value. Keep `aria-hidden="true"` on
a replacement icon. Overriding `content` replaces all three blocks, the visually-hidden prefix included.

```twig {"preview":true}
<div class="d-flex gap-4">
    <twig:Tabler:Trending value="9">
        <twig:block name="icon"><twig:Tabler:Icon name="trending-up" class="ms-1" aria-hidden="true" /></twig:block>
    </twig:Tabler:Trending>
    <twig:Tabler:Trending value="-5">
        <twig:block name="icon"><twig:Tabler:Icon name="trending-down" class="ms-1" aria-hidden="true" /></twig:block>
    </twig:Tabler:Trending>
</div>
```

## Props

| Prop        | Type          | Default | Description                                                                         |
| ----------- | ------------- | ------- | ----------------------------------------------------------------------------------- |
| `value`     | number/string | `0`     | The change, rendered as written, trimmed. Its sign sets the direction               |
| `unit`      | string        | `'%'`   | Text after the value, `''` for none                                                 |
| `direction` | string?       | `null`  | `up`, `down` or `neutral`, to override the direction read from `value`              |
| `label`     | string?       | `null`  | Visually-hidden prefix, `Increased by`, `Decreased by` or `No change,` when not set |

Other attributes go to the root `<span>`, for example `class="h2 m-0"` for a bigger trend.

## Blocks

| Block     | Default                                                                    |
| --------- | -------------------------------------------------------------------------- |
| `label`   | The visually-hidden prefix                                                 |
| `value`   | `value` followed by `unit`                                                 |
| `icon`    | `arrow-up`, `minus` or `arrow-down` icon, hidden from assistive technology |
| `content` | `label`, `value` and `icon`: replace it to compose freely                  |
