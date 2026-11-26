# Breadcrumb

A trail of links from the home page to the current page.

```twig {"preview":true}
<twig:Tabler:Breadcrumb items="{{ [
    {label: 'Home', href: '/', icon: 'home'},
    {label: 'Users', href: '/users'},
    {label: 'Jane Cooper', href: '/users/42'},
] }}" />
```

`items` is an array of `{label, href?, active?, icon?}`, each rendered with `Breadcrumb:Item`. The last item is the
current page: it renders as plain text with `aria-current="page"`, even with an `href`. Once an entry sets `active`,
the last one is no longer active by default: only the entries with `active: true` are. `icon` puts a
[Tabler icon](https://tabler.io/icons), or a UX Icons name (`lucide:house`), before the label.

## Installation

::: installation

## Composed

Pass `Breadcrumb:Item`s as children instead: they replace the `content` block. An item with an `href` renders a link.
Mark the current page `active`: it renders as plain text with `aria-current="page"`, even with an `href`.

```twig {"preview":true}
<twig:Tabler:Breadcrumb>
    <twig:Tabler:Breadcrumb:Item href="/">Home</twig:Tabler:Breadcrumb:Item>
    <twig:Tabler:Breadcrumb:Item href="/users">Users</twig:Tabler:Breadcrumb:Item>
    <twig:Tabler:Breadcrumb:Item active>Jane Cooper</twig:Tabler:Breadcrumb:Item>
</twig:Tabler:Breadcrumb>
```

## Separators

`separator` sets the character between items: `default` (a slash), `dots`, `arrows` or `bullets`:

```twig {"preview":true}
{% for separator in ['default', 'dots', 'arrows', 'bullets'] %}
    <twig:Tabler:Breadcrumb separator="{{ separator }}">
        <twig:Tabler:Breadcrumb:Item href="/">Home</twig:Tabler:Breadcrumb:Item>
        <twig:Tabler:Breadcrumb:Item href="/invoices">Invoices</twig:Tabler:Breadcrumb:Item>
        <twig:Tabler:Breadcrumb:Item active>INV-0142</twig:Tabler:Breadcrumb:Item>
    </twig:Tabler:Breadcrumb>
{% endfor %}
```

## Muted

`muted` gives the links the color of the text around them:

```twig {"preview":true}
<twig:Tabler:Breadcrumb muted>
    <twig:Tabler:Breadcrumb:Item href="/">Home</twig:Tabler:Breadcrumb:Item>
    <twig:Tabler:Breadcrumb:Item href="/deployments">Deployments</twig:Tabler:Breadcrumb:Item>
    <twig:Tabler:Breadcrumb:Item active>#1284</twig:Tabler:Breadcrumb:Item>
</twig:Tabler:Breadcrumb>
```

## Props

`Breadcrumb`:

| Prop        | Type   | Default     | Description                                                                                          |
| ----------- | ------ | ----------- | ---------------------------------------------------------------------------------------------------- |
| `items`     | array? | `null`      | `{label, href?, active?, icon?}` entries, rendered with `Breadcrumb:Item`; the last one is active    |
| `separator` | string | `'default'` | `default` `dots` (`breadcrumb-dots`) `arrows` (`breadcrumb-arrows`) `bullets` (`breadcrumb-bullets`) |
| `muted`     | bool   | `false`     | Muted links (`breadcrumb-muted`)                                                                     |

The component renders a `<nav aria-label="breadcrumbs">` around the list; other attributes go to the
`<ol class="breadcrumb">`.

`Breadcrumb:Item`:

| Prop     | Type    | Default | Description                                              |
| -------- | ------- | ------- | -------------------------------------------------------- |
| `href`   | string? | `null`  | Link target; without it, the item is plain text          |
| `active` | bool    | `false` | The current page: plain text, with `aria-current="page"` |
| `icon`   | string? | `null`  | Leading Tabler icon or UX Icons name                     |

Other attributes go to the `<li class="breadcrumb-item">`.

## Sub-components

| Component         | Renders                                                     |
| ----------------- | ----------------------------------------------------------- |
| `Breadcrumb:Item` | `<li class="breadcrumb-item">`, with an `<a>` when it links |

## Blocks

| Block     | Default                                                |
| --------- | ------------------------------------------------------ |
| `content` | A `Breadcrumb:Item` for each entry of the `items` prop |

The content of `Breadcrumb:Item` is its label, after the `icon`.
