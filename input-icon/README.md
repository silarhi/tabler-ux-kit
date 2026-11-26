# InputIcon

An icon inside a text field, to hint at what goes in it, or a spinner to show that the field is busy (`.input-icon`).

```twig {"preview":true}
<twig:Tabler:InputIcon icon="search" name="q" placeholder="Search…" label="Search" />
```

## Installation

::: installation

## Position

`position` puts the icon at the `end` of the field (the default) or at its `start`:

```twig {"preview":true}
<div class="d-flex flex-column gap-2">
    <twig:Tabler:InputIcon icon="user" position="start" name="username" placeholder="Username" label="Username" />
    <twig:Tabler:InputIcon icon="calendar" position="end" name="date" placeholder="Date" label="Date" />
</div>
```

## Loader

`loader` shows a small spinner instead of the icon:

```twig {"preview":true}
<div class="d-flex flex-column gap-2">
    <twig:Tabler:InputIcon loader="{{ true }}" placeholder="Loading…" label="Search" />
    <twig:Tabler:InputIcon loader="{{ true }}" position="start" placeholder="Loading…" label="Search" />
</div>
```

## Sizes

`size` sets the size of the input. From Tabler 1.7, the addon follows it; on Tabler 1.6, it keeps the default height.

```twig {"preview":true}
<div class="d-flex flex-column gap-2">
    {% for size in ['lg', 'md', 'sm'] %}
        <twig:Tabler:InputIcon icon="search" position="start" size="{{ size }}" placeholder="Search…" label="Search" />
    {% endfor %}
</div>
```

## Your own input

The tag content replaces only the input, so the icon stays: pass your own field, such as a Symfony form widget
(`{{ form_widget(form.query) }}`):

```twig {"preview":true}
<twig:Tabler:InputIcon icon="search" position="start">
    <input type="search" class="form-control form-control-rounded" name="query" placeholder="Search…" aria-label="Search" autocomplete="off">
</twig:Tabler:InputIcon>
```

## Composed

Without `icon` nor `loader`, place `InputIcon:Addon` yourself: before the input, it sits at the start of the field,
after it, at the end. An addon can hold any content:

```twig {"preview":true}
<twig:Tabler:InputIcon>
    <twig:Tabler:InputIcon:Addon icon="mail" />
    <input type="email" class="form-control" name="email" placeholder="Email" aria-label="Email">
    <twig:Tabler:InputIcon:Addon loader="{{ true }}" />
</twig:Tabler:InputIcon>
```

## Props

| Prop          | Type    | Default  | Description                                                              |
| ------------- | ------- | -------- | ------------------------------------------------------------------------ |
| `icon`        | string? | `null`   | Tabler icon name (or ux-icons name), rendered with `Icon` in the addon   |
| `loader`      | bool    | `false`  | Shows a small spinner in the addon instead of the icon                   |
| `position`    | string  | `'end'`  | `start` or `end`: where the addon goes                                   |
| `type`        | string  | `'text'` | The `type` of the default input                                          |
| `name`        | string? | `null`   | The `name` of the default input                                          |
| `value`       | string? | `null`   | The initial value of the default input                                   |
| `placeholder` | string? | `null`   | The placeholder of the default input                                     |
| `id`          | string? | `null`   | The `id` of the default input, for a `<label for>`                       |
| `label`       | string? | `null`   | The accessible name of the default input (`aria-label`)                  |
| `size`        | string  | `'md'`   | `sm` `md` `lg`, the size of the default input (`form-control-sm`, `-lg`) |

Other attributes go to the root `<div class="input-icon">`.

### InputIcon:Addon

| Prop     | Type    | Default | Description                                                    |
| -------- | ------- | ------- | -------------------------------------------------------------- |
| `icon`   | string? | `null`  | Tabler icon name (or ux-icons name), rendered with `Icon`      |
| `loader` | bool    | `false` | Shows a small [Spinner](https://tabler-ux-components.silarhi.dev/components/feedback/spinner/) instead |

## Sub-components

| Component         | Renders                                                       |
| ----------------- | ------------------------------------------------------------- |
| `InputIcon:Addon` | `<span class="input-icon-addon">`, around the icon or spinner |

## Blocks

| Block     | Default                                                    |
| --------- | ---------------------------------------------------------- |
| `addon`   | `InputIcon:Addon` with `icon` or `loader`, when one is set |
| `content` | An `<input class="form-control">` from the input props     |
