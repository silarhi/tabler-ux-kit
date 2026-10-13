# Offcanvas

A Bootstrap offcanvas, opened by a trigger with `data-bs-toggle="offcanvas"` and `data-bs-target="#<id>"`. It needs
`tabler.js`.

```twig {"preview":true}
<twig:Tabler:Button variant="primary" data-bs-toggle="offcanvas" data-bs-target="#deployment-log">Show log</twig:Tabler:Button>

<twig:Tabler:Offcanvas id="deployment-log" placement="end" title="Deployment #318" text="Build finished in 2 min 14 s. Release v2.4.0 is live." />
```

## Installation

::: installation

## Composed

The sub-components take over for a form or custom actions:

```twig {"preview":true}
<twig:Tabler:Button variant="default" data-bs-toggle="offcanvas" data-bs-target="#user-filters">
    <twig:Tabler:Icon name="filter" class="icon" /> Filters
</twig:Tabler:Button>

<twig:Tabler:Offcanvas id="user-filters" placement="end">
    <twig:Tabler:Offcanvas:Header>
        <twig:Tabler:Offcanvas:Title>Filter users</twig:Tabler:Offcanvas:Title>
        <twig:Tabler:Offcanvas:Close />
    </twig:Tabler:Offcanvas:Header>
    <twig:Tabler:Offcanvas:Body>
        <label class="form-check">
            <input type="checkbox" class="form-check-input" checked>
            <span class="form-check-label">Active</span>
        </label>
        <label class="form-check">
            <input type="checkbox" class="form-check-input">
            <span class="form-check-label">Invited</span>
        </label>
        <label class="form-check">
            <input type="checkbox" class="form-check-input">
            <span class="form-check-label">Suspended</span>
        </label>
    </twig:Tabler:Offcanvas:Body>
    <twig:Tabler:Offcanvas:Footer>
        <twig:Tabler:Button variant="primary" block="{{ true }}" data-bs-dismiss="offcanvas">Apply filters</twig:Tabler:Button>
    </twig:Tabler:Offcanvas:Footer>
</twig:Tabler:Offcanvas>
```

## Placements

`placement` sets the edge the panel slides in from. `start` and `end` follow the text direction.

```twig {"preview":true}
<div class="btn-list">
    {% for placement in ['start', 'end', 'top', 'bottom'] %}
        <twig:Tabler:Button variant="default" data-bs-toggle="offcanvas" data-bs-target="#offcanvas-{{ placement }}">{{ placement|capitalize }}</twig:Tabler:Button>
    {% endfor %}
</div>

{% for placement in ['start', 'end', 'top', 'bottom'] %}
    <twig:Tabler:Offcanvas id="offcanvas-{{ placement }}" placement="{{ placement }}" title="Placement: {{ placement }}" text="This panel slides in from the {{ placement }} edge." />
{% endfor %}
```

## Narrow and floating

`narrow` limits the panel to 20rem. `floating` (Tabler 1.6+) detaches it from the edges of the viewport, with rounded
corners:

```twig {"preview":true}
<twig:Tabler:Button variant="default" data-bs-toggle="offcanvas" data-bs-target="#notifications">
    <twig:Tabler:Icon name="bell" class="icon" /> Notifications
</twig:Tabler:Button>

<twig:Tabler:Offcanvas id="notifications" placement="end" narrow="{{ true }}" floating="{{ true }}" title="Notifications" text="Invoice #1042 was paid." footer="2 unread notifications" />
```

By default, the page cannot scroll while the panel is open: `scrollable` allows it (`data-bs-scroll="true"`).

## Blocks

`title`, `text` and `footer` are plain strings. For richer content, such as buttons in the footer, override the
matching block: `header`, `body` or `footer`. The other blocks keep rendering from their props. See
[Composition](https://tabler-ux-components.silarhi.dev/getting-started/composition/) for how blocks work.

```twig {"preview":true}
<twig:Tabler:Button variant="default" data-bs-toggle="offcanvas" data-bs-target="#invoice-1042">Invoice #1042</twig:Tabler:Button>

<twig:Tabler:Offcanvas id="invoice-1042" placement="end" title="Invoice #1042" text="1,250.00 EUR, due on November 12.">
    <twig:block name="footer">
        <twig:Tabler:Offcanvas:Footer class="d-flex gap-2">
            <twig:Tabler:Button variant="default" data-bs-dismiss="offcanvas">Close</twig:Tabler:Button>
            <twig:Tabler:Button variant="primary" class="ms-auto">Send reminder</twig:Tabler:Button>
        </twig:Tabler:Offcanvas:Footer>
    </twig:block>
</twig:Tabler:Offcanvas>
```

## Props

| Prop          | Type    | Default   | Description                                                          |
| ------------- | ------- | --------- | -------------------------------------------------------------------- |
| `id`          | string? | `null`    | DOM id targeted by triggers (`data-bs-target="#id"`)                 |
| `placement`   | string  | `'start'` | `start` `end` `top` `bottom`                                         |
| `title`       | string? | `null`    | Rendered with `Offcanvas:Header` and `Offcanvas:Title`               |
| `text`        | string? | `null`    | Rendered with `Offcanvas:Body`                                       |
| `footer`      | string? | `null`    | Rendered with `Offcanvas:Footer`                                     |
| `dismissible` | bool    | `true`    | Close button in the header rendered from `title` (`Offcanvas:Close`) |
| `scrollable`  | bool    | `false`   | The page keeps scrolling while the panel is open (`data-bs-scroll`)  |
| `narrow`      | bool    | `false`   | 20rem wide panel (`offcanvas-narrow`)                                |
| `floating`    | bool    | `false`   | Gap between the panel and the viewport edges (`offcanvas-floating`)  |

Other attributes go to the root `<div class="offcanvas" tabindex="-1">`. To hide the close button, pass
`dismissible="{{ false }}"` (see [boolean props](https://tabler-ux-components.silarhi.dev/getting-started/composition/#boolean-props)).

## Sub-components

| Component          | Renders                                                                     |
| ------------------ | --------------------------------------------------------------------------- |
| `Offcanvas:Header` | `<div class="offcanvas-header">`: holds the title and the close button      |
| `Offcanvas:Title`  | `<h5 class="offcanvas-title">`                                              |
| `Offcanvas:Close`  | `<button class="btn-close" data-bs-dismiss="offcanvas" aria-label="Close">` |
| `Offcanvas:Body`   | `<div class="offcanvas-body">`                                              |
| `Offcanvas:Footer` | `<div class="offcanvas-footer">`: usually the actions                       |

## Blocks

| Block     | Default                                                                                                   |
| --------- | --------------------------------------------------------------------------------------------------------- |
| `header`  | `Offcanvas:Header` with `Offcanvas:Title` and `Offcanvas:Close` (when `dismissible`), when `title` is set |
| `body`    | `Offcanvas:Body` with the `text` prop, when set                                                           |
| `footer`  | `Offcanvas:Footer` with the `footer` prop, when set                                                       |
| `content` | `header`, `body` and `footer`: replace it to compose freely                                               |
