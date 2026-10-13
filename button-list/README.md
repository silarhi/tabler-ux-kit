# ButtonList

Lays its children out in a row with Tabler's `btn-list`: a flex container with a `0.5rem` gap that wraps when the row
is too narrow. Unlike `ButtonGroup`, the buttons keep their own borders and radius.

```twig {"preview":true}
<twig:Tabler:ButtonList>
    <twig:Tabler:Button variant="primary">Save changes</twig:Tabler:Button>
    <twig:Tabler:Button variant="default">Save and continue</twig:Tabler:Button>
    <twig:Tabler:Button variant="default" appearance="ghost">Cancel</twig:Tabler:Button>
</twig:Tabler:ButtonList>
```

## Installation

::: installation

## Alignment

`center` centers the row (`btn-list-center`). To push the buttons to the end, add the `justify-content-end` class:

```twig {"preview":true}
<div class="space-y">
    <twig:Tabler:ButtonList center="{{ true }}">
        <twig:Tabler:Button variant="primary">Accept invitation</twig:Tabler:Button>
        <twig:Tabler:Button variant="default">Decline</twig:Tabler:Button>
    </twig:Tabler:ButtonList>
    <twig:Tabler:ButtonList class="justify-content-end">
        <twig:Tabler:Button variant="default">Cancel</twig:Tabler:Button>
        <twig:Tabler:Button variant="danger">Delete project</twig:Tabler:Button>
    </twig:Tabler:ButtonList>
</div>
```

## Wrapping

The buttons move to the next line when they do not fit, with the same gap between rows:

```twig {"preview":true}
<div style="max-width: 22rem">
    <twig:Tabler:ButtonList>
        <twig:Tabler:Button variant="default" size="sm">Unpaid</twig:Tabler:Button>
        <twig:Tabler:Button variant="default" size="sm">Overdue</twig:Tabler:Button>
        <twig:Tabler:Button variant="default" size="sm">Due this week</twig:Tabler:Button>
        <twig:Tabler:Button variant="default" size="sm">Disputed</twig:Tabler:Button>
        <twig:Tabler:Button variant="default" size="sm">Partially paid</twig:Tabler:Button>
        <twig:Tabler:Button variant="default" size="sm">Written off</twig:Tabler:Button>
    </twig:Tabler:ButtonList>
</div>
```

## Mixed content

Any child is spaced the same way: a button group or a dropdown sits next to plain buttons.

```twig {"preview":true}
<twig:Tabler:ButtonList>
    <twig:Tabler:Button variant="primary">
        <twig:Tabler:Icon name="plus" class="icon" /> New invoice
    </twig:Tabler:Button>
    <twig:Tabler:ButtonGroup aria-label="View">
        <twig:Tabler:ButtonGroup:Toggle id="view-list" name="view" value="list" checked="{{ true }}">List</twig:Tabler:ButtonGroup:Toggle>
        <twig:Tabler:ButtonGroup:Toggle id="view-board" name="view" value="board">Board</twig:Tabler:ButtonGroup:Toggle>
    </twig:Tabler:ButtonGroup>
    <twig:Tabler:Dropdown>
        <twig:Tabler:Dropdown:Toggle>Export</twig:Tabler:Dropdown:Toggle>
        <twig:Tabler:Dropdown:Menu>
            <twig:Tabler:Dropdown:Item>CSV</twig:Tabler:Dropdown:Item>
            <twig:Tabler:Dropdown:Item>PDF</twig:Tabler:Dropdown:Item>
        </twig:Tabler:Dropdown:Menu>
    </twig:Tabler:Dropdown>
</twig:Tabler:ButtonList>
```

## Props

| Prop     | Type | Default | Description                         |
| -------- | ---- | ------- | ----------------------------------- |
| `center` | bool | `false` | Centers the row (`btn-list-center`) |

Other attributes go to the root `<div class="btn-list">`.

## Blocks

| Block     | Default                          |
| --------- | -------------------------------- |
| `content` | Empty: the children, the buttons |
