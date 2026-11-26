# List

A `<ul>` with Tabler's list helpers, for a list that needs no borders: people, links in a footer, the steps of a
procedure. For bordered rows, use [List group](https://tabler-ux-components.silarhi.dev/components/content/list-group/).

```twig {"preview":true}
<twig:Tabler:List separated="{{ true }}" unstyled="{{ true }}" class="mb-0">
    {% for person in [
        {name: 'Jane Cooper', role: 'Account manager', avatar: '/examples/avatar-1.jpg'},
        {name: 'Wade Warren', role: 'Accountant', avatar: '/examples/avatar-2.jpg'},
        {name: 'Esther Howard', role: 'Sales', avatar: '/examples/avatar-3.jpg'},
    ] %}
        <twig:Tabler:List:Item class="d-flex align-items-center gap-2">
            <twig:Tabler:Avatar size="sm" image="{{ person.avatar }}" />
            <div>
                <div class="fw-medium">{{ person.name }}</div>
                <div class="text-secondary small">{{ person.role }}</div>
            </div>
        </twig:Tabler:List:Item>
    {% endfor %}
</twig:Tabler:List>
```

`separated` stacks the items with a gap (`list-separated`), for items that are blocks, such as a picture next to two
lines of text. `unstyled` removes the bullets and the indent (`list-unstyled`).

## Installation

::: installation

## Inline

`inline` lays the items out in a row (`list-inline`), and its `List:Item`s follow it (`list-inline-item`). `dots` adds a
dot between the items (`list-inline-dots`), and has no effect without `inline`:

```twig {"preview":true}
<twig:Tabler:List inline="{{ true }}" dots="{{ true }}" class="mb-0">
    <twig:Tabler:List:Item><a href="/docs" class="link-secondary">Documentation</a></twig:Tabler:List:Item>
    <twig:Tabler:List:Item><a href="/license" class="link-secondary">License</a></twig:Tabler:List:Item>
    <twig:Tabler:List:Item><a href="/changelog" class="link-secondary">Changelog</a></twig:Tabler:List:Item>
</twig:Tabler:List>
```

## Ordered

`ordered` renders an `<ol>`, for items whose order matters:

```twig {"preview":true}
<twig:Tabler:List ordered="{{ true }}" class="mb-0">
    <twig:Tabler:List:Item>Install the bundle with Composer.</twig:Tabler:List:Item>
    <twig:Tabler:List:Item>Load the Tabler stylesheet and script.</twig:Tabler:List:Item>
    <twig:Tabler:List:Item>Render your first component.</twig:Tabler:List:Item>
</twig:Tabler:List>
```

## Icons

`icon` replaces the bullets with icons (`list-icon`, Tabler 1.7+), for the features of a plan or the steps of a setup.
The first icon of each item is its marker, centered on the first line: the `icon` of a `List:Item`. `variant` on the
list colors every marker, `variant` on an item only its own:

```twig {"preview":true}
<twig:Tabler:List icon variant="success" class="mb-0">
    {% for feature in ['Unlimited projects', 'Priority support', 'Custom domains'] %}
        <twig:Tabler:List:Item icon="check">{{ feature }}</twig:Tabler:List:Item>
    {% endfor %}
    <twig:Tabler:List:Item icon="x" variant="danger">No single sign-on</twig:Tabler:List:Item>
</twig:Tabler:List>
```

With `icon`, `inline` lays short entries out in a row that wraps (`list-icon-inline`) instead of `list-inline`, and its
items get no `list-inline-item`:

```twig {"preview":true}
<twig:Tabler:List icon inline class="mb-0">
    <twig:Tabler:List:Item icon="mail">hello@example.com</twig:Tabler:List:Item>
    <twig:Tabler:List:Item icon="phone">+33 5 61 00 00 00</twig:Tabler:List:Item>
    <twig:Tabler:List:Item icon="map-pin">Toulouse, France</twig:Tabler:List:Item>
</twig:Tabler:List>
```

## Props

| Prop        | Type    | Default | Description                                                                                    |
| ----------- | ------- | ------- | ---------------------------------------------------------------------------------------------- |
| `separated` | bool    | `false` | Stacks the items with a gap (`list-separated`)                                                 |
| `inline`    | bool    | `false` | Items in a row (`list-inline`), its `List:Item`s following it; with `icon`, `list-icon-inline` |
| `dots`      | bool    | `false` | With `inline`: a dot between the items (`list-inline-dots`)                                    |
| `unstyled`  | bool    | `false` | No bullets and no indent (`list-unstyled`)                                                     |
| `ordered`   | bool    | `false` | Renders an `<ol>` instead of a `<ul>`                                                          |
| `icon`      | bool    | `false` | Icons instead of bullets (`list-icon`, Tabler 1.7+)                                            |
| `variant`   | string? | `null`  | With `icon`: the color of every marker (`--tblr-list-icon-color`), a semantic color            |

Other attributes go to the root `<ul>` (or `<ol>`).

`List:Item`:

| Prop      | Type    | Default | Description                                                                   |
| --------- | ------- | ------- | ----------------------------------------------------------------------------- |
| `inline`  | bool?   | `null`  | Item of an inline list (`list-inline-item`); `null` follows the parent `List` |
| `icon`    | string? | `null`  | Icon before the content: the marker of an icon list                           |
| `variant` | string? | `null`  | Color of that icon (`text-{variant}`), overriding the color of the list       |

Other attributes go to the `<li>`. An item placed outside a `List`, e.g. in a list of your own markup, needs `inline`
set by hand; `inline="{{ false }}"` keeps an item of an inline list out of the row.

## Sub-components

| Component   | Renders               |
| ----------- | --------------------- |
| `List:Item` | `<li>`: one list item |

## Blocks

| Block     | Default                               |
| --------- | ------------------------------------- |
| `content` | Empty: the children, the `List:Item`s |

`List:Item` has an `icon` block, the `Icon` of its `icon` and `variant` props, before its `content`.

`List:Item` has an empty `content` block too, for the item content.
