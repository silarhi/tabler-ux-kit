# Spinner

A loading indicator for a section, a button or a table that is still fetching data.

```twig {"preview":true}
<twig:Tabler:Spinner label="Loading…" />
```

The `label` is visually hidden: screen readers announce it, nothing shows on screen.

## Installation

::: installation

## Variants

```twig {"preview":true}
{% for variant in ['primary', 'secondary', 'success', 'danger', 'warning', 'info', 'dark', 'light'] %}
    <twig:Tabler:Spinner variant="{{ variant }}" label="Loading…" />
{% endfor %}
```

Without `variant`, the spinner takes the color of the surrounding text.

## Types and sizes

`type="grow"` pulses instead of spinning; `size="sm"` shrinks either type:

```twig {"preview":true}
<twig:Tabler:Spinner type="border" variant="primary" />
<twig:Tabler:Spinner type="border" variant="primary" size="sm" />
<twig:Tabler:Spinner type="grow" variant="success" />
<twig:Tabler:Spinner type="grow" variant="success" size="sm" />
```

## Inline

A small spinner next to a short message:

```twig {"preview":true}
<div class="d-flex align-items-center gap-2 text-secondary">
    <twig:Tabler:Spinner size="sm" />
    Loading invoices…
</div>
```

## Props

| Prop      | Type    | Default    | Description                                                                         |
| --------- | ------- | ---------- | ----------------------------------------------------------------------------------- |
| `type`    | string  | `'border'` | `border` (spinning ring) `grow` (pulsing dot)                                       |
| `variant` | string? | `null`     | `primary` `secondary` `success` `danger` `warning` `info` `dark` `light` (`text-*`) |
| `size`    | string  | `'md'`     | `md` `sm`                                                                           |
| `label`   | string? | `null`     | Visually-hidden text (`<span class="visually-hidden">`)                             |

Other attributes go to the root `<div role="status">`.

## Blocks

| Block     | Default                                     |
| --------- | ------------------------------------------- |
| `content` | The visually-hidden `label`, when it is set |
