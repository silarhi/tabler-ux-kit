# Step

Shows the progress through a multi-step flow: onboarding, checkout, a setup wizard. Mark the current step `active`.

```twig {"preview":true}
<twig:Tabler:Step>
    <twig:Tabler:Step:Item href="#">Account</twig:Tabler:Step:Item>
    <twig:Tabler:Step:Item href="#">Billing</twig:Tabler:Step:Item>
    <twig:Tabler:Step:Item active>Team</twig:Tabler:Step:Item>
    <twig:Tabler:Step:Item>Done</twig:Tabler:Step:Item>
</twig:Tabler:Step>
```

An item with an `href` renders a link, for the steps the user can go back to; without it, a `<span>`.

## Installation

::: installation

## Counter

`counter` numbers the steps:

```twig {"preview":true}
<twig:Tabler:Step counter>
    <twig:Tabler:Step:Item href="#">Account</twig:Tabler:Step:Item>
    <twig:Tabler:Step:Item active>Billing</twig:Tabler:Step:Item>
    <twig:Tabler:Step:Item>Team</twig:Tabler:Step:Item>
    <twig:Tabler:Step:Item>Done</twig:Tabler:Step:Item>
</twig:Tabler:Step>
```

## Vertical

`vertical` stacks the steps, with room for a description under each one:

```twig {"preview":true}
<twig:Tabler:Step vertical>
    <twig:Tabler:Step:Item>
        <span class="d-block h4 m-0">Order placed</span>
        <span class="d-block text-secondary">October 2, 10:14</span>
    </twig:Tabler:Step:Item>
    <twig:Tabler:Step:Item active>
        <span class="d-block h4 m-0">Shipped</span>
        <span class="d-block text-secondary">October 3, 16:40</span>
    </twig:Tabler:Step:Item>
    <twig:Tabler:Step:Item>
        <span class="d-block h4 m-0">Delivered</span>
    </twig:Tabler:Step:Item>
</twig:Tabler:Step>
```

## Props

`Step`:

| Prop       | Type | Default | Description                        |
| ---------- | ---- | ------- | ---------------------------------- |
| `counter`  | bool | `false` | Numbered steps (`steps-counter`)   |
| `vertical` | bool | `false` | Vertical layout (`steps-vertical`) |

Other attributes go to the root `<div class="steps">`.

`Step:Item`:

| Prop     | Type    | Default | Description                                     |
| -------- | ------- | ------- | ----------------------------------------------- |
| `href`   | string? | `null`  | Link target; without it, the step is a `<span>` |
| `active` | bool    | `false` | The current step (`active`)                     |

Other attributes go to the `<a>` or `<span class="step-item">`.

## Sub-components

| Component   | Renders                                               |
| ----------- | ----------------------------------------------------- |
| `Step:Item` | `<a class="step-item">`, or a `<span>` without `href` |
