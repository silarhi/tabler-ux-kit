# Datagrid

A responsive grid of title and value pairs: the details of a server, an invoice, a user.

```twig {"preview":true}
<twig:Tabler:Datagrid>
    <twig:Tabler:Datagrid:Item title="Hostname" text="db-primary-01" />
    <twig:Tabler:Datagrid:Item title="Region" text="eu-west-3" />
    <twig:Tabler:Datagrid:Item title="Engine" text="PostgreSQL 17.2" />
    <twig:Tabler:Datagrid:Item title="Port" text="5432" />
    <twig:Tabler:Datagrid:Item title="Storage" text="250 GB" />
    <twig:Tabler:Datagrid:Item title="Last backup" text="Today, 04:00" />
</twig:Tabler:Datagrid>
```

## Installation

::: installation

## Composed

When the value is more than a string, compose the item with `Datagrid:Item:Title` and `Datagrid:Item:Content`. Both
forms mix freely in the same grid:

```twig {"preview":true}
<twig:Tabler:Datagrid>
    <twig:Tabler:Datagrid:Item title="Invoice" text="INV-2026-0142" />
    <twig:Tabler:Datagrid:Item>
        <twig:Tabler:Datagrid:Item:Title>Customer</twig:Tabler:Datagrid:Item:Title>
        <twig:Tabler:Datagrid:Item:Content>
            <div class="d-flex align-items-center">
                <twig:Tabler:Avatar size="xs" image="/examples/avatar-1.jpg" class="me-2" />
                Jane Cooper
            </div>
        </twig:Tabler:Datagrid:Item:Content>
    </twig:Tabler:Datagrid:Item>
    <twig:Tabler:Datagrid:Item>
        <twig:Tabler:Datagrid:Item:Title>Status</twig:Tabler:Datagrid:Item:Title>
        <twig:Tabler:Datagrid:Item:Content>
            <twig:Tabler:Status variant="success" dot label="Paid" />
        </twig:Tabler:Datagrid:Item:Content>
    </twig:Tabler:Datagrid:Item>
    <twig:Tabler:Datagrid:Item title="Amount" text="€1,250.00" />
</twig:Tabler:Datagrid>
```

## Blocks

`Datagrid:Item` has a block per prop. Override `body` to keep the `title` prop and render a custom value:

```twig {"preview":true}
<twig:Tabler:Datagrid>
    <twig:Tabler:Datagrid:Item title="Repository">
        <twig:block name="body">
            <twig:Tabler:Datagrid:Item:Content>
                <a href="#">acme/billing-api</a>
            </twig:Tabler:Datagrid:Item:Content>
        </twig:block>
    </twig:Tabler:Datagrid:Item>
    <twig:Tabler:Datagrid:Item title="Branch" text="main" />
</twig:Tabler:Datagrid>
```

## Props

`Datagrid` has no props: attributes go to the root `<div class="datagrid">`.

`Datagrid:Item`:

| Prop    | Type    | Default | Description                           |
| ------- | ------- | ------- | ------------------------------------- |
| `title` | string? | `null`  | Rendered with `Datagrid:Item:Title`   |
| `text`  | string? | `null`  | Rendered with `Datagrid:Item:Content` |

Other attributes go to the `<div class="datagrid-item">`.

## Sub-components

| Component               | Renders                                 |
| ----------------------- | --------------------------------------- |
| `Datagrid:Item`         | `<div class="datagrid-item">`, one pair |
| `Datagrid:Item:Title`   | `<div class="datagrid-title">`          |
| `Datagrid:Item:Content` | `<div class="datagrid-content">`        |

## Blocks

Blocks of `Datagrid:Item`:

| Block     | Default                                                |
| --------- | ------------------------------------------------------ |
| `title`   | `Datagrid:Item:Title` with the `title` prop, when set  |
| `body`    | `Datagrid:Item:Content` with the `text` prop, when set |
| `content` | `title` and `body`: replace it to compose freely       |
