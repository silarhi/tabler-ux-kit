# Ribbon

Flags a card. The ribbon is absolutely positioned, so place it inside a positioned parent such as a
[Card](https://tabler-ux-components.silarhi.dev/components/content/card/).

```twig {"preview":true}
<twig:Tabler:Card>
    <twig:Tabler:Ribbon variant="success">New</twig:Tabler:Ribbon>
    <twig:Tabler:Card:Body>
        <twig:Tabler:Card:Title>Pro plan</twig:Tabler:Card:Title>
        <p class="text-secondary mb-0">Unlimited projects and deployments.</p>
    </twig:Tabler:Card:Body>
</twig:Tabler:Card>
```

## Installation

::: installation

## Positions

`position` is `end` (the default, the top-right corner), `start`, `top`, `top-start`, `bottom` or `bottom-start`:

```twig {"preview":true}
<div class="row row-cards">
    {% for position in ['end', 'start', 'top', 'top-start', 'bottom', 'bottom-start'] %}
        <div class="col-sm-4">
            <twig:Tabler:Card>
                <twig:Tabler:Ribbon variant="primary" position="{{ position }}"><twig:Tabler:Icon name="star" /></twig:Tabler:Ribbon>
                <twig:Tabler:Card:Body class="py-5 text-center">{{ position }}</twig:Tabler:Card:Body>
            </twig:Tabler:Card>
        </div>
    {% endfor %}
</div>
```

## Bookmark

`bookmark` turns the ribbon into a bookmark with a notched end:

```twig {"preview":true}
<div class="row row-cards">
    <div class="col-sm-6">
        <twig:Tabler:Card>
            <twig:Tabler:Ribbon variant="warning" bookmark="{{ true }}"><twig:Tabler:Icon name="star" /></twig:Tabler:Ribbon>
            <twig:Tabler:Card:Body class="py-5 text-center">Bookmark, end</twig:Tabler:Card:Body>
        </twig:Tabler:Card>
    </div>
    <div class="col-sm-6">
        <twig:Tabler:Card>
            <twig:Tabler:Ribbon variant="danger" position="top-start" bookmark="{{ true }}"><twig:Tabler:Icon name="flame" /></twig:Tabler:Ribbon>
            <twig:Tabler:Card:Body class="py-5 text-center">Bookmark, top start</twig:Tabler:Card:Body>
        </twig:Tabler:Card>
    </div>
</div>
```

## Variants

Without `variant`, the ribbon uses Tabler's default color, the primary one.

```twig {"preview":true}
<div class="row row-cards">
    {% for variant in ['primary', 'success', 'danger', 'dark'] %}
        <div class="col-6 col-sm-3">
            <twig:Tabler:Card>
                <twig:Tabler:Ribbon variant="{{ variant }}">{{ variant|slice(0, 3)|upper }}</twig:Tabler:Ribbon>
                <twig:Tabler:Card:Body class="py-5 text-center">{{ variant }}</twig:Tabler:Card:Body>
            </twig:Tabler:Card>
        </div>
    {% endfor %}
</div>
```

## Props

| Prop       | Type    | Default | Description                                                                          |
| ---------- | ------- | ------- | ------------------------------------------------------------------------------------ |
| `variant`  | string? | `null`  | Background: `primary` `secondary` `success` `danger` `warning` `info` `dark` `light` |
| `position` | string  | `'end'` | `end` `start` `top` `top-start` `bottom` `bottom-start`                              |
| `bookmark` | bool    | `false` | Bookmark style (`ribbon-bookmark`)                                                   |

Other attributes go to the root `<div class="ribbon">`. Any other `variant` value renders no color class.

## Blocks

| Block     | Default                                       |
| --------- | --------------------------------------------- |
| `content` | Empty: the children, a short label or an icon |
