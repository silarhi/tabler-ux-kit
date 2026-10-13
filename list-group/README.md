# List group

A bordered block of rows: a settings menu, a list of records, an activity feed, the steps of an onboarding.

```twig {"preview":true}
<twig:Tabler:ListGroup tag="nav" items="{{ [
    {label: 'Profile', href: '/settings/profile', active: true},
    {label: 'Notifications', href: '/settings/notifications'},
    {label: 'Billing', href: '/settings/billing'},
    {label: 'API tokens', href: '/settings/tokens', disabled: true},
] }}" />
```

`items` is an array of `{label, href?, active?, disabled?, variant?}`, rendered with `ListGroup:Item`. Pick the
element of the root with `tag`, for the content: `nav` with link items for navigation, `ul` or `ol` for a list (the
generated items then render as `<li>`), `div` (the default) otherwise.

## Installation

::: installation

## Items

`ListGroup:Item` renders an `<a>` when `href` is set and a `<button type="button">` when `button` is set (`href` wins
when both are). Both get
the hover and focus style of an actionable item (`list-group-item-action`). Otherwise the item is a `<div>`. `action`
forces that style on or off, here off for the last link:

```twig {"preview":true}
<twig:Tabler:ListGroup>
    <twig:Tabler:ListGroup:Item href="/invoices/1042">Invoice #1042: a link</twig:Tabler:ListGroup:Item>
    <twig:Tabler:ListGroup:Item button data-invoice="1043">Invoice #1043: a button</twig:Tabler:ListGroup:Item>
    <twig:Tabler:ListGroup:Item>Invoice #1044: plain text</twig:Tabler:ListGroup:Item>
    <twig:Tabler:ListGroup:Item href="/invoices/1045" action="{{ false }}">Invoice #1045: a link without the hover style</twig:Tabler:ListGroup:Item>
</twig:Tabler:ListGroup>
```

In a `ul` or `ol` list group, set `tag="li"` on each item that is not a link nor a button:

```twig {"preview":true}
<twig:Tabler:ListGroup tag="ul">
    <twig:Tabler:ListGroup:Item tag="li" label="PHP 8.4 or later" />
    <twig:Tabler:ListGroup:Item tag="li" label="Symfony 7.4 or later" />
    <twig:Tabler:ListGroup:Item tag="li" label="Symfony UX TwigComponent" />
</twig:Tabler:ListGroup>
```

## Active and disabled

`active` marks the current item, with `aria-current="true"`. `disabled` greys out an item the user cannot pick. A
disabled link loses its `href` and gets `aria-disabled="true"` and `tabindex="-1"`, so it cannot be followed nor
focused. A disabled button gets the `disabled` attribute.

```twig {"preview":true}
<twig:Tabler:ListGroup>
    <twig:Tabler:ListGroup:Item href="/projects/website" active>Website redesign</twig:Tabler:ListGroup:Item>
    <twig:Tabler:ListGroup:Item href="/projects/mobile-app">Mobile app</twig:Tabler:ListGroup:Item>
    <twig:Tabler:ListGroup:Item href="/projects/legacy-crm" disabled>Legacy CRM (archived)</twig:Tabler:ListGroup:Item>
    <twig:Tabler:ListGroup:Item button disabled>Data warehouse (no access)</twig:Tabler:ListGroup:Item>
</twig:Tabler:ListGroup>
```

## Variants

`variant` tints an item: `primary` `secondary` `success` `danger` `warning` `info` `dark` `light`.

```twig {"preview":true}
<twig:Tabler:ListGroup>
    <twig:Tabler:ListGroup:Item variant="success">Deployment #318 succeeded</twig:Tabler:ListGroup:Item>
    <twig:Tabler:ListGroup:Item variant="warning">Disk usage on db-01 is at 85%</twig:Tabler:ListGroup:Item>
    <twig:Tabler:ListGroup:Item variant="danger">Payment for invoice #1042 failed</twig:Tabler:ListGroup:Item>
    <twig:Tabler:ListGroup:Item variant="info">Maintenance scheduled for Sunday, 02:00</twig:Tabler:ListGroup:Item>
</twig:Tabler:ListGroup>
```

## Numbered

`numbered` numbers the items with a CSS counter. Use it on an `<ol>`, so the order is in the markup too:

```twig {"preview":true}
<twig:Tabler:ListGroup tag="ol" numbered items="{{ [
    {label: 'Create your organization'},
    {label: 'Invite your team'},
    {label: 'Connect your bank account'},
] }}" />
```

## Horizontal

