# Mention

A rounded chip inside a sentence: a user in a comment, a tag in a post, an app or a color in release notes.

```twig {"preview":true}
<p>
    <twig:Tabler:Mention label="JaneCooper" prefix="@" prefixHidden avatar="/examples/avatar-1.jpg" href="#" />
    assigned ticket #1042 to
    <twig:Tabler:Mention label="WadeWarren" prefix="@" prefixHidden avatar="/examples/avatar-2.jpg" href="#" />
    this morning.
</p>
```

The mention is a `<span>`. With `href`, it renders as an `<a>`, so a chip that leads somewhere is reachable with the
keyboard.

## Installation

::: installation

## People

`avatar` adds a round picture of the person. `prefix` puts a sign before the label, such as `@`. With `prefixHidden`,
the sign is kept for assistive technology only (`visually-hidden`), when the design drops it:

```twig {"preview":true}
<p>
    <twig:Tabler:Mention label="EstherHoward" prefix="@" avatar="/examples/avatar-3.jpg" href="#" />
    issued the refund.
</p>
<p>
    <twig:Tabler:Mention label="JaneCooper" prefix="@" prefixHidden avatar="/examples/avatar-1.jpg" href="#" />
    approved the quote.
</p>
```

## Tags

`count` appends a muted number, for example how many posts carry the tag:

```twig {"preview":true}
<p>
    Filed under <twig:Tabler:Mention label="billing" prefix="#" count="16" href="#" /> and
    <twig:Tabler:Mention label="refunds" prefix="#" count="4" href="#" /> by the support team.
</p>
```

## Colors

`swatch` adds a color dot. It takes a theme color (`primary` `secondary` `success` `danger` `warning` `info` `dark`
`light` `muted`) or a palette color (`blue` `azure` `indigo` `purple` `pink` `red` `orange` `yellow` `lime` `green`
`teal` `cyan`); any other value renders a dot with no color class. Keep the color value or name in the label: the dot
alone says nothing to a screen reader or to a color-blind user.

```twig {"preview":true}
<p>
    Links use <twig:Tabler:Mention label="#066fd1" swatch="blue" /> and overdue invoices use
    <twig:Tabler:Mention label="red" swatch="red" /> in every report.
</p>
```

## Apps

`logo` adds the square logo of an app or a brand (`Mention:App`), scaled to fit the chip (`bg-cover`):

```twig {"preview":true}
<p>
    The release notes are on
    <twig:Tabler:Mention label="GitHub" href="#" logo="https://cdn.jsdelivr.net/npm/@tabler/core@1.6.1/dist/img/social/github.svg" />
    and in the
    <twig:Tabler:Mention label="Discord" logo="https://cdn.jsdelivr.net/npm/@tabler/core@1.6.1/dist/img/social/discord.svg" />
    announcements channel.
</p>
```

## Composed

Pass children to build the mention yourself. Children replace the whole content, so the props are ignored, except
`href`:

```twig {"preview":true}
<p>
    Ask
    <twig:Tabler:Mention href="#" data-user-id="42">
        <twig:Tabler:Mention:Avatar image="/examples/avatar-2.jpg" />
        <span class="visually-hidden">@</span>WadeWarren
        <twig:Tabler:Mention:Count>Support</twig:Tabler:Mention:Count>
    </twig:Tabler:Mention>
    about the refund policy.
</p>
```

## Blocks

Override a block to change one part and keep the others:

```twig {"preview":true}
<p>
    The
    <twig:Tabler:Mention label="refunds" prefix="#" href="#">
        <twig:block name="count"><twig:Tabler:Mention:Count>4 open</twig:Tabler:Mention:Count></twig:block>
    </twig:Tabler:Mention>
    queue is due by Friday.
</p>
```

See [Composition](https://tabler-ux-components.silarhi.dev/getting-started/composition/) for how blocks work.

## Accessibility

The avatar, the logo and the color dot carry no text, so the label must say who or what the chip is. Keep the `@` or
`#` sign in the text, with `prefixHidden` when it should not show.

## Props

| Prop           | Type    | Default | Description                                                          |
| -------------- | ------- | ------- | -------------------------------------------------------------------- |
| `label`        | string? | `null`  | The chip text                                                        |
| `href`         | string? | `null`  | Renders an `<a href>` instead of a `<span>`                          |
| `prefix`       | string? | `null`  | Sign before the label, such as `@` or `#`                            |
| `prefixHidden` | bool    | `false` | Keeps the prefix for assistive technology only (`visually-hidden`)   |
| `avatar`       | string? | `null`  | Round picture URL of a person, rendered with `Mention:Avatar`        |
| `logo`         | string? | `null`  | Square logo URL of an app or a brand, rendered with `Mention:App`    |
| `swatch`       | string? | `null`  | Color dot, rendered with `Mention:Color`: a theme or a palette color |
| `count`        | string? | `null`  | Muted number at the end, rendered with `Mention:Count`               |

Other attributes go to the root `<span class="mention">` (or `<a>`).

## Sub-components

| Component        | Renders                                                                                               |
| ---------------- | ----------------------------------------------------------------------------------------------------- |
| `Mention:Avatar` | `<span class="mention-avatar">`; `image` (default `null`) sets its background image                   |
| `Mention:App`    | `<span class="mention-app">`; `image` (default `null`) sets its background image, scaled (`bg-cover`) |
| `Mention:Color`  | `<span class="mention-color">`; `variant` (default `null`) sets the color, as `swatch`                |
| `Mention:Count`  | `<span class="mention-count">`                                                                        |

On `Mention:Avatar` and `Mention:App`, a `style` attribute is merged after the `background-image`, so it can still
override it.

## Blocks

| Block     | Default                                                              |
| --------- | -------------------------------------------------------------------- |
| `leading` | The avatar, logo and color dot, each when its prop is set            |
| `label`   | The `prefix` (visually hidden with `prefixHidden`), then the `label` |
| `count`   | `Mention:Count` with the `count` prop, when set                      |
| `content` | `leading`, `label` and `count`: replace it to compose freely         |
