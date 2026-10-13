# Modal

Bootstrap 5 modal markup, opened by a trigger with `data-bs-toggle="modal"` and `data-bs-target="#<id>"`. It needs
`tabler.js`.

```twig {"preview":true}
<twig:Tabler:Button variant="danger" data-bs-toggle="modal" data-bs-target="#delete-user">Delete user</twig:Tabler:Button>

<twig:Tabler:Modal id="delete-user" title="Delete Jane Doe?" text="She loses access to the workspace immediately." />
```

## Installation

::: installation

## Composed

The sub-components take over for a form or custom actions. `blur` blurs the page behind the modal (`modal-blur`).
Attributes go to the root `<div class="modal">`: add `fade` for the open animation.

```twig {"preview":true}
<twig:Tabler:Button variant="primary" data-bs-toggle="modal" data-bs-target="#invite-user">Invite user</twig:Tabler:Button>

<twig:Tabler:Modal id="invite-user" blur="{{ true }}" class="fade">
    <twig:Tabler:Modal:Header>
        <twig:Tabler:Modal:Title>Invite a user</twig:Tabler:Modal:Title>
        <twig:Tabler:Modal:Close />
    </twig:Tabler:Modal:Header>
    <twig:Tabler:Modal:Body>
        <label class="form-label" for="invite-email">Email</label>
        <input type="email" id="invite-email" class="form-control" placeholder="jane@example.com">
    </twig:Tabler:Modal:Body>
    <twig:Tabler:Modal:Footer>
        <twig:Tabler:Button variant="default" data-bs-dismiss="modal">Cancel</twig:Tabler:Button>
        <twig:Tabler:Button variant="primary" class="ms-auto">Send invitation</twig:Tabler:Button>
    </twig:Tabler:Modal:Footer>
</twig:Tabler:Modal>
```

## Size, position and status

`size` sets the width of the dialog (`fullscreen` covers the whole viewport), `centered` centers it vertically, and
`status` adds a colored bar at its top:

```twig {"preview":true}
<twig:Tabler:Button variant="danger" data-bs-toggle="modal" data-bs-target="#cancel-subscription">Cancel subscription</twig:Tabler:Button>

<twig:Tabler:Modal id="cancel-subscription" size="sm" centered="{{ true }}" status="danger" title="Cancel subscription?" text="The workspace moves to the free plan at the end of the billing period." footer="You can subscribe again at any time." />
```

The status bar is rendered outside the `content` block, so a composed modal keeps it: set `status` and pass the
sub-components as children:

```twig {"preview":true}
<twig:Tabler:Button variant="success" data-bs-toggle="modal" data-bs-target="#payment-received">Show receipt</twig:Tabler:Button>

<twig:Tabler:Modal id="payment-received" size="sm" centered="{{ true }}" status="success">
    <twig:Tabler:Modal:Body class="text-center py-4">
        <twig:Tabler:Icon name="circle-check" class="text-green mb-2 fs-1" />
        <h3>Payment received</h3>
        <div class="text-secondary">Invoice #1042 is paid: 1,250.00 EUR.</div>
    </twig:Tabler:Modal:Body>
    <twig:Tabler:Modal:Footer>
        <twig:Tabler:Button variant="default" block="{{ true }}" data-bs-dismiss="modal">Close</twig:Tabler:Button>
    </twig:Tabler:Modal:Footer>
</twig:Tabler:Modal>
```

For long content, `scrollable` scrolls the body of the dialog instead of the page.

## Blocks

