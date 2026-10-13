# Clipboard

A copy button handled by `tabler.js` (`data-bs-toggle="clipboard"`, Tabler 1.6+). `target` points to the element to
copy: a field gives its value, any other element its text.

```twig {"preview":true}
<div class="input-group">
    <input type="text" id="api-key" class="form-control" value="tblr_live_8f2c41d0a7" readonly>
    <twig:Tabler:Clipboard target="#api-key" />
</div>
```

The browser only exposes the clipboard API on secure contexts (HTTPS or `localhost`): elsewhere, the copy fails and
`tabler.js` fires `error.bs.clipboard`.

## Installation

::: installation

## Literal text

`text` copies a fixed string, and wins over `target`. `label` and `feedback` set the two states, `delay` how long the
copied state lasts in milliseconds (2000 by default, `0` keeps it). The button is a plain `.btn`: add a color or a size
with `class`.

```twig {"preview":true}
<div class="btn-list">
    <twig:Tabler:Clipboard text="composer require silarhi/tabler-ux-components" label="Copy command" feedback="Copied!" class="btn-primary" />
    <twig:Tabler:Clipboard text="https://example.com/invoices/1042" label="Copy link" feedback="Link copied" delay="5000" class="btn-sm" />
</div>
```

## Composed

Use the sub-components for icon states. `tabler.js` hides the `Clipboard:Feedback` until a copy, then swaps it with
the `Clipboard:Label`. Give an icon-only button an `aria-label`:

```twig {"preview":true}
<div class="input-group">
    <input type="text" id="webhook-url" class="form-control" value="https://example.com/hooks/deploy" readonly>
    <twig:Tabler:Clipboard target="#webhook-url" class="btn-icon" aria-label="Copy the webhook URL">
        <twig:Tabler:Clipboard:Label><twig:Tabler:Icon name="copy" class="fs-2 lh-1 d-block" /></twig:Tabler:Clipboard:Label>
        <twig:Tabler:Clipboard:Feedback class="text-green"><twig:Tabler:Icon name="check" class="fs-2 lh-1 d-block" /></twig:Tabler:Clipboard:Feedback>
    </twig:Tabler:Clipboard>
</div>
```

Size webfont icons with utilities (`fs-2 lh-1 d-block`) rather than Tabler's `icon` class: `icon` is made for an icon
placed directly in the button, and the label and feedback wrappers push it off center.

## Blocks

`label` and `feedback` each have a matching block. Override one, and the other keeps rendering from its prop:

```twig {"preview":true}
<twig:Tabler:Clipboard text="INV-2026-1042" label="Copy reference">
    <twig:block name="feedback">
        <twig:Tabler:Clipboard:Feedback class="text-green">
            <twig:Tabler:Icon name="check" class="icon" /> Copied
        </twig:Tabler:Clipboard:Feedback>
    </twig:block>
</twig:Tabler:Clipboard>
```

## Props

| Prop       | Type    | Default    | Description                                                                                 |
| ---------- | ------- | ---------- | ------------------------------------------------------------------------------------------- |
| `target`   | string? | `null`     | Selector of the element to copy (`data-bs-target`)                                          |
| `text`     | string? | `null`     | Literal string to copy, wins over `target` (`data-bs-text`)                                 |
| `delay`    | int?    | `null`     | Duration of the copied state in ms (`data-bs-delay`); Tabler defaults to 2000, `0` keeps it |
| `label`    | string  | `'Copy'`   | Resting text, rendered with `Clipboard:Label`                                               |
| `feedback` | string  | `'Copied'` | Text shown after a copy, rendered with `Clipboard:Feedback`                                 |

Other attributes go to the `<button class="btn">`.

## Sub-components

| Component            | Renders                                                 |
| -------------------- | ------------------------------------------------------- |
| `Clipboard:Label`    | `<span class="clipboard-label">`: the resting state     |
| `Clipboard:Feedback` | `<span class="clipboard-feedback">`: shown after a copy |

## Blocks

| Block      | Default                                              |
| ---------- | ---------------------------------------------------- |
| `label`    | `Clipboard:Label` with the `label` prop              |
| `feedback` | `Clipboard:Feedback` with the `feedback` prop        |
| `content`  | `label` and `feedback`: replace it to compose freely |
