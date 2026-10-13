# Card

The main building block of an admin page: a box that groups a title, content and actions.

```twig {"preview":true}
<twig:Tabler:Card title="Active users" text="1,284 users signed in during the last 30 days." footer="Updated 5 minutes ago" />
```

## Installation

::: installation

## Composed

Use the sub-components for anything richer than a string. `Card:Actions` sits at the end of the header; wrap the title
and the subtitle in a `<div>` so they stack:

```twig {"preview":true}
<twig:Tabler:Card>
    <twig:Tabler:Card:Header>
        <div>
            <twig:Tabler:Card:Title>Invoice #2026-0142</twig:Tabler:Card:Title>
            <twig:Tabler:Card:Subtitle>Acme Corp, due October 31</twig:Tabler:Card:Subtitle>
        </div>
        <twig:Tabler:Card:Actions>
            <twig:Tabler:Button variant="primary" size="sm">Send</twig:Tabler:Button>
        </twig:Tabler:Card:Actions>
    </twig:Tabler:Card:Header>
    <twig:Tabler:Card:Body>
        Total: <strong>$4,320.00</strong>, 3 line items.
    </twig:Tabler:Card:Body>
    <twig:Tabler:Card:Footer>Created by Jane Doe on October 1</twig:Tabler:Card:Footer>
</twig:Tabler:Card>
```

## Status

`status` adds a colored border, on the `top` edge by default. `statusPosition` moves it to the `bottom` or the
`start`:

```twig {"preview":true}
<div class="row row-cards">
    <div class="col-sm-4">
        <twig:Tabler:Card status="success" title="api-1" text="Healthy, 99.98% uptime." />
    </div>
    <div class="col-sm-4">
        <twig:Tabler:Card status="warning" statusPosition="bottom" title="api-2" text="High latency: 820 ms." />
    </div>
    <div class="col-sm-4">
        <twig:Tabler:Card status="danger" statusPosition="start" title="db-1" text="Unreachable since 09:42." />
    </div>
</div>
```

The border is rendered outside the `content` block, so a composed card keeps it:

```twig {"preview":true}
<twig:Tabler:Card status="danger" statusPosition="start">
    <twig:Tabler:Card:Header>
        <twig:Tabler:Card:Title>Danger zone</twig:Tabler:Card:Title>
        <twig:Tabler:Card:Actions>
            <twig:Tabler:Button variant="danger" size="sm">Delete project</twig:Tabler:Button>
        </twig:Tabler:Card:Actions>
    </twig:Tabler:Card:Header>
    <twig:Tabler:Card:Body>Deleting the project removes its deployments. This cannot be undone.</twig:Tabler:Card:Body>
</twig:Tabler:Card>
```

`Card:Status` renders the same border on its own, for a card that does not use the `status` prop.

## Gradients

`gradient` tints the card with a gradient background (`card-gradient`). It takes one of the presets: `disco` `gold`
`love` `mellow` `ocean` `psychedelic` `rainbow` `snow` `sun`.

```twig {"preview":true}
<div class="row row-cards">
    {% for preset in ['disco', 'gold', 'love', 'mellow', 'ocean', 'psychedelic', 'rainbow', 'snow', 'sun'] %}
        <div class="col-sm-4">
            <twig:Tabler:Card gradient="{{ preset }}" title="{{ preset|capitalize }}" text="The {{ preset }} preset." />
        </div>
    {% endfor %}
</div>
```

It also takes a color (`primary` `secondary` `success` `danger` `warning` `info` `dark` `light`), or `true` (a bare
`gradient` attribute) for the default gradient. `gradientDirection` sets the edge the gradient starts from (`start`,
`end` or `bottom`), and `gradientAnimated` slowly shifts it:

```twig {"preview":true}
<div class="row row-cards">
    <div class="col-sm-6">
        <twig:Tabler:Card gradient="{{ true }}" title="Default" text="A bare gradient uses the primary color." />
    </div>
    <div class="col-sm-6">
        <twig:Tabler:Card gradient="success" title="Color" text="Any semantic color: success, danger, info…" />
    </div>
    <div class="col-sm-6">
        <twig:Tabler:Card gradient="info" gradientDirection="bottom" title="Direction" text="The gradient starts from the bottom edge." />
    </div>
    <div class="col-sm-6">
        <twig:Tabler:Card gradient="ocean" gradientDirection="start" gradientAnimated="{{ true }}" title="Animated" text="The gradient slowly shifts." />
    </div>
</div>
```

