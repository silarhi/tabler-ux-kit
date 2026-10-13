# PageHeader

The title block at the top of a page, with a pretitle above the title and buttons on the end side.

```twig {"preview":true}
<twig:Tabler:PageHeader pretitle="Overview" title="Dashboard" />
```

## Installation

::: installation

## Actions

Fill the `actions` block with `PageHeader:Actions`: it lays the buttons out in a `btn-list` on the end side, and the
title keeps coming from the props.

```twig {"preview":true}
<twig:Tabler:PageHeader pretitle="Billing" title="Invoices">
    <twig:block name="actions">
        <twig:Tabler:PageHeader:Actions>
            <twig:Tabler:Button appearance="outline" variant="secondary">Export</twig:Tabler:Button>
            <twig:Tabler:Button variant="primary"><twig:Tabler:Icon name="plus" class="icon" /> New invoice</twig:Tabler:Button>
        </twig:Tabler:PageHeader:Actions>
    </twig:block>
</twig:Tabler:PageHeader>
```

## Composed

Direct children replace the `content` block, which holds the whole grid row: the `pretitle` and `title` props are no
longer rendered. Rebuild the `.row` yourself, here to add an avatar next to the title.

```twig {"preview":true}
<twig:Tabler:PageHeader>
    <div class="row g-3 align-items-center">
        <div class="col-auto">
            <twig:Tabler:Avatar image="/examples/avatar-2.jpg" size="lg" />
        </div>
        <div class="col">
            <twig:Tabler:PageHeader:Pretitle>Users</twig:Tabler:PageHeader:Pretitle>
            <twig:Tabler:PageHeader:Title>Jane Doe</twig:Tabler:PageHeader:Title>
            <div class="text-secondary mt-1">Administrator · joined March 2024</div>
        </div>
        <twig:Tabler:PageHeader:Actions>
            <twig:Tabler:Button appearance="outline" variant="danger">Suspend</twig:Tabler:Button>
        </twig:Tabler:PageHeader:Actions>
    </div>
</twig:Tabler:PageHeader>
```

## Props

| Prop       | Type    | Default | Description                         |
| ---------- | ------- | ------- | ----------------------------------- |
| `pretitle` | string? | `null`  | Rendered with `PageHeader:Pretitle` |
| `title`    | string? | `null`  | Rendered with `PageHeader:Title`    |

Other attributes go to the root `<div class="page-header d-print-none">`.

## Sub-components

| Component             | Renders                                                            |
| --------------------- | ------------------------------------------------------------------ |
| `PageHeader:Pretitle` | `<div class="page-pretitle">`                                      |
| `PageHeader:Title`    | `<h2 class="page-title">`                                          |
| `PageHeader:Actions`  | `<div class="col-auto ms-auto">` around a `<div class="btn-list">` |

## Blocks

| Block      | Default                                                          |
| ---------- | ---------------------------------------------------------------- |
| `pretitle` | `PageHeader:Pretitle` with the `pretitle` prop, when set         |
| `title`    | `PageHeader:Title` with the `title` prop, when set               |
| `actions`  | Nothing: put a `PageHeader:Actions` in it                        |
| `content`  | A `.row`: a `.col` around `pretitle` and `title`, then `actions` |
