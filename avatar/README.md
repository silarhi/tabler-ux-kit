# Avatar

Shows who a user is: their photo, their initials on a tinted background, or an icon.

```twig {"preview":true}
<twig:Tabler:Avatar:List>
    <twig:Tabler:Avatar image="/examples/avatar-1.jpg" />
    <twig:Tabler:Avatar variant="primary">JD</twig:Tabler:Avatar>
    <twig:Tabler:Avatar variant="success"><twig:Tabler:Icon name="user" /></twig:Tabler:Avatar>
</twig:Tabler:Avatar:List>
```

`image` sets the picture as a background image. Without it, the children (initials, an icon) are centered in the
avatar.

## Installation

::: installation

## Sizes

`size` goes from `xxs` to `2xl`; `md` is the default.

```twig {"preview":true}
{% for size in ['xxs', 'xs', 'sm', 'md', 'lg', 'xl', '2xl'] %}
    <twig:Tabler:Avatar size="{{ size }}" image="/examples/avatar-2.jpg" />
{% endfor %}
```

## Variants

`variant` gives initials or icons a tinted background (`bg-{variant}-lt`):

```twig {"preview":true}
{% for variant, initials in {primary: 'JD', secondary: 'AL', success: 'MK', danger: 'RB', warning: 'SC', info: 'TW', dark: 'EV', light: 'NP'} %}
    <twig:Tabler:Avatar variant="{{ variant }}">{{ initials }}</twig:Tabler:Avatar>
{% endfor %}
```

## Shapes

Avatars are round in Tabler 1.6. `square` switches to rounded corners (`avatar-square`). `rounded` adds Bootstrap's
`rounded-circle`, which forces a circle when your CSS gives avatars another shape.

```twig {"preview":true}
<twig:Tabler:Avatar image="/examples/avatar-3.jpg" />
<twig:Tabler:Avatar image="/examples/avatar-3.jpg" square="{{ true }}" />
<twig:Tabler:Avatar variant="info" square="{{ true }}">TW</twig:Tabler:Avatar>
```

## Cover

