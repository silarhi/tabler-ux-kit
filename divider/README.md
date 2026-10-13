# Divider

Separates two sections. Without children it renders a plain `<hr class="hr">`; with children, a labeled rule
(`hr-text`).

```twig {"preview":true}
<p>Billing address</p>
<twig:Tabler:Divider />
<p>Shipping address</p>
<twig:Tabler:Divider>Or</twig:Tabler:Divider>
<p class="mb-0">Pick up in store</p>
```

## Installation

::: installation

## Positions

`position` aligns the label: `start`, `center` (the default) or `end`.

```twig {"preview":true}
<twig:Tabler:Divider position="start">Start</twig:Tabler:Divider>
<twig:Tabler:Divider>Center</twig:Tabler:Divider>
<twig:Tabler:Divider position="end">End</twig:Tabler:Divider>
```

## Variants

`variant` colors the label (`text-{variant}`):

```twig {"preview":true}
{% for variant in ['primary', 'success', 'danger', 'warning'] %}
    <twig:Tabler:Divider variant="{{ variant }}">{{ variant|capitalize }}</twig:Tabler:Divider>
{% endfor %}
```

## Spaceless

`spaceless` replaces the vertical margin of a labeled divider with a small negative one (`hr-text-spaceless`), for a
label between rows that already have padding, such as list items:

```twig {"preview":true}
<div class="list-group list-group-flush">
    <div class="list-group-item">Invoice INV-0144 sent to Initech</div>
    <div class="list-group-item">Payment of €480.00 received</div>
    <twig:Tabler:Divider spaceless="{{ true }}">Yesterday</twig:Tabler:Divider>
    <div class="list-group-item">Customer Globex updated</div>
    <div class="list-group-item">Invoice INV-0143 sent to Globex</div>
</div>
```

`position`, `variant` and `spaceless` only apply to a labeled divider: the plain `<hr>` ignores them.

## Props

| Prop        | Type    | Default    | Description                                                              |
| ----------- | ------- | ---------- | ------------------------------------------------------------------------ |
| `position`  | string  | `'center'` | `start` `center` `end`: label alignment                                  |
| `variant`   | string? | `null`     | `primary` `secondary` `success` `danger` `warning` `info` `dark` `light` |
| `spaceless` | bool    | `false`    | No vertical margin around the label (`hr-text-spaceless`)                |

Other attributes go to the root `<div class="hr-text">` or `<hr class="hr">`.

## Blocks

| Block     | Default                                                          |
| --------- | ---------------------------------------------------------------- |
| `content` | Empty: the children, the label. Empty or blank renders an `<hr>` |
