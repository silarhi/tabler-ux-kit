# Toast

A lightweight notification: a background job that finished, a message from a teammate.

```twig {"preview":true}
<twig:Tabler:Toast show>
    <twig:Tabler:Toast:Header>
        <twig:Tabler:Avatar image="/examples/avatar-1.jpg" size="xs" class="me-2" />
        <strong class="me-auto">Jane Doe</strong>
        <small class="text-secondary">2 min ago</small>
        <twig:Tabler:Toast:Close />
    </twig:Tabler:Toast:Header>
    <twig:Tabler:Toast:Body>Deployment #482 is live on production.</twig:Tabler:Toast:Body>
</twig:Tabler:Toast>
```

Toast has no content props: compose it with `Toast:Header`, `Toast:Body` and `Toast:Close`.

## Installation

::: installation

## Body only

Drop the header for a one-line message, and put the close button next to the body:

```twig {"preview":true}
<twig:Tabler:Toast show>
    <div class="d-flex">
        <twig:Tabler:Toast:Body>Invoice INV-0042 sent to the customer.</twig:Tabler:Toast:Body>
        <twig:Tabler:Toast:Close class="me-2 m-auto" />
    </div>
</twig:Tabler:Toast>
```

## Placement

The toast does not position itself. Wrap toasts in a `Toast:Container`: it stacks them, and its `placement` pins the
stack to a corner or the center of the viewport. Without `placement`, the container stays in the flow of its parent:

```twig {"preview":true}
<twig:Tabler:Toast:Container placement="top-end">
    <twig:Tabler:Toast show>
        <twig:Tabler:Toast:Header>
            <strong class="me-auto">Backup</strong>
            <small class="text-secondary">just now</small>
            <twig:Tabler:Toast:Close />
        </twig:Tabler:Toast:Header>
        <twig:Tabler:Toast:Body>The nightly backup finished.</twig:Tabler:Toast:Body>
    </twig:Tabler:Toast>
    <twig:Tabler:Toast show>
        <twig:Tabler:Toast:Header>
            <strong class="me-auto">Users</strong>
            <small class="text-secondary">5 min ago</small>
            <twig:Tabler:Toast:Close />
        </twig:Tabler:Toast:Header>
        <twig:Tabler:Toast:Body>3 users accepted their invitation.</twig:Tabler:Toast:Body>
    </twig:Tabler:Toast>
</twig:Tabler:Toast:Container>
```

## Showing a toast

Without `show`, a toast stays hidden until Bootstrap shows it. With `tabler.js`, a trigger carrying
`data-bs-toggle="toast"` and a `data-bs-target` shows it on click; from your own code, call
`bootstrap.Toast.getOrCreateInstance(element).show()`.

A shown toast hides itself after Bootstrap's delay (5 seconds, set `data-bs-delay` to change it). `autohide` set to
`false` keeps it until it is closed, as here:

```twig {"preview":true}
<twig:Tabler:Button variant="primary" data-bs-toggle="toast" data-bs-target="#deploy-toast">Deploy</twig:Tabler:Button>

<twig:Tabler:Toast:Container placement="bottom-end">
    <twig:Tabler:Toast id="deploy-toast" autohide="{{ false }}">
        <twig:Tabler:Toast:Header>
            <strong class="me-auto">Deployment started</strong>
            <twig:Tabler:Toast:Close />
        </twig:Tabler:Toast:Header>
        <twig:Tabler:Toast:Body>Production will be updated in a few minutes.</twig:Tabler:Toast:Body>
    </twig:Tabler:Toast>
</twig:Tabler:Toast:Container>
```

## Props

| Prop       | Type | Default | Description                                                                 |
| ---------- | ---- | ------- | --------------------------------------------------------------------------- |
| `show`     | bool | `false` | Renders the toast visible (`show`)                                          |
| `autohide` | bool | `true`  | `false` adds `data-bs-autohide="false"`: the toast stays until it is closed |

Other attributes go to the root `<div role="alert">`, such as the `id` a trigger targets.

## Sub-components

| Component         | Renders                                                                                |
| ----------------- | -------------------------------------------------------------------------------------- |
| `Toast:Header`    | `<div class="toast-header">`                                                           |
| `Toast:Body`      | `<div class="toast-body">`                                                             |
| `Toast:Close`     | The close button, `<button class="ms-2 btn-close" data-bs-dismiss="toast">` (needs JS) |
| `Toast:Container` | `<div class="toast-container">`: stacks toasts, see its props below                    |

### `Toast:Container` props

| Prop        | Type    | Default | Description                                                                                    |
| ----------- | ------- | ------- | ---------------------------------------------------------------------------------------------- |
| `placement` | string? | `null`  | `top-start` `top-center` `top-end` `middle-center` `bottom-start` `bottom-center` `bottom-end` |

With a `placement`, the container gets `position-fixed p-3` and the position utilities of that place (for instance
`top-0 end-0`). Other attributes go to the container `<div>`.