## Dashed

`dashed` draws a dashed border, for an empty slot or an "add" placeholder:

```twig {"preview":true}
<twig:Tabler:Card dashed="{{ true }}">
    <twig:Tabler:Card:Body class="text-center text-secondary">
        <twig:Tabler:Icon name="plus" /> Add a server
    </twig:Tabler:Card:Body>
</twig:Tabler:Card>
```

## Appearance

`borderless` removes the borders of the card, its header and its footer (`card-borderless`). `transparent` removes the
background and the shadow and keeps a dashed border (`card-transparent`). `stacked` draws a second card behind this one
(`card-stacked`). `active` marks the card as selected with a primary border (`card-active`), and `inactive` dims its
body and disables pointer events (`card-inactive`). `rotate` tilts the card: `start` or `left` to one side, `end` or
`right` to the other (`card-rotate-*`).

```twig {"preview":true}
<div class="row row-cards">
    <div class="col-sm-4">
        <twig:Tabler:Card borderless="{{ true }}" title="Borderless" text="No border around the card." />
    </div>
    <div class="col-sm-4">
        <twig:Tabler:Card transparent="{{ true }}" title="Transparent" text="No background, a dashed border." />
    </div>
    <div class="col-sm-4">
        <twig:Tabler:Card stacked="{{ true }}" title="Stacked" text="A second card behind this one." />
    </div>
    <div class="col-sm-4">
        <twig:Tabler:Card active="{{ true }}" title="Active" text="The selected plan." />
    </div>
    <div class="col-sm-4">
        <twig:Tabler:Card inactive="{{ true }}" title="Inactive" text="Not available on your plan." />
    </div>
    <div class="col-sm-4">
        <twig:Tabler:Card rotate="start" title="Rotated" text="Tilted to the start." />
    </div>
</div>
```

## Sizes

`size` sets the padding: `sm`, `md` (the default) or `lg`.

```twig {"preview":true}
<div class="row row-cards">
    {% for size in ['sm', 'md', 'lg'] %}
        <div class="col-sm-4">
            <twig:Tabler:Card size="{{ size }}" title="Size {{ size }}" text="Padding follows the size." />
        </div>
    {% endfor %}
</div>
```

## Links

With `href`, the card renders as an `<a>`, so the whole card is clickable. `link` adds a hover effect: `true` (a bare
`link` attribute) for a hover shadow (`card-link`), `pop` to lift the card (`card-link-pop`) or `rotate` to tilt it
(`card-link-rotate`):

```twig {"preview":true}
<div class="row row-cards">
    <div class="col-sm-4">
        <twig:Tabler:Card href="/deployments/1842" link="{{ true }}" title="Deployment #1842" text="main, deployed 2 hours ago." />
    </div>
    <div class="col-sm-4">
        <twig:Tabler:Card href="/deployments/1841" link="pop" title="Deployment #1841" text="main, deployed yesterday." />
    </div>
    <div class="col-sm-4">
        <twig:Tabler:Card href="/deployments/1840" link="rotate" title="Deployment #1840" text="main, deployed 3 days ago." />
    </div>
</div>
```

## Images

`Card:Img` renders an image on an edge of the card. `position` sets the edge whose corners are rounded: `top` (the
default), `bottom`, `start` or `end`, or `full` for every corner (`card-img`). Put it first in the card for `top`, last
for `bottom`. `alt` defaults to an empty string, for a decorative image.

```twig {"preview":true}
<div class="row row-cards">
    <div class="col-sm-6">
        <twig:Tabler:Card>
            <twig:Tabler:Card:Img src="/examples/photo-1.jpg" alt="Open-plan office with desks" />
            <twig:Tabler:Card:Body>
                <twig:Tabler:Card:Title>Paris office</twig:Tabler:Card:Title>
                <p class="text-secondary mb-0">12 desks, 3 meeting rooms.</p>
            </twig:Tabler:Card:Body>
        </twig:Tabler:Card>
    </div>
    <div class="col-sm-6">
        <twig:Tabler:Card>
            <twig:Tabler:Card:Body>
                <twig:Tabler:Card:Title>Lyon office</twig:Tabler:Card:Title>
                <p class="text-secondary mb-0">8 desks, 2 meeting rooms.</p>
            </twig:Tabler:Card:Body>
            <twig:Tabler:Card:Img src="/examples/photo-2.jpg" alt="Meeting room" position="bottom" />
        </twig:Tabler:Card>
    </div>
</div>
```

