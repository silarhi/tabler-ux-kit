# SwitchIcon

A toggle button that swaps two icons with an animation. `tabler.js` (`data-bs-toggle="switch-icon"`) toggles it on
click and keeps `aria-pressed` in sync. Give the button an `aria-label` saying what it toggles.

```twig {"preview":true}
<twig:Tabler:SwitchIcon iconA="moon" iconB="sun" animation="fade" aria-label="Dark mode" />
```

## Installation

::: installation

## Composed

`iconA` and `iconB` take [Icon](https://tabler-ux-components.silarhi.dev/components/content/icon/) names. For anything else (a color, an SVG), use the
`SwitchIcon:A` and `SwitchIcon:B` sub-components:

```twig {"preview":true}
<twig:Tabler:SwitchIcon animation="scale" aria-label="Add to favorites">
    <twig:Tabler:SwitchIcon:A><twig:Tabler:Icon name="heart" class="text-secondary" /></twig:Tabler:SwitchIcon:A>
    <twig:Tabler:SwitchIcon:B><twig:Tabler:Icon name="heart" class="text-red" /></twig:Tabler:SwitchIcon:B>
</twig:Tabler:SwitchIcon>
```

## Animations

```twig {"preview":true}
<div class="d-flex flex-wrap gap-4">
    {% for animation in ['fade', 'scale', 'flip', 'slide-up', 'slide-down', 'slide-left', 'slide-right', 'slide-start', 'slide-end'] %}
        <div class="text-center">
            <twig:Tabler:SwitchIcon iconA="bell" iconB="bell-off" animation="{{ animation }}" aria-label="Mute notifications" />
            <div class="text-secondary small">{{ animation }}</div>
        </div>
    {% endfor %}
</div>
```

## States

`active` starts on the second icon. `loading` (Tabler 1.6+) shows a spinner instead of the icons, ignores clicks and
sets `aria-busy="true"`:

```twig {"preview":true}
<div class="d-flex gap-4">
    <twig:Tabler:SwitchIcon iconA="bell" iconB="bell-off" animation="fade" active="{{ true }}" aria-label="Mute notifications" />
    <twig:Tabler:SwitchIcon iconA="bell" iconB="bell-off" animation="fade" loading="{{ true }}" aria-label="Mute notifications" />
</div>
```

## Blocks

`a` and `b` each have a matching block. Override one, and the other keeps rendering from its prop:

```twig {"preview":true}
<twig:Tabler:SwitchIcon iconA="star" animation="flip" aria-label="Star the repository">
    <twig:block name="b">
        <twig:Tabler:SwitchIcon:B><twig:Tabler:Icon name="star" class="text-yellow" /></twig:Tabler:SwitchIcon:B>
    </twig:block>
</twig:Tabler:SwitchIcon>
```

## Props

| Prop        | Type    | Default | Description                                                                                                                |
| ----------- | ------- | ------- | -------------------------------------------------------------------------------------------------------------------------- |
| `animation` | string? | `null`  | `fade` `scale` `flip` `slide-up` `slide-down` `slide-left` `slide-right` `slide-start` `slide-end`; `null` swaps instantly |
| `active`    | bool    | `false` | Starts switched on, showing icon B (`active`, `aria-pressed="true"`)                                                       |
| `loading`   | bool    | `false` | Spinner instead of the icons, clicks ignored (`switch-icon-loading`, `aria-busy`)                                          |
| `iconA`     | string? | `null`  | Name of the first icon, rendered with `Icon` inside `SwitchIcon:A`                                                         |
| `iconB`     | string? | `null`  | Name of the second icon, rendered with `Icon` inside `SwitchIcon:B`                                                        |

Other attributes go to the root `<button class="switch-icon">`.

## Sub-components

| Component      | Renders                                                 |
| -------------- | ------------------------------------------------------- |
| `SwitchIcon:A` | `<span class="switch-icon-a">`: the first, default icon |
| `SwitchIcon:B` | `<span class="switch-icon-b">`: the toggled icon        |

## Blocks

| Block     | Default                                               |
| --------- | ----------------------------------------------------- |
| `a`       | `SwitchIcon:A`, with an `Icon` named `iconA` when set |
| `b`       | `SwitchIcon:B`, with an `Icon` named `iconB` when set |
| `content` | `a` and `b`: replace it to compose freely             |
