# ButtonToolbar

Combines button groups into one toolbar, Bootstrap's `btn-toolbar`: a flex row that wraps. The root gets
`role="toolbar"`: give it an `aria-label`. The toolbar adds no space between its children, so add a gap class such as
`gap-2`.

```twig {"preview":true}
<twig:Tabler:ButtonToolbar aria-label="Editor toolbar" class="gap-2">
    <twig:Tabler:ButtonGroup aria-label="Formatting">
        <twig:Tabler:Button variant="default" iconOnly="{{ true }}" aria-label="Bold">
            <twig:Tabler:Icon name="bold" class="icon" />
        </twig:Tabler:Button>
        <twig:Tabler:Button variant="default" iconOnly="{{ true }}" aria-label="Italic">
            <twig:Tabler:Icon name="italic" class="icon" />
        </twig:Tabler:Button>
        <twig:Tabler:Button variant="default" iconOnly="{{ true }}" aria-label="Underline">
            <twig:Tabler:Icon name="underline" class="icon" />
        </twig:Tabler:Button>
    </twig:Tabler:ButtonGroup>
    <twig:Tabler:ButtonGroup aria-label="Lists">
        <twig:Tabler:Button variant="default" iconOnly="{{ true }}" aria-label="Bulleted list">
            <twig:Tabler:Icon name="list" class="icon" />
        </twig:Tabler:Button>
        <twig:Tabler:Button variant="default" iconOnly="{{ true }}" aria-label="Numbered list">
            <twig:Tabler:Icon name="list-numbers" class="icon" />
        </twig:Tabler:Button>
    </twig:Tabler:ButtonGroup>
    <twig:Tabler:ButtonGroup aria-label="History">
        <twig:Tabler:Button variant="default" iconOnly="{{ true }}" aria-label="Undo">
            <twig:Tabler:Icon name="arrow-back-up" class="icon" />
        </twig:Tabler:Button>
        <twig:Tabler:Button variant="default" iconOnly="{{ true }}" aria-label="Redo">
            <twig:Tabler:Icon name="arrow-forward-up" class="icon" />
        </twig:Tabler:Button>
    </twig:Tabler:ButtonGroup>
</twig:Tabler:ButtonToolbar>
```

## Installation

::: installation

## Input groups

An input group placed in the toolbar keeps its natural width instead of stretching:

```twig {"preview":true}
<twig:Tabler:ButtonToolbar aria-label="Pagination" class="gap-2">
    <twig:Tabler:ButtonGroup aria-label="Pages">
        <twig:Tabler:Button variant="default">1</twig:Tabler:Button>
        <twig:Tabler:Button variant="default">2</twig:Tabler:Button>
        <twig:Tabler:Button variant="default">3</twig:Tabler:Button>
    </twig:Tabler:ButtonGroup>
    <div class="input-group">
        <span class="input-group-text" id="go-to-page">Go to page</span>
        <input type="number" class="form-control" min="1" style="width: 5rem" aria-describedby="go-to-page">
    </div>
</twig:Tabler:ButtonToolbar>
```

## Spacing

Flex utilities lay the groups out, for example `justify-content-between` to push them to both ends:

```twig {"preview":true}
<twig:Tabler:ButtonToolbar aria-label="Customer list toolbar" class="justify-content-between gap-2">
    <twig:Tabler:ButtonGroup aria-label="Selection">
        <twig:Tabler:Button variant="default">Select all</twig:Tabler:Button>
        <twig:Tabler:Button variant="default">Clear</twig:Tabler:Button>
    </twig:Tabler:ButtonGroup>
    <twig:Tabler:ButtonGroup aria-label="Bulk actions">
        <twig:Tabler:Button variant="default">Tag</twig:Tabler:Button>
        <twig:Tabler:Button variant="default">Export</twig:Tabler:Button>
        <twig:Tabler:Button variant="danger" appearance="outline">Delete</twig:Tabler:Button>
    </twig:Tabler:ButtonGroup>
</twig:Tabler:ButtonToolbar>
```

## Props

The component has no props. Other attributes go to the root `<div class="btn-toolbar" role="toolbar">`: a `class` is
added to `btn-toolbar`, a `role` replaces `toolbar`.

## Blocks

| Block     | Default                                |
| --------- | -------------------------------------- |
| `content` | Empty: the children, the button groups |
