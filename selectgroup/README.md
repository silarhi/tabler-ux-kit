# Selectgroup

A set of radios or checkboxes styled as buttons (`.form-selectgroup`), for a filter bar or a set of options outside a
Symfony form. The real inputs stay in the markup, hidden with CSS: the arrow keys, the space bar and form submission
work as usual.

```twig {"preview":true}
<twig:Tabler:Selectgroup name="language" items="{{ [
    {value: 'html', label: 'HTML', checked: true},
    {value: 'css', label: 'CSS'},
    {value: 'php', label: 'PHP'},
    {value: 'js', label: 'JavaScript'},
] }}" role="group" aria-label="Language" />
```

Each entry of `items` is a `Selectgroup:Item`: a `value`, and an optional `label`, `icon`, `iconOnly`, `checked` and
`disabled`. Give the group an accessible name: `role="group"` and an `aria-label`, or a `<fieldset>` with a `<legend>`
around it.

## Installation

::: installation

## Several choices

`type="checkbox"` lets the user pick several options; end the `name` with `[]` so the server gets them all:

```twig {"preview":true}
<twig:Tabler:Selectgroup name="status[]" type="checkbox" items="{{ [
    {value: 'open', label: 'Open', checked: true},
    {value: 'review', label: 'In review', checked: true},
    {value: 'closed', label: 'Closed'},
    {value: 'archived', label: 'Archived', disabled: true},
] }}" role="group" aria-label="Status" />
```

## Icons

`icon` puts an icon before the label. With `iconOnly`, only the icon shows, and the label becomes the `aria-label` of
the input:

```twig {"preview":true}
<div class="d-flex flex-column gap-3">
    <twig:Tabler:Selectgroup name="weather[]" type="checkbox" items="{{ [
        {value: 'sun', label: 'Sunny', icon: 'sun', iconOnly: true, checked: true},
        {value: 'moon', label: 'Clear night', icon: 'moon', iconOnly: true},
        {value: 'rain', label: 'Rain', icon: 'cloud-rain', iconOnly: true},
        {value: 'other', label: 'Other'},
    ] }}" role="group" aria-label="Weather" />
    <twig:Tabler:Selectgroup name="view" items="{{ [
        {value: 'home', label: 'Home', icon: 'home', checked: true},
        {value: 'user', label: 'User', icon: 'user'},
        {value: 'settings', label: 'Settings', icon: 'settings'},
    ] }}" role="group" aria-label="View" />
</div>
```

## Pills

```twig {"preview":true}
<twig:Tabler:Selectgroup name="tags[]" type="checkbox" variant="pills" items="{{ [
    {value: 'bug', label: 'Bug', checked: true},
    {value: 'feature', label: 'Feature'},
    {value: 'docs', label: 'Documentation'},
    {value: 'question', label: 'Question'},
] }}" role="group" aria-label="Tags" />
```

## Boxes

`variant="boxes"` turns each option into a box with a check mark, round for radios and square for checkboxes.
`vertical` stacks the items in a column:

```twig {"preview":true}
<twig:Tabler:Selectgroup name="plan" variant="boxes" vertical="{{ true }}" items="{{ [
    {value: 'free', label: 'Free'},
    {value: 'pro', label: 'Pro', checked: true},
    {value: 'team', label: 'Team'},
] }}" role="group" aria-label="Plan" />
```

## Composed

The tag content replaces the items: place `Selectgroup:Item` yourself, each with its `name`. The content of an item
replaces its icon and label; `check` adds the check mark of a box:

```twig {"preview":true}
<twig:Tabler:Selectgroup variant="boxes" vertical="{{ true }}" role="group" aria-label="Billing">
    <twig:Tabler:Selectgroup:Item name="billing" value="monthly" check="{{ true }}" class="flex-fill">
        <strong>Monthly</strong> — $29 per month
    </twig:Tabler:Selectgroup:Item>
    <twig:Tabler:Selectgroup:Item name="billing" value="yearly" check="{{ true }}" checked="{{ true }}" class="flex-fill">
        <strong>Yearly</strong> — $290 per year, two months free
    </twig:Tabler:Selectgroup:Item>
</twig:Tabler:Selectgroup>
```

## Props

| Prop       | Type    | Default   | Description                                                                                   |
| ---------- | ------- | --------- | --------------------------------------------------------------------------------------------- |
| `name`     | string? | `null`    | The `name` of every input; end it with `[]` for checkboxes                                    |
| `type`     | string  | `'radio'` | `radio` (one choice) or `checkbox` (several)                                                  |
| `items`    | list    | `[]`      | `{value, label?, icon?, iconOnly?, checked?, disabled?}` entries, one `Selectgroup:Item` each |
| `variant`  | string? | `null`    | `pills` (`form-selectgroup-pills`) or `boxes` (`form-selectgroup-boxes`, with a check)        |
| `vertical` | bool    | `false`   | Stacks the items in a column (`form-selectgroup-vertical`)                                    |

Other attributes go to the root `<div class="form-selectgroup">`.

### Selectgroup:Item

| Prop       | Type    | Default   | Description                                                   |
| ---------- | ------- | --------- | ------------------------------------------------------------- |
| `type`     | string  | `'radio'` | `radio` or `checkbox`                                         |
| `name`     | string? | `null`    | The `name` of the input                                       |
| `value`    | string? | `null`    | The `value` of the input                                      |
| `label`    | string? | `null`    | The option text                                               |
| `icon`     | string? | `null`    | Tabler icon name (or ux-icons name) before the text           |
| `iconOnly` | bool    | `false`   | Shows only the icon; `label` becomes the input's `aria-label` |
| `checked`  | bool    | `false`   | Initially selected                                            |
| `disabled` | bool    | `false`   | Cannot be selected                                            |
| `check`    | bool    | `false`   | Adds a check mark before the content (`Selectgroup:Check`)    |

Other attributes go to its root `<label>`.

### Selectgroup:Label

| Prop    | Type | Default | Description                                                      |
| ------- | ---- | ------- | ---------------------------------------------------------------- |
| `check` | bool | `false` | Puts a `Selectgroup:Check` before the content, laid out as a box |

## Sub-components

| Component           | Renders                                                                           |
| ------------------- | --------------------------------------------------------------------------------- |
| `Selectgroup:Item`  | `<label class="form-selectgroup-item">`, with the hidden `form-selectgroup-input` |
| `Selectgroup:Label` | `<span class="form-selectgroup-label">`, the visible part of an item              |
| `Selectgroup:Check` | `<span class="form-selectgroup-check">`, the check mark of a box                  |

## Blocks

| Block     | Default                                   |
| --------- | ----------------------------------------- |
| `items`   | A `Selectgroup:Item` per entry of `items` |
| `content` | `items`: replace it to compose freely     |

`Selectgroup:Item` has an `icon` block (a `Tabler:Icon` named `icon`) and a `content` block (`icon` and the `label`),
which its tag content replaces.