## Image overlay

`Card:ImgOverlay` lays content over a `Card:Img` with `position="full"` (`card-img-overlay`). `dark` adds a gradient
that darkens the bottom of the image, so white text stays readable (`card-img-overlay-dark`):

```twig {"preview":true}
<div class="row row-cards">
    <div class="col-sm-6">
        <twig:Tabler:Card>
            <twig:Tabler:Card:Img src="/examples/photo-3.jpg" position="full" />
            <twig:Tabler:Card:ImgOverlay dark="{{ true }}" class="d-flex flex-column justify-content-end">
                <h3 class="card-title text-white mb-1">Working from home</h3>
                <p class="text-white mb-0">Six tips for a desk that lasts.</p>
            </twig:Tabler:Card:ImgOverlay>
        </twig:Tabler:Card>
    </div>
</div>
```

## Cover

`Card:Cover` is a header with a background photo under a dark overlay (`card-cover`). `image` sets the photo, and
`blurred` blurs it (`card-cover-blurred`). The content is wrapped in a `<div class="position-relative">`, which keeps it
above the overlay. Put `text-white` on the text itself, since headings set their own color:

```twig {"preview":true}
<div class="row row-cards">
    <div class="col-sm-6">
        <twig:Tabler:Card>
            <twig:Tabler:Card:Cover image="/examples/photo-1.jpg" class="text-center py-4">
                <div class="h2 m-0 text-white">Paris office</div>
            </twig:Tabler:Card:Cover>
            <twig:Tabler:Card:Body>12 desks, 3 meeting rooms.</twig:Tabler:Card:Body>
        </twig:Tabler:Card>
    </div>
    <div class="col-sm-6">
        <twig:Tabler:Card>
            <twig:Tabler:Card:Cover image="/examples/photo-2.jpg" blurred="{{ true }}" class="text-center py-4">
                <div class="h2 m-0 text-white">Lyon office</div>
            </twig:Tabler:Card:Cover>
            <twig:Tabler:Card:Body>8 desks, 2 meeting rooms.</twig:Tabler:Card:Body>
        </twig:Tabler:Card>
    </div>
</div>
```

