# Timeline

A vertical feed of events: an activity log, a deployment history, an audit trail.

```twig {"preview":true}
<twig:Tabler:Timeline>
    <twig:Tabler:Timeline:Event title="Deployed to production" time="2 hrs ago" text="Release v2.4.0 is live." />
    <twig:Tabler:Timeline:Event title="Backup completed" time="10 hrs ago" text="Nightly backup of db-primary-01." />
    <twig:Tabler:Timeline:Event title="Invoice paid" time="1 day ago" text="Acme Corp paid INV-0142." />
</twig:Tabler:Timeline>
```

## Installation

::: installation

## Icons

Every event has an icon marker, empty by default. Fill it with the `icon` block and `Timeline:Event:Icon`; a
`bg-*-lt` class colors it:

```twig {"preview":true}
<twig:Tabler:Timeline>
    <twig:Tabler:Timeline:Event title="Deployed to production" time="2 hrs ago" text="Release v2.4.0 is live.">
        <twig:block name="icon">
            <twig:Tabler:Timeline:Event:Icon class="bg-success-lt"><twig:Tabler:Icon name="rocket" /></twig:Tabler:Timeline:Event:Icon>
        </twig:block>
    </twig:Tabler:Timeline:Event>
    <twig:Tabler:Timeline:Event title="Build failed" time="5 hrs ago" text="3 tests failed on the main branch.">
        <twig:block name="icon">
            <twig:Tabler:Timeline:Event:Icon class="bg-danger-lt"><twig:Tabler:Icon name="x" /></twig:Tabler:Timeline:Event:Icon>
        </twig:block>
    </twig:Tabler:Timeline:Event>
    <twig:Tabler:Timeline:Event title="New user" time="1 day ago" text="Jane Cooper joined the team.">
        <twig:block name="icon">
            <twig:Tabler:Timeline:Event:Icon class="bg-primary-lt"><twig:Tabler:Icon name="user-plus" /></twig:Tabler:Timeline:Event:Icon>
        </twig:block>
    </twig:Tabler:Timeline:Event>
</twig:Tabler:Timeline>
```

## Blocks

Each prop of `Timeline:Event` has a matching block. Override one, and the others keep rendering from their props:

```twig {"preview":true}
<twig:Tabler:Timeline>
    <twig:Tabler:Timeline:Event title="Release v2.4.0" time="2 hrs ago">
        <twig:block name="icon">
            <twig:Tabler:Timeline:Event:Icon><twig:Tabler:Icon name="tag" /></twig:Tabler:Timeline:Event:Icon>
        </twig:block>
        <twig:block name="body">
            <twig:Tabler:Timeline:Event:Body>
                Shipped by <strong>Wade Warren</strong>. <a href="#">Read the changelog</a>.
            </twig:Tabler:Timeline:Event:Body>
        </twig:block>
    </twig:Tabler:Timeline:Event>
</twig:Tabler:Timeline>
```

## Composed

Replace the `content` block to build the whole event yourself. It holds the icon and the
`<div class="card timeline-event-card">`, so keep that markup:

```twig {"preview":true}
<twig:Tabler:Timeline>
    <twig:Tabler:Timeline:Event>
        <twig:block name="content">
            <twig:Tabler:Timeline:Event:Icon><twig:Tabler:Icon name="file-invoice" /></twig:Tabler:Timeline:Event:Icon>
            <div class="card timeline-event-card">
                <div class="card-body">
                    <twig:Tabler:Timeline:Event:Time>1 day ago</twig:Tabler:Timeline:Event:Time>
                    <twig:Tabler:Timeline:Event:Title>Invoice sent</twig:Tabler:Timeline:Event:Title>
                    <twig:Tabler:Timeline:Event:Body>
                        <a href="#">INV-0142</a> was emailed to <strong>billing@acme.example</strong>.
                    </twig:Tabler:Timeline:Event:Body>
                </div>
            </div>
        </twig:block>
    </twig:Tabler:Timeline:Event>
</twig:Tabler:Timeline>
```

## Simple

`simple` gives a compact timeline without icons:

```twig {"preview":true}
<twig:Tabler:Timeline simple>
    <twig:Tabler:Timeline:Event title="Password changed" time="2 hrs ago" text="From 192.0.2.14, Paris." />
    <twig:Tabler:Timeline:Event title="Signed in" time="3 hrs ago" text="From 192.0.2.14, Paris." />
</twig:Tabler:Timeline>
```

## Props

`Timeline`:

| Prop     | Type | Default | Description                                 |
| -------- | ---- | ------- | ------------------------------------------- |
| `simple` | bool | `false` | Compact style, no icons (`timeline-simple`) |

Other attributes go to the root `<ul class="timeline">`.

`Timeline:Event`:

| Prop    | Type    | Default | Description                                       |
| ------- | ------- | ------- | ------------------------------------------------- |
| `title` | string? | `null`  | Rendered with `Timeline:Event:Title`              |
| `time`  | string? | `null`  | Rendered with `Timeline:Event:Time`, on the right |
| `text`  | string? | `null`  | Rendered with `Timeline:Event:Body`               |

Other attributes go to the `<li class="timeline-event">`.

## Sub-components

| Component              | Renders                                                                  |
| ---------------------- | ------------------------------------------------------------------------ |
| `Timeline:Event`       | `<li class="timeline-event">`: the icon and a `timeline-event-card` card |
| `Timeline:Event:Icon`  | `<div class="timeline-event-icon">`: put any icon inside                 |
| `Timeline:Event:Time`  | `<div class="text-secondary float-end">`                                 |
| `Timeline:Event:Title` | `<h4>`                                                                   |
| `Timeline:Event:Body`  | `<div class="text-secondary">`                                           |

## Blocks

Blocks of `Timeline:Event`:

| Block     | Default                                                                             |
| --------- | ----------------------------------------------------------------------------------- |
| `icon`    | An empty `Timeline:Event:Icon`                                                      |
| `time`    | `Timeline:Event:Time` with the `time` prop, when set                                |
| `title`   | `Timeline:Event:Title` with the `title` prop, when set                              |
| `body`    | `Timeline:Event:Body` with the `text` prop, when set                                |
| `content` | `icon`, then the card with `time`, `title` and `body`: replace it to compose freely |