`title`, `text` and `footer` are plain strings. For richer content, such as buttons in the footer, override the
matching block: `header`, `body` or `footer`. The other blocks keep rendering from their props. See
[Composition](https://tabler-ux-components.silarhi.dev/getting-started/composition/) for how blocks work.

```twig {"preview":true}
<twig:Tabler:Button variant="primary" data-bs-toggle="modal" data-bs-target="#deploy">Deploy</twig:Tabler:Button>

<twig:Tabler:Modal id="deploy" title="Deploy to production?" text="Release v2.4.0 goes live for every customer.">
    <twig:block name="footer">
        <twig:Tabler:Modal:Footer>
            <twig:Tabler:Button variant="default" data-bs-dismiss="modal">Cancel</twig:Tabler:Button>
            <twig:Tabler:Button variant="primary" class="ms-auto" data-bs-dismiss="modal">Deploy</twig:Tabler:Button>
        </twig:Tabler:Modal:Footer>
    </twig:block>
</twig:Tabler:Modal>
```

## Static backdrop

With `staticBackdrop`, neither a click on the backdrop nor the Escape key closes the modal. `dismissible="{{ false }}"`
removes the close button of the header (see [boolean props](https://tabler-ux-components.silarhi.dev/getting-started/composition/#boolean-props)), so the
footer button is the only way out:

```twig {"preview":true}
<twig:Tabler:Button variant="primary" data-bs-toggle="modal" data-bs-target="#accept-terms">Continue</twig:Tabler:Button>

<twig:Tabler:Modal id="accept-terms" staticBackdrop="{{ true }}" dismissible="{{ false }}" title="Updated terms of service" text="Accept the new terms to keep using the workspace.">
    <twig:block name="footer">
        <twig:Tabler:Modal:Footer>
            <twig:Tabler:Button variant="primary" data-bs-dismiss="modal">Accept</twig:Tabler:Button>
        </twig:Tabler:Modal:Footer>
    </twig:block>
</twig:Tabler:Modal>
```

## Props

| Prop             | Type    | Default | Description                                                                       |
| ---------------- | ------- | ------- | --------------------------------------------------------------------------------- |
| `id`             | string? | `null`  | DOM id targeted by triggers (`data-bs-target="#id"`)                              |
| `size`           | string  | `'md'`  | `sm` `md` `lg` `xl` `full` (`modal-full-width`) `fullscreen` (`modal-fullscreen`) |
| `centered`       | bool    | `false` | Vertically centered dialog (`modal-dialog-centered`)                              |
| `scrollable`     | bool    | `false` | Scrolls the body instead of the page (`modal-dialog-scrollable`)                  |
| `status`         | string? | `null`  | Color of the status bar, rendered with `Modal:Status`                             |
| `title`          | string? | `null`  | Rendered with `Modal:Header` and `Modal:Title`                                    |
| `text`           | string? | `null`  | Rendered with `Modal:Body`                                                        |
| `footer`         | string? | `null`  | Rendered with `Modal:Footer`                                                      |
| `dismissible`    | bool    | `true`  | Close button in the header rendered from `title` (`Modal:Close`)                  |
| `staticBackdrop` | bool    | `false` | The backdrop and the Escape key do not close the modal                            |
| `blur`           | bool    | `false` | Blurs the page behind the backdrop (`modal-blur`)                                 |

Other attributes go to the root `<div class="modal" tabindex="-1">`.

## Sub-components

| Component      | Renders                                                                                    |
| -------------- | ------------------------------------------------------------------------------------------ |
| `Modal:Header` | `<div class="modal-header">`: holds the title and the close button                         |
| `Modal:Title`  | `<h5 class="modal-title">`                                                                 |
| `Modal:Close`  | `<button class="btn-close" data-bs-dismiss="modal" aria-label="Close">`                    |
| `Modal:Body`   | `<div class="modal-body">`                                                                 |
| `Modal:Footer` | `<div class="modal-footer">`: usually the actions                                          |
| `Modal:Status` | `<div class="modal-status bg-…">`: the colored bar; `variant` prop, `'primary'` by default |

`Modal:Status` takes `variant`: `primary` `secondary` `success` `danger` `warning` `info` `dark` `light`.

## Blocks

| Block     | Default                                                                                       |
| --------- | --------------------------------------------------------------------------------------------- |
| `header`  | `Modal:Header` with `Modal:Title` and `Modal:Close` (when `dismissible`), when `title` is set |
| `body`    | `Modal:Body` with the `text` prop, when set                                                   |
| `footer`  | `Modal:Footer` with the `footer` prop, when set                                               |
| `content` | `header`, `body` and `footer`: replace it to compose freely; the status bar stays outside it  |
