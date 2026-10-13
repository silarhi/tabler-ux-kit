# Empty

An empty state: a list with no items yet, a search with no results.

```twig {"preview":true}
<twig:Tabler:Empty title="No results found" subtitle="Try adjusting your search or filters." />
```

## Installation

::: installation

## Icon and action

The `icon` and `action` blocks have no matching prop: fill them with `Empty:Icon` and `Empty:Action`, while the title
and the subtitle keep coming from the props. See [blocks](https://tabler-ux-components.silarhi.dev/getting-started/composition/#blocks).

`Empty:Icon` is a 3rem box sized for an SVG: give a webfont icon a matching `font-size`.

```twig {"preview":true}
<twig:Tabler:Empty title="No invoices yet" subtitle="Invoices you create show up here.">
    <twig:block name="icon">
        <twig:Tabler:Empty:Icon><twig:Tabler:Icon name="file-invoice" style="font-size: 3rem" /></twig:Tabler:Empty:Icon>
    </twig:block>
    <twig:block name="action">
        <twig:Tabler:Empty:Action>
            <twig:Tabler:Button variant="primary"><twig:Tabler:Icon name="plus" class="icon" /> New invoice</twig:Tabler:Button>
        </twig:Tabler:Empty:Action>
    </twig:block>
</twig:Tabler:Empty>
```

## Header and image

Instead of an icon, lead with a large text in `Empty:Header`, such as an error code:

```twig {"preview":true}
<twig:Tabler:Empty title="Page not found" subtitle="The page you are looking for was moved or deleted.">
    <twig:block name="icon">
        <twig:Tabler:Empty:Header>404</twig:Tabler:Empty:Header>
    </twig:block>
    <twig:block name="action">
        <twig:Tabler:Empty:Action>
            <twig:Tabler:Button variant="primary" href="/dashboard"><twig:Tabler:Icon name="arrow-left" class="icon" /> Back to the dashboard</twig:Tabler:Button>
        </twig:Tabler:Empty:Action>
    </twig:block>
</twig:Tabler:Empty>
```

Or with an illustration in `Empty:Img`. `bordered` draws a border around the empty state:

```twig {"preview":true}
<twig:Tabler:Empty bordered="{{ true }}" title="No projects yet" subtitle="Create a project to start tracking time and expenses.">
    <twig:block name="icon">
        <twig:Tabler:Empty:Img><img src="/examples/photo-1.jpg" height="128" alt=""></twig:Tabler:Empty:Img>
    </twig:block>
    <twig:block name="action">
        <twig:Tabler:Empty:Action>
            <twig:Tabler:Button variant="primary"><twig:Tabler:Icon name="plus" class="icon" /> New project</twig:Tabler:Button>
        </twig:Tabler:Empty:Action>
    </twig:block>
</twig:Tabler:Empty>
```

## Composed

Children replace the whole content, for rich text in the subtitle:

```twig {"preview":true}
<twig:Tabler:Empty>
    <twig:Tabler:Empty:Icon><twig:Tabler:Icon name="users" style="font-size: 3rem" /></twig:Tabler:Empty:Icon>
    <twig:Tabler:Empty:Title>No team members</twig:Tabler:Empty:Title>
    <twig:Tabler:Empty:Subtitle>
        Invite people to <strong>Acme Corp</strong> to share projects and invoices.
    </twig:Tabler:Empty:Subtitle>
    <twig:Tabler:Empty:Action>
        <twig:Tabler:Button variant="primary"><twig:Tabler:Icon name="user-plus" class="icon" /> Invite members</twig:Tabler:Button>
    </twig:Tabler:Empty:Action>
</twig:Tabler:Empty>
```

## Props

| Prop       | Type    | Default | Description                                      |
| ---------- | ------- | ------- | ------------------------------------------------ |
| `title`    | string? | `null`  | Rendered with `Empty:Title`                      |
| `subtitle` | string? | `null`  | Rendered with `Empty:Subtitle`                   |
| `bordered` | bool    | `false` | Border around the empty state (`empty-bordered`) |

Other attributes go to the root `<div class="empty">`.

## Sub-components

| Component        | Renders                                                                       |
| ---------------- | ----------------------------------------------------------------------------- |
| `Empty:Icon`     | `<div class="empty-icon">`: put any icon inside (Tabler Icons, SVG, ux-icons) |
| `Empty:Header`   | `<div class="empty-header">`: a large text, such as an error code             |
| `Empty:Img`      | `<div class="empty-img">`: put an illustration inside                         |
| `Empty:Title`    | `<p class="empty-title">`                                                     |
| `Empty:Subtitle` | `<p class="empty-subtitle text-secondary">`                                   |
| `Empty:Action`   | `<div class="empty-action">`: buttons or links                                |

## Blocks

| Block      | Default                                                                |
| ---------- | ---------------------------------------------------------------------- |
| `icon`     | Nothing: put an `Empty:Icon`, `Empty:Header` or `Empty:Img` in it      |
| `title`    | `Empty:Title` with the `title` prop, when set                          |
| `subtitle` | `Empty:Subtitle` with the `subtitle` prop, when set                    |
| `action`   | Nothing: put an `Empty:Action` in it                                   |
| `content`  | `icon`, `title`, `subtitle` and `action`: replace it to compose freely |
