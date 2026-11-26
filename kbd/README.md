# Kbd

A keyboard key rendered as a `<kbd>`, or a shortcut rendered as a `<kbd class="kbd-group">` of keys. Requires Tabler
1.7+.

```twig {"preview":true}
<p>
    Press <twig:Tabler:Kbd>Esc</twig:Tabler:Kbd> to close, or <twig:Tabler:Kbd keys="ctrl+k" /> to search.
</p>
```

The content is a single key. `keys` renders a shortcut instead: one `Kbd:Key` per key, with an even gap between them.

## Installation

::: installation

## Shortcuts

`keys` takes a string split on `+`, or a list. Use a list for a shortcut with the `+` key itself, or for keys you
want to keep as they are:

```twig {"preview":true}
<div class="d-flex flex-wrap gap-3">
    <twig:Tabler:Kbd keys="⌘+K" />
    <twig:Tabler:Kbd keys="ctrl+shift+P" />
    <twig:Tabler:Kbd keys="{{ ['⌘', '⇧', 'M'] }}" />
    <twig:Tabler:Kbd keys="{{ ['ctrl', '+'] }}" />
</div>
```

## In a button

Tabler spaces a key placed directly in a button or a badge, and gives it the color of its text:

```twig {"preview":true}
<div class="d-flex flex-wrap gap-2">
    <button type="button" class="btn">Search <twig:Tabler:Kbd keys="⌘+K" /></button>
    <button type="button" class="btn btn-primary">Save <twig:Tabler:Kbd keys="⌘+S" /></button>
</div>
```

## Composed

`Kbd:Group` holds the keys of a shortcut and `Kbd:Key` renders one of them. A key can hold an icon, which Tabler
sizes to the key:

```twig {"preview":true}
<twig:Tabler:Kbd:Group>
    <twig:Tabler:Kbd:Key>Shift</twig:Tabler:Kbd:Key>
    <twig:Tabler:Kbd:Key><twig:Tabler:Icon name="arrow-up" /></twig:Tabler:Kbd:Key>
</twig:Tabler:Kbd:Group>
```

## Custom keys

Override the `keys` block to render the keys yourself, for example with a `title` on each:

```twig {"preview":true}
<twig:Tabler:Kbd keys="ctrl+c">
    <twig:block name="keys">
        <twig:Tabler:Kbd:Key title="Control">⌃</twig:Tabler:Kbd:Key>
        <twig:Tabler:Kbd:Key>C</twig:Tabler:Kbd:Key>
    </twig:block>
</twig:Tabler:Kbd>
```

## Props

| Prop   | Type          | Default | Description                                                                         |
| ------ | ------------- | ------- | ----------------------------------------------------------------------------------- |
| `keys` | string\|list? | `null`  | The keys of a shortcut: a string split on `+` (`'ctrl+k'`) or a list (`['⌘', 'K']`) |

Other attributes go to the root `<kbd>`.

## Sub-components

| Component   | Renders                                            |
| ----------- | -------------------------------------------------- |
| `Kbd:Group` | `<kbd class="kbd-group">`, around the keys         |
| `Kbd:Key`   | `<kbd>`, one key of a shortcut: a label or an icon |

## Blocks

| Block     | Default                                                            |
| --------- | ------------------------------------------------------------------ |
| `keys`    | A `Kbd:Key` per key of `keys`, when set                            |
| `content` | `keys`; the tag content replaces it, as a single key or to compose |