`horizontal` lays the items out in a row. As a bare attribute, the row applies at every width. With a breakpoint
(`sm` `md` `lg` `xl` `xxl`), the items stack below it and line up from it:

```twig {"preview":true}
<twig:Tabler:ListGroup horizontal="md" class="mb-3">
    <twig:Tabler:ListGroup:Item>Draft: 4</twig:Tabler:ListGroup:Item>
    <twig:Tabler:ListGroup:Item>Sent: 12</twig:Tabler:ListGroup:Item>
    <twig:Tabler:ListGroup:Item>Paid: 37</twig:Tabler:ListGroup:Item>
</twig:Tabler:ListGroup>
<twig:Tabler:ListGroup horizontal>
    <twig:Tabler:ListGroup:Item>Monday</twig:Tabler:ListGroup:Item>
    <twig:Tabler:ListGroup:Item>Tuesday</twig:Tabler:ListGroup:Item>
    <twig:Tabler:ListGroup:Item>Wednesday</twig:Tabler:ListGroup:Item>
</twig:Tabler:ListGroup>
```

## In a card

`flush` removes the outer border and the rounded corners, so the list group sits edge to edge in a card. `card` gives
the items the horizontal padding of the card (`card-list-group`). `ListGroup:Header` splits the list into sections,
with a small uppercase label:

```twig {"preview":true}
<div class="card">
    <div class="card-header">
        <h3 class="card-title">Recent activity</h3>
    </div>
    <twig:Tabler:ListGroup flush card>
        <twig:Tabler:ListGroup:Header>Today</twig:Tabler:ListGroup:Header>
        <twig:Tabler:ListGroup:Item>Jane Cooper paid invoice #1042</twig:Tabler:ListGroup:Item>
        <twig:Tabler:ListGroup:Item>Paul Martin joined the team</twig:Tabler:ListGroup:Item>
        <twig:Tabler:ListGroup:Header>Yesterday</twig:Tabler:ListGroup:Header>
        <twig:Tabler:ListGroup:Item>Release v2.4.0 was deployed</twig:Tabler:ListGroup:Item>
    </twig:Tabler:ListGroup>
</div>
```

## Hoverable

`hoverable` highlights the row under the cursor, even for plain items, and reveals its `ListGroup:Actions`: a link on
the trailing edge of the item. `show` keeps the action visible, here for a user already in the favorites. Lay the
item out with a grid to put the action at the end:

```twig {"preview":true}
<div class="card">
    <twig:Tabler:ListGroup flush hoverable>
        {% for user in [
            {id: 12, name: 'Jane Cooper', email: 'jane.cooper@example.com', avatar: '/examples/avatar-1.jpg', favorite: true},
            {id: 27, name: 'Paul Martin', email: 'paul.martin@example.com', avatar: '/examples/avatar-2.jpg', favorite: false},
            {id: 31, name: 'Sophie Laurent', email: 'sophie.laurent@example.com', avatar: '/examples/avatar-3.jpg', favorite: false},
        ] %}
            <twig:Tabler:ListGroup:Item>
                <div class="row align-items-center">
                    <div class="col-auto">
                        <twig:Tabler:Avatar image="{{ user.avatar }}" />
                    </div>
                    <div class="col text-truncate">
                        <a href="/users/{{ user.id }}" class="text-reset d-block">{{ user.name }}</a>
                        <div class="text-secondary text-truncate">{{ user.email }}</div>
                    </div>
                    <div class="col-auto">
                        <twig:Tabler:ListGroup:Actions href="/users/{{ user.id }}/favorite" show="{{ user.favorite }}" aria-label="{{ user.favorite ? 'Remove ' ~ user.name ~ ' from favorites' : 'Add ' ~ user.name ~ ' to favorites' }}">
                            <twig:Tabler:Icon name="star" class="icon {{ user.favorite ? 'text-yellow' : 'text-secondary' }}" aria-hidden="true" />
                        </twig:Tabler:ListGroup:Actions>
                    </div>
                </div>
            </twig:Tabler:ListGroup:Item>
        {% endfor %}
    </twig:Tabler:ListGroup>
</div>
```

`ListGroup:Actions` is hidden with `opacity` only: it stays in the tab order, and keyboard users reach it without
seeing it. Never make it the only way to do something, and name it with an `aria-label`, since it usually holds an
icon only.

## Transparent

`transparent` drops the background and the borders of the items, for a side menu. It also sets a negative horizontal
margin of 1.25rem, the padding of a card body: in one, the labels line up with the rest of the content and the active
highlight spans the full width of the card.