`cover` pulls the avatar up by half its height over the element above it, such as a
[`Card:Cover`](https://tabler-ux-components.silarhi.dev/components/content/card/#cover), and draws a ring in the card background around it (`avatar-cover`):

```twig {"preview":true}
<div class="row row-cards">
    <div class="col-sm-6">
        <twig:Tabler:Card>
            <twig:Tabler:Card:Cover image="/examples/photo-1.jpg" class="py-5" />
            <twig:Tabler:Card:Body class="text-center">
                <twig:Tabler:Avatar size="xl" image="/examples/avatar-1.jpg" cover="{{ true }}" class="mb-3" />
                <twig:Tabler:Card:Title class="mb-1">Jane Cooper</twig:Tabler:Card:Title>
                <twig:Tabler:Card:Meta>Account manager</twig:Tabler:Card:Meta>
            </twig:Tabler:Card:Body>
        </twig:Tabler:Card>
    </div>
</div>
```

## Lists

`Avatar:List` spaces several avatars in a row (`avatar-list`). `stacked` overlaps them (`avatar-list-stacked`), and
`size` sizes every avatar in the list (`avatar-list-{size}`):

```twig {"preview":true}
<twig:Tabler:Avatar:List stacked="{{ true }}" class="mb-3">
    <twig:Tabler:Avatar image="/examples/avatar-1.jpg" />
    <twig:Tabler:Avatar image="/examples/avatar-2.jpg" />
    <twig:Tabler:Avatar image="/examples/avatar-3.jpg" />
    <twig:Tabler:Avatar>+8</twig:Tabler:Avatar>
</twig:Tabler:Avatar:List>
<twig:Tabler:Avatar:List size="sm">
    <twig:Tabler:Avatar variant="primary">JD</twig:Tabler:Avatar>
    <twig:Tabler:Avatar variant="success">AL</twig:Tabler:Avatar>
    <twig:Tabler:Avatar variant="warning">MK</twig:Tabler:Avatar>
</twig:Tabler:Avatar:List>
```

## Brand mark

`Avatar:Brand` adds a small mark in the bottom corner of an avatar (`avatar-brand`), e.g. the service an account comes
from. Put it in the avatar, with an `image` or with markup such as an icon:

```twig {"preview":true}
<twig:Tabler:Avatar:List>
    <twig:Tabler:Avatar size="lg" image="/examples/avatar-1.jpg">
        <twig:Tabler:Avatar:Brand class="d-flex align-items-center justify-content-center">
            <twig:Tabler:Icon name="brand-github" />
        </twig:Tabler:Avatar:Brand>
    </twig:Tabler:Avatar>
    <twig:Tabler:Avatar size="lg" variant="info">TW
        <twig:Tabler:Avatar:Brand class="d-flex align-items-center justify-content-center">
            <twig:Tabler:Icon name="brand-gitlab" />
        </twig:Tabler:Avatar:Brand>
    </twig:Tabler:Avatar>
    <twig:Tabler:Avatar size="lg" image="/examples/avatar-2.jpg">
        <twig:Tabler:Avatar:Brand image="https://cdn.jsdelivr.net/npm/@tabler/core@1.6.1/dist/img/social/discord.svg" />
    </twig:Tabler:Avatar>
</twig:Tabler:Avatar:List>
```

## Upload slot

`Avatar:Upload` is a dashed empty slot for a picture that is not set yet (`avatar-upload`). It renders a
`<button type="button">`, or an `<a>` with `href`. `icon` and `text` fill it; children replace both:

```twig {"preview":true}
<twig:Tabler:Avatar:Upload size="xl" icon="plus" text="Add" aria-label="Add a profile picture" />
<twig:Tabler:Avatar:Upload href="/profile/picture" size="xl" icon="camera" text="Change" />
```

## Props

| Prop      | Type    | Default | Description                                                                                 |
| --------- | ------- | ------- | ------------------------------------------------------------------------------------------- |
| `size`    | string  | `'md'`  | `xxs` `xs` `sm` `md` `lg` `xl` `2xl`                                                        |
| `variant` | string? | `null`  | Tinted background: `primary` `secondary` `success` `danger` `warning` `info` `dark` `light` |
| `rounded` | bool    | `false` | Circle (`rounded-circle`)                                                                   |
| `square`  | bool    | `false` | Rounded corners instead of a circle (`avatar-square`)                                       |
| `cover`   | bool    | `false` | Pulled over the element above, with a ring (`avatar-cover`)                                 |
| `image`   | string? | `null`  | Image URL, set as an inline `background-image` style                                        |

Other attributes go to the root `<span class="avatar">`. A `style` attribute is merged after the `background-image`,
so it can still override it.

`Avatar:List`:

| Prop      | Type    | Default | Description                                                                     |
| --------- | ------- | ------- | ------------------------------------------------------------------------------- |
| `stacked` | bool    | `false` | Overlaps the avatars (`avatar-list-stacked`)                                    |
| `size`    | string? | `null`  | `xxs` `xs` `sm` `md` `lg` `xl` `2xl`: sizes every avatar (`avatar-list-{size}`) |

`Avatar:Brand`:

| Prop    | Type    | Default | Description                                                                                          |
| ------- | ------- | ------- | ---------------------------------------------------------------------------------------------------- |
| `image` | string? | `null`  | Image URL of the mark, set as an inline `background-image` style and scaled to the mark (`bg-cover`) |

Other attributes go to the `<span class="avatar-brand">`. A `style` attribute is merged after the `background-image`,
so it can still override it.

`Avatar:Upload`:

| Prop   | Type    | Default | Description                                                   |
| ------ | ------- | ------- | ------------------------------------------------------------- |
| `href` | string? | `null`  | Renders an `<a href>`; without it, a `<button type="button">` |
| `size` | string  | `'md'`  | `xxs` `xs` `sm` `md` `lg` `xl` `2xl`                          |
| `icon` | string? | `null`  | Tabler icon name, rendered with `Icon`                        |
| `text` | string? | `null`  | Label under the icon (`avatar-upload-text`)                   |

## Sub-components

| Component       | Renders                                                                 |
| --------------- | ----------------------------------------------------------------------- |
| `Avatar:List`   | `<div class="avatar-list">`: a row of avatars                           |
| `Avatar:Brand`  | `<span class="avatar-brand">`: a mark in the bottom corner of an avatar |
| `Avatar:Upload` | `<button class="avatar avatar-upload">` (or `<a>`): an empty slot       |

## Blocks

| Block     | Default                                         |
| --------- | ----------------------------------------------- |
| `content` | Empty: the children (initials, an icon) go here |

`Avatar:List` and `Avatar:Brand` have an empty `content` block for their children. The `content` block of
`Avatar:Upload` renders the `icon` and the `text`.
