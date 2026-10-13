# Pagination

Links to the pages of a long list. Mark the current page `active`, and `disabled` the links that lead nowhere.

```twig {"preview":true}
<twig:Tabler:Pagination>
    <twig:Tabler:Pagination:Item disabled>«</twig:Tabler:Pagination:Item>
    <twig:Tabler:Pagination:Item href="?page=1" active>1</twig:Tabler:Pagination:Item>
    <twig:Tabler:Pagination:Item href="?page=2">2</twig:Tabler:Pagination:Item>
    <twig:Tabler:Pagination:Item href="?page=3">3</twig:Tabler:Pagination:Item>
    <twig:Tabler:Pagination:Item href="?page=2">»</twig:Tabler:Pagination:Item>
</twig:Tabler:Pagination>
```

A `disabled` item keeps its `<a>`, without `href` and with `aria-disabled="true"`, so it cannot be followed. An
item without `href` links to `#`.

## Installation

::: installation

## Styles

`outline` adds a border to every link, `circle` makes them round. Combine them:

```twig {"preview":true}
<twig:Tabler:Pagination outline>
    <twig:Tabler:Pagination:Item href="?page=1">1</twig:Tabler:Pagination:Item>
    <twig:Tabler:Pagination:Item href="?page=2" active>2</twig:Tabler:Pagination:Item>
    <twig:Tabler:Pagination:Item href="?page=3">3</twig:Tabler:Pagination:Item>
</twig:Tabler:Pagination>
<twig:Tabler:Pagination circle>
    <twig:Tabler:Pagination:Item href="?page=1">1</twig:Tabler:Pagination:Item>
    <twig:Tabler:Pagination:Item href="?page=2" active>2</twig:Tabler:Pagination:Item>
    <twig:Tabler:Pagination:Item href="?page=3">3</twig:Tabler:Pagination:Item>
</twig:Tabler:Pagination>
<twig:Tabler:Pagination outline circle>
    <twig:Tabler:Pagination:Item href="?page=1">1</twig:Tabler:Pagination:Item>
    <twig:Tabler:Pagination:Item href="?page=2" active>2</twig:Tabler:Pagination:Item>
    <twig:Tabler:Pagination:Item href="?page=3">3</twig:Tabler:Pagination:Item>
</twig:Tabler:Pagination>
```

## Sizes

`size` sets the size of the links: `sm`, `md` (the default) or `lg`:

```twig {"preview":true}
{% for size in ['sm', 'md', 'lg'] %}
    <twig:Tabler:Pagination size="{{ size }}">
        <twig:Tabler:Pagination:Item href="?page=1">1</twig:Tabler:Pagination:Item>
        <twig:Tabler:Pagination:Item href="?page=2" active>2</twig:Tabler:Pagination:Item>
        <twig:Tabler:Pagination:Item href="?page=3">3</twig:Tabler:Pagination:Item>
    </twig:Tabler:Pagination>
{% endfor %}
```

## Labels and icons

The content of an item is free: text, icons, an ellipsis. Compute `active` and `disabled` from the current page:

```twig {"preview":true}
{% set page = 4 %}
{% set pages = 12 %}
<twig:Tabler:Pagination>
    <twig:Tabler:Pagination:Item href="?page={{ page - 1 }}" disabled="{{ page == 1 }}">
        <twig:Tabler:Icon name="chevron-left" /> prev
    </twig:Tabler:Pagination:Item>
    {% for i in [1, 2, 3, 4, 5] %}
        <twig:Tabler:Pagination:Item href="?page={{ i }}" active="{{ i == page }}">{{ i }}</twig:Tabler:Pagination:Item>
    {% endfor %}
    <twig:Tabler:Pagination:Item disabled>…</twig:Tabler:Pagination:Item>
    <twig:Tabler:Pagination:Item href="?page={{ pages }}">{{ pages }}</twig:Tabler:Pagination:Item>
    <twig:Tabler:Pagination:Item href="?page={{ page + 1 }}" disabled="{{ page == pages }}">
        next <twig:Tabler:Icon name="chevron-right" />
    </twig:Tabler:Pagination:Item>
</twig:Tabler:Pagination>
```

## Named pager

A pager links to the previous and next pages by name, at the end of a help article or a wizard step. `direction` sets
the side (`page-prev` or `page-next`) and adds `rel="prev"` or `rel="next"` to the link. `title` names the page and
`subtitle` adds a small uppercase label above it:

```twig {"preview":true}
<twig:Tabler:Pagination>
    <twig:Tabler:Pagination:Item href="/help/invoices" direction="prev" subtitle="previous" title="Invoices" />
    <twig:Tabler:Pagination:Item href="/help/payments" direction="next" subtitle="next" title="Payments" />
</twig:Tabler:Pagination>
```

## Props

`Pagination`:

| Prop      | Type   | Default | Description                                        |
| --------- | ------ | ------- | -------------------------------------------------- |
| `outline` | bool   | `false` | Bordered links (`pagination-outline`)              |
| `circle`  | bool   | `false` | Round links (`pagination-circle`)                  |
| `size`    | string | `'md'`  | `sm` (`pagination-sm`) `md` `lg` (`pagination-lg`) |

Other attributes go to the root `<ul class="pagination">`.

`Pagination:Item`:

| Prop        | Type    | Default | Description                                                                        |
| ----------- | ------- | ------- | ---------------------------------------------------------------------------------- |
| `href`      | string? | `null`  | Link target; `#` when not set                                                      |
| `active`    | bool    | `false` | The current page (`active`, with `aria-current="page"` on the link)                |
| `disabled`  | bool    | `false` | Not clickable (`disabled`): the link has no `href` and gets `aria-disabled="true"` |
| `direction` | string? | `null`  | `prev` (`page-prev`) `next` (`page-next`): a pager step, with a `rel` on the link  |
| `title`     | string? | `null`  | Page name, for a named pager (`page-item-title`)                                   |
| `subtitle`  | string? | `null`  | Small uppercase label above the title (`page-item-subtitle`)                       |

Other attributes go to the `<li class="page-item">`. The `subtitle` and `title` render before the content of the item.

## Sub-components

| Component         | Renders                                                  |
| ----------------- | -------------------------------------------------------- |
| `Pagination:Item` | `<li class="page-item">` with an `<a class="page-link">` |
