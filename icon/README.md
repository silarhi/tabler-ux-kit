# Icon

Renders one of the [Tabler Icons](https://tabler.io/icons) as `<i class="ti ti-{name}">`. It needs the
`@tabler/icons-webfont` stylesheet, see [Installation](https://tabler-ux-components.silarhi.dev/getting-started/installation/).

```twig {"preview":true}
<twig:Tabler:Icon name="server" />
<twig:Tabler:Icon name="users" />
<twig:Tabler:Icon name="file-invoice" />
<twig:Tabler:Icon name="settings" />
```

`name` is the icon name without the `ti-` prefix, as listed on [tabler.io/icons](https://tabler.io/icons).

## Installation

::: installation

## Sizes

Without `size`, the icon follows the font size of its parent. `size` gives it a fixed size, with Tabler's `icon` class:
`sm` (1rem), `md` (2.5rem) or `lg` (3.5rem). `inline` is 1rem and aligned with the text around it:

```twig {"preview":true}
<twig:Tabler:Icon name="server" size="sm" />
<twig:Tabler:Icon name="server" />
<twig:Tabler:Icon name="server" size="md" />
<twig:Tabler:Icon name="server" size="lg" />
<p class="mt-3 mb-0">
    <twig:Tabler:Icon name="clock" size="inline" /> Updated 5 minutes ago
</p>
```

## Filled

`filled` renders the filled variant of the icon (`ti-filled ti-filled-{name}`):

```twig {"preview":true}
<div class="d-flex align-items-center gap-3 fs-1">
    <twig:Tabler:Icon name="star" variant="warning" />
    <twig:Tabler:Icon name="star" variant="warning" filled />
    <twig:Tabler:Icon name="heart" variant="danger" />
    <twig:Tabler:Icon name="heart" variant="danger" filled />
    <twig:Tabler:Icon name="bell" />
    <twig:Tabler:Icon name="bell" filled />
</div>
```

The filled icons are a separate font of `@tabler/icons-webfont` (3.36.1+), and its `tabler-icons-filled.css` reuses
the class names of the outline icons (`ti`, `ti-{name}`), so it cannot be loaded next to them. Compile its SCSS source
under the `ti-filled` prefix instead, here with Webpack Encore's Sass loader (or `symfonycasts/sass-bundle` with
AssetMapper):

```scss
// assets/styles/tabler-icons-filled.scss
@use '@tabler/icons-webfont/dist/tabler-icons-filled.scss' with (
    $ti-prefix: 'ti-filled',
    $ti-font-path: '~@tabler/icons-webfont/dist/fonts'
);
```

`$ti-font-path` points at the font files: adjust it to how your build resolves `node_modules`.

## Icons from symfony/ux-icons

With [Symfony UX Icons](https://symfony.com/bundles/ux-icons/current/index.html) (2.17+ / 3.x) installed, a `name` with
an icon set prefix renders that icon as an inline `<svg>` instead of the webfont: any of the 200,000+ icons of
[Iconify](https://icon-sets.iconify.design/) (`lucide:circle-check`, `mdi:account`, `tabler:check`…), or your own SVG
files in `assets/icons/`. Names without a prefix keep using the webfont, so both can be mixed.

```bash
composer require symfony/ux-icons
```

The `<svg>` gets Tabler's `icon` class, which sizes SVG icons, and the same `variant`, `size` and `animation` classes.
`filled` picks the filled icon of the `tabler` set (`tabler:{name}-filled`) and has no effect on other sets. Every
`icon` prop takes these names too, since the components render it with `Icon`:

```twig {"preview":true}
<div class="d-flex align-items-center gap-3">
    <twig:Tabler:Icon name="tabler:check" variant="success" />
    <twig:Tabler:Icon name="tabler:star" variant="warning" />
    <twig:Tabler:Icon name="tabler:star" variant="warning" filled />
    <twig:Tabler:Icon name="lucide:circle-check" variant="success" size="md" />
</div>
<twig:Tabler:Alert variant="success" icon="lucide:circle-check" title="Saved!" description="Your changes are live." class="mt-3 mb-0" />
```

UX Icons hides the icon from assistive technology (`aria-hidden="true"`) unless you give it an `aria-label` or a
`title`. Download the icons you use with `php bin/console ux:icons:lock`, so production never calls the Iconify API:
see the [UX Icons documentation](https://symfony.com/bundles/ux-icons/current/index.html).

## Variants

`variant` sets the color (`text-{variant}`):

```twig {"preview":true}
{% for variant in ['primary', 'secondary', 'success', 'danger', 'warning', 'info', 'dark', 'light'] %}
    <twig:Tabler:Icon name="circle-check" variant="{{ variant }}" class="fs-1" />
{% endfor %}
```

## Animations

`animation` is `pulse`, `tada` or `rotate`:

```twig {"preview":true}
<twig:Tabler:Icon name="heart" variant="danger" animation="pulse" />
<twig:Tabler:Icon name="bell" variant="warning" animation="tada" />
<twig:Tabler:Icon name="refresh" variant="primary" animation="rotate" />
```

## Attributes

Without `size` and `variant`, the icon inherits the font size and color of its parent. Other attributes go to the
`<i>`: a spacing class next to a label, a font-size class, or `role="img"` and an `aria-label` when the icon carries
meaning on its own:

```twig {"preview":true}
<div class="d-flex align-items-center gap-3">
    <twig:Tabler:Button variant="primary">
        <twig:Tabler:Icon name="plus" class="me-1" /> New invoice
    </twig:Tabler:Button>
    <twig:Tabler:Icon name="alert-triangle" variant="warning" class="fs-1" role="img" aria-label="Warning" />
</div>
```

## Props

| Prop        | Type    | Default    | Description                                                                                                                         |
| ----------- | ------- | ---------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| `name`      | string  | (required) | Icon name, without the `ti-` prefix; or a ux-icons name, see [UX Icons](#icons-from-symfonyux-icons)                                |
| `variant`   | string? | `null`     | `primary` `secondary` `success` `danger` `warning` `info` `dark` `light`                                                            |
| `animation` | string? | `null`     | `pulse` `tada` `rotate`                                                                                                             |
| `size`      | string? | `null`     | `sm` `md` `lg` `inline` (`icon icon-{size}`); unset, follows the font size                                                          |
| `filled`    | bool    | `false`    | Filled variant: `ti-filled ti-filled-{name}`, see [Filled](#filled); with UX Icons, `tabler:{name}-filled` in the `tabler` set only |
