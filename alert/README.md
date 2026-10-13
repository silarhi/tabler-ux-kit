# Alert

Contextual feedback messages: the result of an action, a warning, an error.

```twig {"preview":true}
<twig:Tabler:Alert variant="success" icon="check" title="Saved!" description="Your changes are live." />
```

`icon` takes a [Tabler icon](https://tabler-ux-components.silarhi.dev/components/content/icon/) name. For any other icon (inline SVG, ux-icons), override the
`icon` block with `Alert:Icon`:

```twig {"preview":true}
<twig:Tabler:Alert variant="warning" title="Storage almost full" description="You have used 92% of your 50 GB plan.">
    <twig:block name="icon">
        <twig:Tabler:Alert:Icon>
            <svg xmlns="http://www.w3.org/2000/svg" class="icon" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true">
                <path d="M12 9v4" />
                <path d="M10.363 3.591l-8.106 13.534a1.914 1.914 0 0 0 1.636 2.871h16.214a1.914 1.914 0 0 0 1.636 -2.87l-8.106 -13.536a1.914 1.914 0 0 0 -3.274 0z" />
                <path d="M12 16h.01" />
            </svg>
        </twig:Tabler:Alert:Icon>
    </twig:block>
</twig:Tabler:Alert>
```

## Installation

::: installation

## Composed

Bring your own icon, or rich content, with the sub-components. Wrap the title and the description in a `<div>` so
they stack next to the icon, as the all-in-one version does:

```twig {"preview":true}
<twig:Tabler:Alert variant="success">
    <twig:Tabler:Alert:Icon><twig:Tabler:Icon name="check" /></twig:Tabler:Alert:Icon>
    <div>
        <twig:Tabler:Alert:Title>Saved!</twig:Tabler:Alert:Title>
        <twig:Tabler:Alert:Description>
            Your changes are <strong>live</strong>.
        </twig:Tabler:Alert:Description>
    </div>
</twig:Tabler:Alert>
```

## Links, actions and lists

`Alert:Link` is a link inside the message, in the alert color. `Alert:Action` is the next step to take, on its own
line. `Alert:List` lists several messages, such as validation errors:

```twig {"preview":true}
<twig:Tabler:Alert variant="info">
    <twig:Tabler:Alert:Icon><twig:Tabler:Icon name="info-circle" /></twig:Tabler:Alert:Icon>
    <div>
        <twig:Tabler:Alert:Title>Your trial ends in 3 days</twig:Tabler:Alert:Title>
        <twig:Tabler:Alert:Description>
            Your projects stay available until then. <twig:Tabler:Alert:Link href="/billing/plans">Compare plans</twig:Tabler:Alert:Link>
        </twig:Tabler:Alert:Description>
        <twig:Tabler:Alert:Action href="/billing">Upgrade now</twig:Tabler:Alert:Action>
    </div>
</twig:Tabler:Alert>
<twig:Tabler:Alert variant="danger">
    <twig:Tabler:Alert:Icon><twig:Tabler:Icon name="alert-circle" /></twig:Tabler:Alert:Icon>
    <div>
        <twig:Tabler:Alert:Title>The invoice could not be saved</twig:Tabler:Alert:Title>
        <twig:Tabler:Alert:List>
            <li>The customer is missing.</li>
            <li>The due date is before the issue date.</li>
        </twig:Tabler:Alert:List>
    </div>
</twig:Tabler:Alert>
```

## Variants

```twig {"preview":true}
{% for variant in ['primary', 'secondary', 'success', 'danger', 'warning', 'info'] %}
    <twig:Tabler:Alert variant="{{ variant }}" title="{{ variant|capitalize }}" description="A {{ variant }} alert." />
{% endfor %}
```

## Styles

`important` fills the background, `minor` keeps a plain border, `dismissible` adds a close button (it needs
`tabler.js`).

```twig {"preview":true}
<twig:Tabler:Alert variant="danger" important="{{ true }}" title="Important" description="A filled background." />
<twig:Tabler:Alert variant="danger" minor="{{ true }}" title="Minor" description="A plain border, no tinted background." />
<twig:Tabler:Alert variant="danger" dismissible="{{ true }}" title="Dismissible" description="With a close button." />
```

## Blocks

Each prop has a matching block. Override one, and the others keep rendering from their props:

```twig {"preview":true}
<twig:Tabler:Alert variant="info" title="Heads up" description="The title block is overridden, the description is not.">
    <twig:block name="title">
        <twig:Tabler:Alert:Title class="text-uppercase">Heads up</twig:Tabler:Alert:Title>
    </twig:block>
</twig:Tabler:Alert>
```

## Props

| Prop          | Type    | Default  | Description                                                       |
| ------------- | ------- | -------- | ----------------------------------------------------------------- |
| `variant`     | string  | `'info'` | `primary` `secondary` `success` `danger` `warning` `info`         |
| `important`   | bool    | `false`  | Filled background (`alert-important`)                             |
| `minor`       | bool    | `false`  | Plain border, no tinted background (`alert-minor`)                |
| `icon`        | string? | `null`   | Tabler icon name, rendered with `Tabler:Icon` inside `Alert:Icon` |
| `title`       | string? | `null`   | Rendered with `Alert:Title`                                       |
| `description` | string? | `null`   | Rendered with `Alert:Description`                                 |
| `dismissible` | bool    | `false`  | Adds a close button (`Alert:Dismiss`)                             |

Other attributes go to the root `<div role="alert">`.

## Sub-components

| Component           | Renders                                                                       |
| ------------------- | ----------------------------------------------------------------------------- |
| `Alert:Icon`        | `<div class="alert-icon">`: put any icon inside (Tabler Icons, SVG, ux-icons) |
| `Alert:Title`       | `<h4 class="alert-heading">`                                                  |
| `Alert:Description` | `<div class="alert-description">`                                             |
| `Alert:Link`        | `<a class="alert-link">`: a link in the alert color; `href` defaults to `#`   |
| `Alert:Action`      | `<a class="alert-action">`: a link on its own line; `href` defaults to `#`    |
| `Alert:List`        | `<ul class="alert-list">`: without the default list margin                    |
| `Alert:Dismiss`     | The close button, `<button class="btn-close" data-bs-dismiss="alert">`        |

## Blocks

| Block         | Default                                                              |
| ------------- | -------------------------------------------------------------------- |
| `icon`        | `Alert:Icon` with a `Tabler:Icon` named `icon`, when set             |
| `title`       | `Alert:Title` with the `title` prop, when set                        |
| `description` | `Alert:Description` with the `description` prop, when set            |
| `body`        | A `<div>` around `title` and `description`, when one of them renders |
| `dismiss`     | `Alert:Dismiss`, when `dismissible`                                  |
| `content`     | `icon`, `body` and `dismiss`: replace it to compose freely           |
