# Placeholder

Skeleton blocks that stand in for text, buttons or cards while the real content loads.

```twig {"preview":true}
<div class="placeholder-glow">
    <twig:Tabler:Placeholder width="7" />
    <twig:Tabler:Placeholder width="4" />
    <twig:Tabler:Placeholder width="4" />
    <twig:Tabler:Placeholder width="6" />
    <twig:Tabler:Placeholder width="8" />
</div>
```

`width` is a grid column span: `width="7"` adds `col-7`, seven twelfths of the parent's width. Placeholders are
inline blocks, so several of them flow like words in a line of text.

The component renders a `<div>`: keep it out of `<p>` and other inline parents, where the browser would close the
paragraph before it.

## Installation

::: installation

## Sizes

```twig {"preview":true}
<twig:Tabler:Placeholder width="12" size="lg" />
<twig:Tabler:Placeholder width="12" />
<twig:Tabler:Placeholder width="12" size="sm" />
<twig:Tabler:Placeholder width="12" size="xs" />
```

## Animation

Wrap placeholders in `.placeholder-glow` to make them pulse, or in `.placeholder-wave` to sweep a shine across them:

```twig {"preview":true}
<div class="placeholder-glow mb-3">
    <twig:Tabler:Placeholder width="12" />
</div>
<div class="placeholder-wave">
    <twig:Tabler:Placeholder width="12" />
</div>
```

## Loading card

A skeleton of a card, hidden from assistive technology with `aria-hidden`:

```twig {"preview":true}
<twig:Tabler:Card aria-hidden="true">
    <twig:Tabler:Card:Body class="placeholder-glow">
        <twig:Tabler:Placeholder width="6" size="lg" class="mb-3" />
        <twig:Tabler:Placeholder width="7" />
        <twig:Tabler:Placeholder width="4" />
        <twig:Tabler:Placeholder width="4" />
        <twig:Tabler:Placeholder width="6" />
        <twig:Tabler:Placeholder width="8" />
    </twig:Tabler:Card:Body>
</twig:Tabler:Card>
```

## Props

| Prop    | Type    | Default | Description                                                   |
| ------- | ------- | ------- | ------------------------------------------------------------- |
| `width` | int?    | `null`  | Column span, `1` to `12` (`col-*`)                            |
| `size`  | string? | `null`  | `xs` `sm` `lg` (`placeholder-*`); none for the default height |

Other attributes go to the root `<div class="placeholder">`; use a `w-*` class for a width outside the grid.
