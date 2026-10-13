# Dropdown

A Bootstrap dropdown: a toggle and a menu of items, built from sub-components. It needs `tabler.js`.

```twig {"preview":true}
<twig:Tabler:Dropdown>
    <twig:Tabler:Dropdown:Toggle variant="primary">Actions</twig:Tabler:Dropdown:Toggle>
    <twig:Tabler:Dropdown:Menu>
        <twig:Tabler:Dropdown:Header>Invoice #1042</twig:Tabler:Dropdown:Header>
        <twig:Tabler:Dropdown:Item href="/invoices/1042/edit">Edit</twig:Tabler:Dropdown:Item>
        <twig:Tabler:Dropdown:Item href="/invoices/1042/duplicate">Duplicate</twig:Tabler:Dropdown:Item>
        <twig:Tabler:Dropdown:Divider />
        <twig:Tabler:Dropdown:Item href="/invoices/1042/delete" class="text-danger">Delete</twig:Tabler:Dropdown:Item>
    </twig:Tabler:Dropdown:Menu>
</twig:Tabler:Dropdown>
```

## Installation

::: installation

## Toggle

The toggle is a `<button type="button">`, so it never submits an enclosing form. Without `variant`, it is a plain
`.btn`. `noCaret` hides the caret, for an icon-only toggle:

```twig {"preview":true}
<div class="btn-list">
    <twig:Tabler:Dropdown>
        <twig:Tabler:Dropdown:Toggle>Plain</twig:Tabler:Dropdown:Toggle>
        <twig:Tabler:Dropdown:Menu>
            <twig:Tabler:Dropdown:Item>Edit</twig:Tabler:Dropdown:Item>
            <twig:Tabler:Dropdown:Item>Archive</twig:Tabler:Dropdown:Item>
        </twig:Tabler:Dropdown:Menu>
    </twig:Tabler:Dropdown>
    <twig:Tabler:Dropdown>
        <twig:Tabler:Dropdown:Toggle variant="secondary">Secondary</twig:Tabler:Dropdown:Toggle>
        <twig:Tabler:Dropdown:Menu>
            <twig:Tabler:Dropdown:Item>Edit</twig:Tabler:Dropdown:Item>
            <twig:Tabler:Dropdown:Item>Archive</twig:Tabler:Dropdown:Item>
        </twig:Tabler:Dropdown:Menu>
    </twig:Tabler:Dropdown>
    <twig:Tabler:Dropdown>
        <twig:Tabler:Dropdown:Toggle noCaret="{{ true }}" class="btn-icon" aria-label="More actions">
            <twig:Tabler:Icon name="dots-vertical" class="icon" />
        </twig:Tabler:Dropdown:Toggle>
        <twig:Tabler:Dropdown:Menu>
            <twig:Tabler:Dropdown:Item>Edit</twig:Tabler:Dropdown:Item>
            <twig:Tabler:Dropdown:Item>Archive</twig:Tabler:Dropdown:Item>
        </twig:Tabler:Dropdown:Menu>
    </twig:Tabler:Dropdown>
</div>
```

## Split button

