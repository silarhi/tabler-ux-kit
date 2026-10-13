# PageSection

A heading inside the page body, with an optional description, to split a long page into sections.

```twig {"preview":true}
<div class="row row-cards">
    <twig:Tabler:PageSection title="Deployments" description="The last 30 days, all environments." class="col-12" />
    <div class="col-sm-6">
        <twig:Tabler:Card title="Production" text="142 deployments, 3 rolled back." />
    </div>
    <div class="col-sm-6">
        <twig:Tabler:Card title="Staging" text="389 deployments, 12 rolled back." />
    </div>
</div>
```

The root `<div>` has no class of its own: give it the column class it needs in the grid, such as `col-12` in a `.row`.

## Installation

::: installation

## Composed

```twig {"preview":true}
<twig:Tabler:PageSection class="col-12">
    <twig:Tabler:PageSection:Title>
        Invoices <twig:Tabler:Badge variant="warning" light="{{ true }}">4 overdue</twig:Tabler:Badge>
    </twig:Tabler:PageSection:Title>
    <twig:Tabler:PageSection:Description>
        Sent to customers this quarter. <a href="#">See all invoices</a>
    </twig:Tabler:PageSection:Description>
</twig:Tabler:PageSection>
```

## Props

| Prop          | Type    | Default | Description                             |
| ------------- | ------- | ------- | --------------------------------------- |
| `title`       | string? | `null`  | Rendered with `PageSection:Title`       |
| `description` | string? | `null`  | Rendered with `PageSection:Description` |

Other attributes go to the root `<div>`.

## Sub-components

| Component                 | Renders                                |
| ------------------------- | -------------------------------------- |
| `PageSection:Title`       | `<h2 class="page-section-title">`      |
| `PageSection:Description` | `<p class="page-section-description">` |

## Blocks

| Block         | Default                                                         |
| ------------- | --------------------------------------------------------------- |
| `title`       | `PageSection:Title` with the `title` prop, when set             |
| `description` | `PageSection:Description` with the `description` prop, when set |
| `content`     | `title` and `description`: replace it to compose freely         |
