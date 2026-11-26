# Mockup browser

A frame that looks like a browser window, with the window dots and an address bar, around a page preview or a
screenshot. Requires Tabler 1.7+.

```twig {"preview":true}
<twig:Tabler:MockupBrowser url="example.com/offices" src="/examples/photo-1.jpg" alt="The offices page: an open-plan office with desks" />
```

`url` is the address in the toolbar, `src` and `alt` the screenshot, which fills the width of the frame.

## Installation

::: installation

## Sizes and address

`icon` goes before the address, such as `lock` for a secure page. `size="sm"` gives a 24px toolbar with smaller dots
and text, for thumbnails and cards. Without `url`, the frame only has the window dots:

```twig {"preview":true}
<div class="row g-3 align-items-start">
    <div class="col-md-7">
        <twig:Tabler:MockupBrowser icon="lock" url="https://example.com" src="/examples/photo-2.jpg" alt="A meeting room" />
    </div>
    <div class="col-md-5">
        <twig:Tabler:MockupBrowser size="sm" icon="lock" url="https://example.com" src="/examples/photo-2.jpg" alt="A meeting room" />
    </div>
    <div class="col-md-5">
        <twig:Tabler:MockupBrowser size="sm" src="/examples/photo-3.jpg" alt="A lounge with sofas" />
    </div>
</div>
```

## Any content

The body takes any markup, not only an image. Override the `body` block to keep the toolbar of the props, and add a
padding utility to the `MockupBrowser:Body`:

```twig {"preview":true}
<twig:Tabler:MockupBrowser icon="lock" url="example.com/signup">
    <twig:block name="body">
        <twig:Tabler:MockupBrowser:Body class="p-4">
            <h3 class="card-title">Create an account</h3>
            <div class="mb-3">
                <label class="form-label" for="mockup-browser-email">Email</label>
                <input type="email" class="form-control" id="mockup-browser-email" placeholder="you@example.com">
            </div>
            <twig:Tabler:Button variant="primary" class="w-100">Sign up</twig:Tabler:Button>
        </twig:Tabler:MockupBrowser:Body>
    </twig:block>
</twig:Tabler:MockupBrowser>
```

## Composed

Children replace the toolbar and the body: `MockupBrowser:Toolbar` with `MockupBrowser:Controls` and
`MockupBrowser:Url`, then `MockupBrowser:Body`. The `--tblr-mockup-browser-*` variables, in a `style` attribute, change
the colors, the shadow or the size of the dots:

```twig {"preview":true}
<twig:Tabler:MockupBrowser style="--tblr-mockup-browser-toolbar-bg: var(--tblr-gray-900); --tblr-mockup-browser-toolbar-color: var(--tblr-gray-400); --tblr-mockup-browser-border-color: var(--tblr-gray-900)">
    <twig:Tabler:MockupBrowser:Toolbar>
        <twig:Tabler:MockupBrowser:Controls />
        <twig:Tabler:MockupBrowser:Url icon="lock">https://example.com/lounge</twig:Tabler:MockupBrowser:Url>
    </twig:Tabler:MockupBrowser:Toolbar>
    <twig:Tabler:MockupBrowser:Body src="/examples/photo-3.jpg" alt="The lounge page: sofas by the windows" />
</twig:Tabler:MockupBrowser>
```

## Accessibility

The window dots are an empty element, which screen readers skip. The address is plain text, not a link nor a field.
Give a screenshot an `alt` saying what page it shows.

## Props

| Prop   | Type    | Default | Description                                                         |
| ------ | ------- | ------- | ------------------------------------------------------------------- |
| `url`  | string? | `null`  | Address in the toolbar; unset, only the window dots                 |
| `icon` | string? | `null`  | Icon before the address, e.g. `lock`                                |
| `src`  | string? | `null`  | Screenshot URL, rendered with `MockupBrowser:Body`                  |
| `alt`  | string  | `''`    | Alternative text of the screenshot                                  |
| `size` | string? | `null`  | `sm`: a 24px toolbar for thumbnails and cards (`mockup-browser-sm`) |

Other attributes go to the root `<div class="mockup-browser">`.

`MockupBrowser:Toolbar` takes `url` and `icon`, `MockupBrowser:Url` takes `icon` (its content is the address), and
`MockupBrowser:Body` takes `src` and `alt`. Other attributes go to their root element.

## Sub-components

| Component                | Renders                                                                   |
| ------------------------ | ------------------------------------------------------------------------- |
| `MockupBrowser:Toolbar`  | `<div class="mockup-browser-toolbar">`: the dots and the address          |
| `MockupBrowser:Controls` | `<span class="mockup-browser-controls">`: the three window dots           |
| `MockupBrowser:Url`      | `<div class="mockup-browser-url">`: an icon and the address in a `<span>` |
| `MockupBrowser:Body`     | `<div class="mockup-browser-body">`: the page                             |

## Blocks

| Block     | Default                                                                |
| --------- | ---------------------------------------------------------------------- |
| `toolbar` | `MockupBrowser:Toolbar` with the `url` and `icon` props                |
| `body`    | `MockupBrowser:Body` with the `src` and `alt` props, when `src` is set |
| `content` | `toolbar` and `body`: replace it to compose freely                     |

`MockupBrowser:Toolbar` has the `controls` and `url` blocks, `MockupBrowser:Url` an `icon` block, and
`MockupBrowser:Body` a `content` block holding the `<img>` of its props.