`split` makes the toggle the caret-only half of a split button: put it after a [Button](https://tabler-ux-components.silarhi.dev/components/actions/button/)
in a [ButtonGroup](https://tabler-ux-components.silarhi.dev/components/actions/button-group/), followed by the menu. Give it an `aria-label`:

```twig {"preview":true}
<twig:Tabler:ButtonGroup aria-label="Save options">
    <twig:Tabler:Button variant="primary">Save</twig:Tabler:Button>
    <twig:Tabler:Dropdown:Toggle variant="primary" split="{{ true }}" aria-label="More save options" />
    <twig:Tabler:Dropdown:Menu>
        <twig:Tabler:Dropdown:Item href="/invoices/1042/save-draft" icon="file-pencil">Save as draft</twig:Tabler:Dropdown:Item>
        <twig:Tabler:Dropdown:Item href="/invoices/1042/save-send" icon="send">Save and send</twig:Tabler:Dropdown:Item>
    </twig:Tabler:Dropdown:Menu>
</twig:Tabler:ButtonGroup>
```

## Menu alignment

`end` aligns the menu with the end of the toggle, for a toggle on the right of the page:

```twig {"preview":true}
<div class="d-flex justify-content-end">
    <twig:Tabler:Dropdown>
        <twig:Tabler:Dropdown:Toggle>Jane Doe</twig:Tabler:Dropdown:Toggle>
        <twig:Tabler:Dropdown:Menu end="{{ true }}">
            <twig:Tabler:Dropdown:Item href="/profile">Profile</twig:Tabler:Dropdown:Item>
            <twig:Tabler:Dropdown:Item href="/settings">Settings</twig:Tabler:Dropdown:Item>
            <twig:Tabler:Dropdown:Divider />
            <twig:Tabler:Dropdown:Item href="/logout">Sign out</twig:Tabler:Dropdown:Item>
        </twig:Tabler:Dropdown:Menu>
    </twig:Tabler:Dropdown>
</div>
```

## Direction

`direction` sets where the menu opens: `up` (`dropup`), `end` (`dropend`) or `start` (`dropstart`). The menu flips to
the other side when there is no room:

```twig {"preview":true}
<div class="d-flex flex-column align-items-center gap-5">
    <div class="btn-list">
        <twig:Tabler:Dropdown direction="start">
            <twig:Tabler:Dropdown:Toggle>Dropstart</twig:Tabler:Dropdown:Toggle>
            <twig:Tabler:Dropdown:Menu>
                <twig:Tabler:Dropdown:Item>Edit</twig:Tabler:Dropdown:Item>
                <twig:Tabler:Dropdown:Item>Archive</twig:Tabler:Dropdown:Item>
            </twig:Tabler:Dropdown:Menu>
        </twig:Tabler:Dropdown>
        <twig:Tabler:Dropdown direction="end">
            <twig:Tabler:Dropdown:Toggle>Dropend</twig:Tabler:Dropdown:Toggle>
            <twig:Tabler:Dropdown:Menu>
                <twig:Tabler:Dropdown:Item>Edit</twig:Tabler:Dropdown:Item>
                <twig:Tabler:Dropdown:Item>Archive</twig:Tabler:Dropdown:Item>
            </twig:Tabler:Dropdown:Menu>
        </twig:Tabler:Dropdown>
    </div>
    <twig:Tabler:Dropdown direction="up">
        <twig:Tabler:Dropdown:Toggle>Dropup</twig:Tabler:Dropdown:Toggle>
        <twig:Tabler:Dropdown:Menu>
            <twig:Tabler:Dropdown:Item>Edit</twig:Tabler:Dropdown:Item>
            <twig:Tabler:Dropdown:Item>Archive</twig:Tabler:Dropdown:Item>
        </twig:Tabler:Dropdown:Menu>
    </twig:Tabler:Dropdown>
</div>
```

Dropdowns do not nest into submenus: `Dropdown:Toggle` is a button (`.btn`), not the `.dropdown-item` a submenu
trigger needs.

## Menu styles

`arrow` adds a small arrow pointing at the toggle, `dark` a dark menu on a light page, and `scrollable` caps the menu
height and scrolls the rest:

```twig {"preview":true}
<div class="btn-list">
    <twig:Tabler:Dropdown>
        <twig:Tabler:Dropdown:Toggle>Arrow</twig:Tabler:Dropdown:Toggle>
        <twig:Tabler:Dropdown:Menu arrow="{{ true }}">
            <twig:Tabler:Dropdown:Item href="/profile">Profile</twig:Tabler:Dropdown:Item>
            <twig:Tabler:Dropdown:Item href="/settings">Settings</twig:Tabler:Dropdown:Item>
        </twig:Tabler:Dropdown:Menu>
    </twig:Tabler:Dropdown>
    <twig:Tabler:Dropdown>
        <twig:Tabler:Dropdown:Toggle>Dark</twig:Tabler:Dropdown:Toggle>
        <twig:Tabler:Dropdown:Menu dark="{{ true }}">
            <twig:Tabler:Dropdown:Item href="/profile">Profile</twig:Tabler:Dropdown:Item>
            <twig:Tabler:Dropdown:Item href="/settings">Settings</twig:Tabler:Dropdown:Item>
        </twig:Tabler:Dropdown:Menu>
    </twig:Tabler:Dropdown>
    <twig:Tabler:Dropdown>
        <twig:Tabler:Dropdown:Toggle>Scrollable</twig:Tabler:Dropdown:Toggle>
        <twig:Tabler:Dropdown:Menu scrollable="{{ true }}">
            {% for country in ['Austria', 'Belgium', 'Denmark', 'Finland', 'France', 'Germany', 'Ireland', 'Italy', 'Netherlands', 'Portugal', 'Spain', 'Sweden'] %}
                <twig:Tabler:Dropdown:Item href="?country={{ country|lower }}">{{ country }}</twig:Tabler:Dropdown:Item>
            {% endfor %}
        </twig:Tabler:Dropdown:Menu>
    </twig:Tabler:Dropdown>
</div>
```

`card` turns the menu into a panel for rich content: put a [Card](https://tabler-ux-components.silarhi.dev/components/content/card/) in it.

```twig {"preview":true}
<twig:Tabler:Dropdown>
    <twig:Tabler:Dropdown:Toggle noCaret="{{ true }}" class="btn-icon" aria-label="Notifications">
        <twig:Tabler:Icon name="bell" class="icon" />
    </twig:Tabler:Dropdown:Toggle>
    <twig:Tabler:Dropdown:Menu card="{{ true }}">
        <twig:Tabler:Card>
            <twig:Tabler:Card:Header>
                <twig:Tabler:Card:Title>Notifications</twig:Tabler:Card:Title>
            </twig:Tabler:Card:Header>
            <twig:Tabler:Card:Body>
                <p class="mb-2"><strong>Jane Doe</strong> commented on invoice #1042.</p>
                <p class="mb-0"><strong>John Smith</strong> approved the March expenses.</p>
            </twig:Tabler:Card:Body>
        </twig:Tabler:Card>
    </twig:Tabler:Dropdown:Menu>
</twig:Tabler:Dropdown>
```

## Columns and text

`Dropdown:Columns` splits a long menu into `Dropdown:Column`s. `Dropdown:Text` is plain text that is not an action:

```twig {"preview":true}
<twig:Tabler:Dropdown>
    <twig:Tabler:Dropdown:Toggle variant="primary">Reports</twig:Tabler:Dropdown:Toggle>
    <twig:Tabler:Dropdown:Menu>
        <twig:Tabler:Dropdown:Text>Last updated today at 9:00</twig:Tabler:Dropdown:Text>
        <twig:Tabler:Dropdown:Divider />
        <twig:Tabler:Dropdown:Columns>
            <twig:Tabler:Dropdown:Column>
                <twig:Tabler:Dropdown:Header>Sales</twig:Tabler:Dropdown:Header>
                <twig:Tabler:Dropdown:Item href="/reports/revenue">Revenue</twig:Tabler:Dropdown:Item>
                <twig:Tabler:Dropdown:Item href="/reports/invoices">Invoices</twig:Tabler:Dropdown:Item>
                <twig:Tabler:Dropdown:Item href="/reports/customers">Customers</twig:Tabler:Dropdown:Item>
            </twig:Tabler:Dropdown:Column>
            <twig:Tabler:Dropdown:Column>
                <twig:Tabler:Dropdown:Header>Operations</twig:Tabler:Dropdown:Header>
                <twig:Tabler:Dropdown:Item href="/reports/expenses">Expenses</twig:Tabler:Dropdown:Item>
                <twig:Tabler:Dropdown:Item href="/reports/timesheets">Timesheets</twig:Tabler:Dropdown:Item>
                <twig:Tabler:Dropdown:Item href="/reports/stock">Stock</twig:Tabler:Dropdown:Item>
            </twig:Tabler:Dropdown:Column>
        </twig:Tabler:Dropdown:Columns>
    </twig:Tabler:Dropdown:Menu>
</twig:Tabler:Dropdown>
```

## Items

`active` highlights an item, `disabled` makes it non-interactive. `icon` puts a Tabler icon before the label, with the
`dropdown-item-icon` class:

```twig {"preview":true}
<twig:Tabler:Dropdown>
    <twig:Tabler:Dropdown:Toggle>Sort by</twig:Tabler:Dropdown:Toggle>
    <twig:Tabler:Dropdown:Menu>
        <twig:Tabler:Dropdown:Item href="?sort=date" icon="calendar" active="{{ true }}">Date</twig:Tabler:Dropdown:Item>
        <twig:Tabler:Dropdown:Item href="?sort=amount" icon="currency-euro">Amount</twig:Tabler:Dropdown:Item>
        <twig:Tabler:Dropdown:Item href="?sort=customer" icon="user" disabled="{{ true }}">Customer</twig:Tabler:Dropdown:Item>
    </twig:Tabler:Dropdown:Menu>
</twig:Tabler:Dropdown>
```

`Dropdown:Indicator` is a leading slot in an item for a small marker, such as an avatar, a checkbox or a flag
(`dropdown-item-indicator`):

```twig {"preview":true}
<twig:Tabler:Dropdown>
    <twig:Tabler:Dropdown:Toggle>Assign to</twig:Tabler:Dropdown:Toggle>
    <twig:Tabler:Dropdown:Menu>
        {% for person in [
            {name: 'Jane Cooper', avatar: '/examples/avatar-1.jpg'},
            {name: 'Wade Warren', avatar: '/examples/avatar-2.jpg'},
            {name: 'Esther Howard', avatar: '/examples/avatar-3.jpg'},
        ] %}
            <twig:Tabler:Dropdown:Item href="?assignee={{ loop.index }}">
                <twig:Tabler:Dropdown:Indicator><twig:Tabler:Avatar size="xs" image="{{ person.avatar }}" /></twig:Tabler:Dropdown:Indicator>
                {{ person.name }}
            </twig:Tabler:Dropdown:Item>
        {% endfor %}
    </twig:Tabler:Dropdown:Menu>
</twig:Tabler:Dropdown>
```

An item holding a checkbox or a radio cannot be a link: set `tag="label"` on it, so a click anywhere on the item toggles
the input. `tag` also takes `button`, for an action that is not a navigation. Add `data-bs-auto-close="outside"` to the
toggle to keep the menu open while the user ticks several options:

```twig {"preview":true}
<twig:Tabler:Dropdown>
    <twig:Tabler:Dropdown:Toggle data-bs-auto-close="outside">Columns</twig:Tabler:Dropdown:Toggle>
    <twig:Tabler:Dropdown:Menu>
        {% for column in [{label: 'Customer', checked: true}, {label: 'Amount', checked: true}, {label: 'Due date', checked: false}] %}
            <twig:Tabler:Dropdown:Item tag="label">
                <twig:Tabler:Dropdown:Indicator><input type="checkbox" class="form-check-input m-0"{% if column.checked %} checked{% endif %}></twig:Tabler:Dropdown:Indicator>
                {{ column.label }}
            </twig:Tabler:Dropdown:Item>
        {% endfor %}
    </twig:Tabler:Dropdown:Menu>
</twig:Tabler:Dropdown>
```

## Sub-components

| Component            | Renders                                                                                 |
| -------------------- | --------------------------------------------------------------------------------------- |
| `Dropdown`           | `<div class="dropdown">` around the toggle and the menu                                 |
| `Dropdown:Toggle`    | `<button type="button" class="btn dropdown-toggle" data-bs-toggle="dropdown">`          |
| `Dropdown:Menu`      | `<div class="dropdown-menu">`                                                           |
| `Dropdown:Item`      | `<a class="dropdown-item">`, or the element set by `tag`                                |
| `Dropdown:Header`    | `<div class="dropdown-header">`: a non-interactive label above a group of items         |
| `Dropdown:Text`      | `<span class="dropdown-item-text">`: plain text that is not an action                   |
| `Dropdown:Indicator` | `<span class="dropdown-item-indicator">`: a leading avatar, checkbox or flag in an item |
| `Dropdown:Divider`   | `<div class="dropdown-divider">`: a separator between groups of items                   |
| `Dropdown:Columns`   | `<div class="dropdown-menu-columns">`: splits the menu into columns                     |
| `Dropdown:Column`    | `<div class="dropdown-menu-column">`: one column of `Dropdown:Columns`                  |

Attributes of each component go to its root element.

## Props

`Dropdown:Header`, `Dropdown:Text`, `Dropdown:Indicator`, `Dropdown:Divider`, `Dropdown:Columns` and `Dropdown:Column`
take no props.

### Dropdown

| Prop        | Type   | Default  | Description                                                                      |
| ----------- | ------ | -------- | -------------------------------------------------------------------------------- |
| `direction` | string | `'down'` | `down` `up` `end` `start`: where the menu opens (`dropup` `dropend` `dropstart`) |

### Dropdown:Toggle

| Prop      | Type    | Default | Description                                                                                         |
| --------- | ------- | ------- | --------------------------------------------------------------------------------------------------- |
| `variant` | string? | `null`  | `primary` `secondary` `success` `danger` `warning` `info` `dark` `light`; `null` for a plain `.btn` |
| `noCaret` | bool    | `false` | Hides the caret (no `dropdown-toggle` class)                                                        |
| `split`   | bool    | `false` | Caret-only half of a split button (`dropdown-toggle-split`)                                         |

### Dropdown:Menu

| Prop         | Type | Default | Description                                              |
| ------------ | ---- | ------- | -------------------------------------------------------- |
| `end`        | bool | `false` | Aligns the menu to the end (`dropdown-menu-end`)         |
| `arrow`      | bool | `false` | Arrow pointing at the toggle (`dropdown-menu-arrow`)     |
| `dark`       | bool | `false` | Dark menu (`dropdown-menu-dark`)                         |
| `scrollable` | bool | `false` | Caps the height and scrolls (`dropdown-menu-scrollable`) |
| `card`       | bool | `false` | Panel for rich content (`dropdown-menu-card`)            |

### Dropdown:Item

| Prop       | Type    | Default | Description                                                                                   |
| ---------- | ------- | ------- | --------------------------------------------------------------------------------------------- |
| `tag`      | string  | `'a'`   | `a` `button` `label`… Only an `<a>` gets the `href`; a `button` gets `type="button"`          |
| `href`     | string? | `null`  | Link target, `#` when `null`                                                                  |
| `active`   | bool    | `false` | Highlighted item (`active`)                                                                   |
| `disabled` | bool    | `false` | Non-interactive item (`disabled`, `aria-disabled`, or the `disabled` attribute on a `button`) |
| `icon`     | string? | `null`  | Leading Tabler icon or UX Icons name (`dropdown-item-icon`)                                   |
