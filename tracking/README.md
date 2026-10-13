# Tracking

A row of status blocks, one per period: the history of an uptime monitor, a job or a health check. Hover a block to
see its tooltip.

```twig {"preview":true}
<twig:Tabler:Tracking>
    {% for day in 1..30 %}
        {% if day == 9 %}
            <twig:Tabler:Tracking:Block variant="danger" tooltip="Oct {{ day }}: downtime (42 min)" />
        {% elseif day == 21 %}
            <twig:Tabler:Tracking:Block variant="warning" tooltip="Oct {{ day }}: degraded performance" />
        {% else %}
            <twig:Tabler:Tracking:Block variant="success" tooltip="Oct {{ day }}: operational" />
        {% endif %}
    {% endfor %}
</twig:Tabler:Tracking>
```

Place one `Tracking:Block` per period. The blocks share the width of the row.

## Installation

::: installation

## Variants

`variant` colors a block. Without one, the block is gray, for a period with no data. `tooltip` adds a Bootstrap
tooltip, which `tabler.js` initializes on page load: see [Tooltip](https://tabler-ux-components.silarhi.dev/components/overlays/tooltip/) for content added
later.

```twig {"preview":true}
<twig:Tabler:Tracking>
    {% for variant in ['primary', 'secondary', 'success', 'danger', 'warning', 'info', 'dark', 'light'] %}
        <twig:Tabler:Tracking:Block variant="{{ variant }}" tooltip="{{ variant }}" />
    {% endfor %}
    <twig:Tabler:Tracking:Block tooltip="No variant: no data" />
</twig:Tabler:Tracking>
```

## Squares

`squares` draws square blocks instead of thin bars: each block is as tall as it is wide.

```twig {"preview":true}
<twig:Tabler:Tracking squares>
    {% for day in 1..30 %}
        {% if day == 12 %}
            <twig:Tabler:Tracking:Block variant="danger" tooltip="Oct {{ day }}: 3 failed backups" />
        {% elseif day in [5, 26] %}
            <twig:Tabler:Tracking:Block variant="warning" tooltip="Oct {{ day }}: backup took over 2 hours" />
        {% else %}
            <twig:Tabler:Tracking:Block variant="success" tooltip="Oct {{ day }}: all backups succeeded" />
        {% endif %}
    {% endfor %}
</twig:Tabler:Tracking>
```

## In a card

```twig {"preview":true}
<div class="card">
    <div class="card-body">
        <div class="d-flex align-items-center mb-2">
            <div class="subheader">api.example.com</div>
            <div class="ms-auto text-success">99.86% uptime</div>
        </div>
        <twig:Tabler:Tracking>
            {% for status in ['success', 'success', 'success', 'danger', 'success', 'success', 'success', 'success', 'warning', 'success', 'success', 'success'] %}
                <twig:Tabler:Tracking:Block variant="{{ status }}" />
            {% endfor %}
            <twig:Tabler:Tracking:Block tooltip="No data yet" />
            <twig:Tabler:Tracking:Block tooltip="No data yet" />
        </twig:Tabler:Tracking>
    </div>
</div>
```

## Props

`Tracking`:

| Prop      | Type | Default | Description                                             |
| --------- | ---- | ------- | ------------------------------------------------------- |
| `squares` | bool | `false` | Square blocks instead of thin bars (`tracking-squares`) |

Other attributes go to the root `<div class="tracking">`.

### Tracking:Block

| Prop      | Type    | Default | Description                                                                       |
| --------- | ------- | ------- | --------------------------------------------------------------------------------- |
| `variant` | string? | `null`  | `primary` `secondary` `success` `danger` `warning` `info` `dark` `light` (`bg-*`) |
| `tooltip` | string? | `null`  | Tooltip text (`data-bs-toggle="tooltip"` and `data-bs-title`)                     |

Other attributes go to the block `<div>`.

## Sub-components

| Component        | Renders                                          |
| ---------------- | ------------------------------------------------ |
| `Tracking:Block` | `<div class="tracking-block">`, one status block |

## Blocks

| Block     | Default                           |
| --------- | --------------------------------- |
| `content` | Empty: the `Tracking:Block` items |