```twig {"preview":true}
<div class="card">
    <div class="card-body">
        <twig:Tabler:ListGroup tag="nav" transparent>
            <twig:Tabler:ListGroup:Item href="/mail/inbox" active class="d-flex align-items-center">
                <twig:Tabler:Icon name="inbox" class="icon me-2" aria-hidden="true" /> Inbox
                <span class="badge bg-primary-lt ms-auto">14</span>
            </twig:Tabler:ListGroup:Item>
            <twig:Tabler:ListGroup:Item href="/mail/sent" class="d-flex align-items-center">
                <twig:Tabler:Icon name="send" class="icon me-2" aria-hidden="true" /> Sent
            </twig:Tabler:ListGroup:Item>
            <twig:Tabler:ListGroup:Item href="/mail/archive" class="d-flex align-items-center">
                <twig:Tabler:Icon name="archive" class="icon me-2" aria-hidden="true" /> Archive
            </twig:Tabler:ListGroup:Item>
        </twig:Tabler:ListGroup>
    </div>
</div>
```

## Props

`ListGroup`:

| Prop          | Type         | Default | Description                                                                                 |
| ------------- | ------------ | ------- | ------------------------------------------------------------------------------------------- |
| `tag`         | string       | `'div'` | `div` `ul` `ol` `nav`: the root element; generated items render as `<li>` in a `ul` or `ol` |
| `items`       | array?       | `null`  | `{label, href?, active?, disabled?, variant?}` entries, rendered with `ListGroup:Item`      |
| `flush`       | bool         | `false` | No outer border nor rounded corners (`list-group-flush`)                                    |
| `hoverable`   | bool         | `false` | Highlights the row under the cursor and reveals its actions (`list-group-hoverable`)        |
| `transparent` | bool         | `false` | No background nor borders on the items, for a side menu (`list-group-transparent`)          |
| `numbered`    | bool         | `false` | Numbers the items (`list-group-numbered`)                                                   |
| `horizontal`  | bool\|string | `false` | Items in a row: `true` for every width, or from a breakpoint `sm` `md` `lg` `xl` `xxl`      |
| `card`        | bool         | `false` | Card padding on the items (`card-list-group`)                                               |

Other attributes go to the root `<div class="list-group">` (or the `tag` set).

`ListGroup:Item`:

| Prop       | Type    | Default | Description                                                                             |
| ---------- | ------- | ------- | --------------------------------------------------------------------------------------- |
| `label`    | string? | `null`  | Item text                                                                               |
| `href`     | string? | `null`  | Renders an `<a href>`                                                                   |
| `button`   | bool    | `false` | Renders a `<button type="button">` (ignored with `href`)                                |
| `tag`      | string  | `'div'` | `div` `li`: the element of an item that is not a link nor a button                      |
| `action`   | bool?   | `null`  | Hover and focus style (`list-group-item-action`): `true` for links and buttons          |
| `active`   | bool    | `false` | Current item (`active`, `aria-current="true"`)                                          |
| `disabled` | bool    | `false` | Item the user cannot pick (`disabled`): see [Active and disabled](#active-and-disabled) |
| `variant`  | string? | `null`  | `primary` `secondary` `success` `danger` `warning` `info` `dark` `light`                |

Other attributes go to the `<a>`, `<button>`, `<div>` or `<li class="list-group-item">`. To drop the hover style of a
link, pass `action="{{ false }}"` (see [boolean props](https://tabler-ux-components.silarhi.dev/getting-started/composition/#boolean-props)).

`ListGroup:Header` takes `tag`: `div` (the default) or `li`, in a `ul` or `ol` list group.

`ListGroup:Actions`:

| Prop   | Type    | Default | Description                                |
| ------ | ------- | ------- | ------------------------------------------ |
| `href` | string? | `null`  | Link target, `#` when not set              |
| `show` | bool    | `false` | Always visible, not only on hover (`show`) |

Other attributes go to the `<a class="list-group-item-actions">`.

## Sub-components

| Component           | Renders                                                                          |
| ------------------- | -------------------------------------------------------------------------------- |
| `ListGroup:Item`    | `<div class="list-group-item">`, or an `<a>`, a `<button>` or an `<li>`: one row |
| `ListGroup:Header`  | `<div class="list-group-header">` (or `<li>`): a section label                   |
| `ListGroup:Actions` | `<a href="#" class="list-group-item-actions">`: a trailing link, shown on hover  |

## Blocks

| Block     | Default                                                                      |
| --------- | ---------------------------------------------------------------------------- |
| `content` | A `ListGroup:Item` for each entry of the `items` prop: replace it to compose |

The `content` block of `ListGroup:Item` holds its `label` prop: pass children for richer content.