An [Avatar](https://tabler-ux-components.silarhi.dev/components/content/avatar/#cover) with `cover` overlaps the cover from the body below.

## Code and tables

`Card:Code` replaces the body for a code block, without the body padding (`card-code`). To run a
[Table](https://tabler-ux-components.silarhi.dev/components/content/table/#in-a-card) edge to edge in a card, set its `card` prop.

```twig {"preview":true}
<twig:Tabler:Card>
    <twig:Tabler:Card:Header>
        <twig:Tabler:Card:Title>Installation</twig:Tabler:Card:Title>
    </twig:Tabler:Card:Header>
    <twig:Tabler:Card:Code>
        <pre><code>composer require silarhi/tabler-ux-components</code></pre>
    </twig:Tabler:Card:Code>
</twig:Tabler:Card>
```

## Tabs

`Card:Tabs` switches between several cards with a row of tabs above them (`card-tabs`). Put a
[Tabs](https://tabler-ux-components.silarhi.dev/components/navigation/tabs/) bar and a `Tabs:Content` in it, and give each `Tabs:Pane` the `card` class:

```twig {"preview":true}
<twig:Tabler:Card:Tabs>
    <twig:Tabler:Tabs>
        <twig:Tabler:Tabs:Item target="card-tabs-overview" active="{{ true }}">Overview</twig:Tabler:Tabs:Item>
        <twig:Tabler:Tabs:Item target="card-tabs-activity">Activity</twig:Tabler:Tabs:Item>
    </twig:Tabler:Tabs>
    <twig:Tabler:Tabs:Content>
        <twig:Tabler:Tabs:Pane id="card-tabs-overview" class="card" active="{{ true }}">
            <twig:Tabler:Card:Body>
                <twig:Tabler:Card:Title>Invoice INV-0142</twig:Tabler:Card:Title>
                <p class="mb-0">Acme Corp, €1,250.00, due on November 1.</p>
            </twig:Tabler:Card:Body>
        </twig:Tabler:Tabs:Pane>
        <twig:Tabler:Tabs:Pane id="card-tabs-activity" class="card">
            <twig:Tabler:Card:Body>Sent on October 2, viewed on October 3.</twig:Tabler:Card:Body>
        </twig:Tabler:Tabs:Pane>
    </twig:Tabler:Tabs:Content>
</twig:Tabler:Card:Tabs>
```

## Stamp

`Card:Stamp` adds a large decorative icon in the top end corner (`card-stamp`). Put it in the card, before the body.
`variant` colors the circle (a theme color or a palette color such as `yellow`), and `size="lg"` makes it bigger. It is
hidden from assistive technology:

```twig {"preview":true}
<div class="row row-cards">
    <div class="col-sm-6">
        <twig:Tabler:Card>
            <twig:Tabler:Card:Stamp icon="bell" variant="yellow" />
            <twig:Tabler:Card:Body>
                <twig:Tabler:Card:Title>3 new alerts</twig:Tabler:Card:Title>
                <p class="text-secondary mb-0">api-2 has answered slowly since 09:42.</p>
            </twig:Tabler:Card:Body>
        </twig:Tabler:Card>
    </div>
    <div class="col-sm-6">
        <twig:Tabler:Card>
            <twig:Tabler:Card:Stamp icon="star" variant="primary" size="lg" />
            <twig:Tabler:Card:Body>
                <twig:Tabler:Card:Title>Pro plan</twig:Tabler:Card:Title>
                <p class="text-secondary mb-0">Renews on November 1.</p>
            </twig:Tabler:Card:Body>
        </twig:Tabler:Card>
    </div>
</div>
```

## Progress

`Card:Progress` attaches a thin progress bar to the bottom edge of the card. Put it last in the card. `label` is read by
screen readers, and defaults to the percentage. `Card:Meta` renders a muted secondary line:

```twig {"preview":true}
<div class="row row-cards">
    <div class="col-sm-6">
        <twig:Tabler:Card>
            <twig:Tabler:Card:Body>
                <twig:Tabler:Card:Title>Storage</twig:Tabler:Card:Title>
                <twig:Tabler:Card:Meta>94 GB of 100 GB used</twig:Tabler:Card:Meta>
            </twig:Tabler:Card:Body>
            <twig:Tabler:Card:Progress value="94" variant="danger" label="94% of the storage used" />
        </twig:Tabler:Card>
    </div>
</div>
```

## Bottom buttons

`Card:Btn` is a full-width action along the bottom edge of the card (`card-btn`): an `<a>` with `href`, a
`<button type="button">` without. Wrap several of them in a `<div class="d-flex">` to share the edge:

```twig {"preview":true}
<div class="row row-cards">
    <div class="col-sm-6">
        <twig:Tabler:Card>
            <twig:Tabler:Card:Body class="text-center">
                <twig:Tabler:Avatar size="xl" image="/examples/avatar-1.jpg" class="mb-3" />
                <twig:Tabler:Card:Title class="mb-1">Jane Doe</twig:Tabler:Card:Title>
                <twig:Tabler:Card:Meta>Account manager</twig:Tabler:Card:Meta>
            </twig:Tabler:Card:Body>
            <div class="d-flex">
                <twig:Tabler:Card:Btn href="mailto:jane@example.com">Email</twig:Tabler:Card:Btn>
                <twig:Tabler:Card:Btn href="/users/42">View profile</twig:Tabler:Card:Btn>
            </div>
        </twig:Tabler:Card>
    </div>
</div>
```

## Scrollable body

`Card:Body` takes `scrollable`, which scrolls the body instead of growing the card (`card-body-scrollable`). Give the
body a height or a `max-height`:

```twig {"preview":true}
<twig:Tabler:Card>
    <twig:Tabler:Card:Header>
        <twig:Tabler:Card:Title>Activity</twig:Tabler:Card:Title>
    </twig:Tabler:Card:Header>
    <twig:Tabler:Card:Body scrollable="{{ true }}" style="max-height: 10rem">
        {% for hour in 9..17 %}
            <p>{{ hour }}:00: invoice #2026-{{ 140 + hour }} sent to Acme Corp.</p>
        {% endfor %}
    </twig:Tabler:Card:Body>
</twig:Tabler:Card>
```

## Blocks

`title`, `text` and `footer` each have a matching block. Override one, and the others keep rendering from their props:

```twig {"preview":true}
<twig:Tabler:Card title="Revenue" text="$12,400 this month." footer="Updated today">
    <twig:block name="header">
        <twig:Tabler:Card:Header>
            <twig:Tabler:Card:Title>Revenue</twig:Tabler:Card:Title>
            <twig:Tabler:Card:Actions>
                <twig:Tabler:Badge variant="success" light="{{ true }}">+8%</twig:Tabler:Badge>
            </twig:Tabler:Card:Actions>
        </twig:Tabler:Card:Header>
    </twig:block>
</twig:Tabler:Card>
```

Passing children replaces the `content` block, and so the three blocks. The status border is rendered before
`content`, so it is kept. See [Composition](https://tabler-ux-components.silarhi.dev/getting-started/composition/) for how blocks work.

## Props

| Prop                | Type         | Default | Description                                                                                                                |
| ------------------- | ------------ | ------- | -------------------------------------------------------------------------------------------------------------------------- |
| `size`              | string       | `'md'`  | `sm` `md` `lg`: the padding                                                                                                |
| `status`            | string?      | `null`  | Status border color, rendered with `Card:Status`: `primary` `secondary` `success` `danger` `warning` `info` `dark` `light` |
| `statusPosition`    | string       | `'top'` | `top` `bottom` `start`                                                                                                     |
| `gradient`          | bool\|string | `null`  | Gradient background: `true` for the default, a color as for `status`, or a preset (see above)                              |
| `gradientDirection` | string?      | `null`  | `start` `end` `bottom`: where the gradient starts                                                                          |
| `gradientAnimated`  | bool         | `false` | Slowly shifts the gradient (`card-gradient-animated`)                                                                      |
| `dashed`            | bool         | `false` | Dashed border (`card-dashed`)                                                                                              |
| `borderless`        | bool         | `false` | No border on the card, its header and its footer (`card-borderless`)                                                       |
| `transparent`       | bool         | `false` | No background and no shadow, a dashed border (`card-transparent`)                                                          |
| `stacked`           | bool         | `false` | Draws a second card behind this one (`card-stacked`)                                                                       |
| `active`            | bool         | `false` | Marks the card as selected (`card-active`)                                                                                 |
| `inactive`          | bool         | `false` | Dims the body and disables pointer events (`card-inactive`)                                                                |
| `rotate`            | string?      | `null`  | `start` `end` `left` `right`: tilts the card (`card-rotate-*`)                                                             |
| `link`              | bool\|string | `false` | Hover effect for a link card: `true` (`card-link`), `pop` (`card-link-pop`) or `rotate` (`card-link-rotate`)               |
| `title`             | string?      | `null`  | Rendered with `Card:Header` and `Card:Title`                                                                               |
| `text`              | string?      | `null`  | Rendered with `Card:Body`                                                                                                  |
| `footer`            | string?      | `null`  | Rendered with `Card:Footer`                                                                                                |
| `href`              | string?      | `null`  | Renders an `<a href>` instead of a `<div>`                                                                                 |

Other attributes go to the root `<div class="card">` (or `<a>`).

## Sub-components

| Component         | Renders                                                                            |
| ----------------- | ---------------------------------------------------------------------------------- |
| `Card:Header`     | `<div class="card-header">`                                                        |
| `Card:Title`      | `<h3 class="card-title">`                                                          |
| `Card:Subtitle`   | `<div class="card-subtitle">`: small muted text under the title                    |
| `Card:Actions`    | `<div class="card-actions">`: buttons or links at the end of the header            |
| `Card:Body`       | `<div class="card-body">`                                                          |
| `Card:Footer`     | `<div class="card-footer">`                                                        |
| `Card:Status`     | `<div class="card-status-top bg-primary">`: the status border, see its props below |
| `Card:Img`        | `<img class="card-img-top">`: an image on an edge of the card                      |
| `Card:ImgOverlay` | `<div class="card-img-overlay">`: content over a full `Card:Img`                   |
| `Card:Cover`      | `<div class="card-cover">`: a header with a background photo                       |
| `Card:Code`       | `<div class="card-code">`: a code block without the body padding                   |
| `Card:Tabs`       | `<div class="card-tabs">`: cards switched by a row of tabs                         |
| `Card:Stamp`      | `<div class="card-stamp">`: a large icon in the top end corner                     |
| `Card:Progress`   | `<div class="progress card-progress">`: a progress bar on the bottom edge          |
| `Card:Meta`       | `<div class="card-meta">`: a muted secondary line                                  |
| `Card:Btn`        | `<a class="card-btn">` (or `<button>`): a full-width action on the bottom edge     |

`Card:Status` takes `variant` (default `'primary'`) and `position` (default `'top'`), with the same values as the
`status` and `statusPosition` props of the card.

`Card:Body`:

| Prop         | Type | Default | Description                                                           |
| ------------ | ---- | ------- | --------------------------------------------------------------------- |
| `scrollable` | bool | `false` | Scrolls the body instead of growing the card (`card-body-scrollable`) |

`Card:Img`:

| Prop       | Type   | Default | Description                                                                                                                    |
| ---------- | ------ | ------- | ------------------------------------------------------------------------------------------------------------------------------ |
| `src`      | string |         | Image URL (required)                                                                                                           |
| `alt`      | string | `''`    | Alternative text; empty for a decorative image                                                                                 |
| `position` | string | `'top'` | `top` `bottom` `start` `end` (`card-img-{position}`): the edge whose corners are rounded; `full` for every corner (`card-img`) |

`Card:ImgOverlay`:

| Prop   | Type | Default | Description                                                       |
| ------ | ---- | ------- | ----------------------------------------------------------------- |
| `dark` | bool | `false` | Gradient that keeps light text readable (`card-img-overlay-dark`) |

`Card:Cover`:

| Prop      | Type    | Default | Description                                               |
| --------- | ------- | ------- | --------------------------------------------------------- |
| `image`   | string? | `null`  | Photo URL, set as an inline `background-image` style      |
| `blurred` | bool    | `false` | Blurs the photo behind the overlay (`card-cover-blurred`) |

Other attributes go to the `<div class="card-cover">`. A `style` attribute is merged after the `background-image`.

`Card:Stamp`:

| Prop      | Type    | Default | Description                                                                                                                                   |
| --------- | ------- | ------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| `icon`    | string? | `null`  | Tabler icon or UX Icons name; or put any markup in the `content` block                                                                        |
| `variant` | string? | `null`  | Circle color (`bg-{variant}`): a theme color, or `blue` `azure` `indigo` `purple` `pink` `red` `orange` `yellow` `lime` `green` `teal` `cyan` |
| `size`    | string  | `'md'`  | `md` `lg` (`card-stamp-lg`)                                                                                                                   |

`Card:Progress`:

| Prop      | Type    | Default     | Description                                                        |
| --------- | ------- | ----------- | ------------------------------------------------------------------ |
| `value`   | int     | `0`         | Percentage, from 0 to 100                                          |
| `variant` | string  | `'primary'` | Bar color, as for [`Progress:Bar`](https://tabler-ux-components.silarhi.dev/components/feedback/progress/) |
| `label`   | string? | `null`      | `aria-label` of the bar; defaults to the percentage, e.g. `94%`    |

`Card:Btn`:

| Prop   | Type    | Default | Description                                                   |
| ------ | ------- | ------- | ------------------------------------------------------------- |
| `href` | string? | `null`  | Renders an `<a href>`; without it, a `<button type="button">` |

## Blocks

| Block     | Default                                                              |
| --------- | -------------------------------------------------------------------- |
| `header`  | `Card:Header` with a `Card:Title` holding the `title` prop, when set |
| `body`    | `Card:Body` with the `text` prop, when set                           |
| `footer`  | `Card:Footer` with the `footer` prop, when set                       |
| `content` | `header`, `body` and `footer`: replace it to compose freely          |

The status border (when `status` is set) is rendered before the `content` block, so replacing `content` keeps it.
`Card:Stamp` has a `content` block holding the icon. The other sub-components, except `Card:Status`, `Card:Img` and
`Card:Progress`, have an empty `content` block for their children.
