# Toast

A lightweight notification: a background job that finished, a message from a teammate.

```twig {"preview":true}
<twig:Tabler:Toast show>
    <twig:Tabler:Toast:Header>
        <twig:Tabler:Avatar image="/examples/avatar-1.jpg" size="xs" class="me-2" />
        <twig:Tabler:Toast:Title>Jane Doe</twig:Tabler:Toast:Title>
        <twig:Tabler:Toast:Time>2 min ago</twig:Tabler:Toast:Time>
        <twig:Tabler:Toast:Close />
    </twig:Tabler:Toast:Header>
    <twig:Tabler:Toast:Body>Deployment #482 is live on production.</twig:Tabler:Toast:Body>
</twig:Tabler:Toast>
```

`title`, `time` and `text` render the header and the body, with a close button unless `dismissible` is `false`, as in
the [placement](#placement) examples. For anything richer, such as an avatar before the title, compose it with
`Toast:Header`, `Toast:Body` and `Toast:Close`, as above. `Toast:Header` takes the same `title`, `time` and
`dismissible`.

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
    <twig:Tabler:Toast show title="Backup" time="just now" text="The nightly backup finished." />
    <twig:Tabler:Toast show title="Users" time="5 min ago" text="3 users accepted their invitation." />
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
    <twig:Tabler:Toast id="deploy-toast" autohide="{{ false }}" title="Deployment started" text="Production will be updated in a few minutes." />
</twig:Tabler:Toast:Container>
```

## Urgency

A toast is a polite status message (`role="status"`, `aria-live="polite"`): screen readers announce it once they are
idle, as Tabler does since 1.7.1. `urgent` makes it an alert (`role="alert"`, `aria-live="assertive"`), announced at
once, interrupting the user: keep it for errors that matter.

```twig {"preview":true}
<twig:Tabler:Toast show urgent autohide="{{ false }}" title="Payment failed" text="The card was declined: update the payment method to keep your plan." />
```

## Props

| Prop          | Type    | Default | Description                                                                 |
| ------------- | ------- | ------- | --------------------------------------------------------------------------- |
| `show`        | bool    | `false` | Renders the toast visible (`show`)                                          |
| `autohide`    | bool    | `true`  | `false` adds `data-bs-autohide="false"`: the toast stays until it is closed |
| `title`       | string? | `null`  | Rendered with `Toast:Header` and `Toast:Title`                              |
| `time`        | string? | `null`  | Timestamp next to the title, rendered with `Toast:Time`                     |
| `text`        | string? | `null`  | Rendered with `Toast:Body`                                                  |
| `dismissible` | bool    | `true`  | Close button in the header rendered from `title` (`Toast:Close`)            |
| `urgent`      | bool    | `false` | `role="alert"` and `aria-live="assertive"` instead of `status` and `polite` |

Other attributes go to the root `<div class="toast">`, such as the `id` a trigger targets.

## Sub-components

| Component         | Renders                                                                                   |
| ----------------- | ----------------------------------------------------------------------------------------- |
| `Toast:Header`    | `<div class="toast-header">`: the title, a time and the close button, see its props below |
| `Toast:Title`     | `<strong class="me-auto">`: the title, pushing the time and the close button to the end   |
| `Toast:Time`      | `<small class="text-secondary">`: a timestamp, such as `2 min ago`                        |
| `Toast:Body`      | `<div class="toast-body">`                                                                |
| `Toast:Close`     | The close button, `<button class="ms-2 btn-close" data-bs-dismiss="toast">` (needs JS)    |
| `Toast:Container` | `<div class="toast-container">`: stacks toasts, see its props below                       |

### `Toast:Header` props

| Prop          | Type    | Default | Description                         |
| ------------- | ------- | ------- | ----------------------------------- |
| `title`       | string? | `null`  | Rendered with `Toast:Title`         |
| `time`        | string? | `null`  | Rendered with `Toast:Time`          |
| `dismissible` | bool    | `true`  | Adds a close button (`Toast:Close`) |

### `Toast:Container` props

| Prop        | Type    | Default | Description                                                                                    |
| ----------- | ------- | ------- | ---------------------------------------------------------------------------------------------- |
| `placement` | string? | `null`  | `top-start` `top-center` `top-end` `middle-center` `bottom-start` `bottom-center` `bottom-end` |

With a `placement`, the container gets `position-fixed p-3` and the position utilities of that place (for instance
`top-0 end-0`). Other attributes go to the container `<div>`.

## Blocks

| Block     | Default                                                                              |
| --------- | ------------------------------------------------------------------------------------ |
| `header`  | `Toast:Header` with the `title`, `time` and `dismissible` props, when `title` is set |
| `body`    | `Toast:Body` with the `text` prop, when set                                          |
| `content` | `header` and `body`: replace it to compose freely                                    |

`Toast:Header`:

| Block     | Default                                              |
| --------- | ---------------------------------------------------- |
| `title`   | `Toast:Title` with the `title` prop, when set        |
| `time`    | `Toast:Time` with the `time` prop, when set          |
| `close`   | `Toast:Close`, when `dismissible`                    |
| `content` | `title`, `time` and `close`: its children replace it |
