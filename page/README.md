# Page

The layout of an app page: a `.page` holding the navigation, then a `.page-wrapper` with the page header, the body
and the footer. Direct children go into the body container; the `title` and `pretitle` props render a
[`PageHeader`](../page-header/) above it, and the `navbar` and `footer` blocks take a [`Navbar`](../navbar/) and a
[`Footer`](../footer/).

```twig {"preview":true}
<twig:Tabler:Page pretitle="Overview" title="Dashboard">
    <twig:block name="navbar">
        <twig:Tabler:Navbar expand="sm">
            <twig:Tabler:Navbar:Toggler target="navbar-menu" />
            <twig:Tabler:Navbar:Brand href="/">Acme Admin</twig:Tabler:Navbar:Brand>
            <twig:Tabler:Navbar:Nav id="navbar-menu" collapse>
                <twig:Tabler:Navbar:Item href="/" icon="home" active>Dashboard</twig:Tabler:Navbar:Item>
                <twig:Tabler:Navbar:Item href="/invoices" icon="file-invoice">Invoices</twig:Tabler:Navbar:Item>
            </twig:Tabler:Navbar:Nav>
        </twig:Tabler:Navbar>
    </twig:block>
    <div class="row row-cards">
        <div class="col-sm-6"><twig:Tabler:Card title="Revenue" text="$4,300 this month." /></div>
        <div class="col-sm-6"><twig:Tabler:Card title="New customers" text="38 this month." /></div>
    </div>
    <twig:block name="footer">
        <twig:Tabler:Footer transparent copyright="Copyright © 2026 Acme" endLinks="{{ [{label: 'Documentation', href: '/docs'}] }}" />
    </twig:block>
</twig:Tabler:Page>
```

## Installation

::: installation

## Admin layout with a sidebar

Put a `vertical` navbar in the `navbar` block: Tabler fixes it to the start edge from its `expand` breakpoint and
offsets the page wrapper by its width.

```twig {"preview":true}
<twig:Tabler:Page pretitle="Overview" title="Dashboard">
    <twig:block name="navbar">
        <twig:Tabler:Navbar vertical expand="sm">
            <twig:Tabler:Navbar:Toggler target="sidebar-menu" />
            <twig:Tabler:Navbar:Brand href="/">Acme Admin</twig:Tabler:Navbar:Brand>
            <twig:Tabler:Navbar:Nav id="sidebar-menu" collapse>
                <twig:Tabler:Navbar:SectionTitle>Overview</twig:Tabler:Navbar:SectionTitle>
                <twig:Tabler:Navbar:Item href="/" icon="home" active>Dashboard</twig:Tabler:Navbar:Item>
                <twig:Tabler:Navbar:Item href="/invoices" icon="file-invoice">Invoices</twig:Tabler:Navbar:Item>
                <twig:Tabler:Navbar:Item href="/customers" icon="users">Customers</twig:Tabler:Navbar:Item>
            </twig:Tabler:Navbar:Nav>
            <twig:Tabler:Navbar:Footer>
                <twig:Tabler:Navbar:Item href="/me" icon="user">Jane Doe</twig:Tabler:Navbar:Item>
            </twig:Tabler:Navbar:Footer>
        </twig:Tabler:Navbar>
    </twig:block>
    <div class="row row-cards">
        <div class="col-md-6"><twig:Tabler:Card title="Revenue" text="$4,300 this month." /></div>
        <div class="col-md-6"><twig:Tabler:Card title="New customers" text="38 this month." /></div>
    </div>
    <twig:block name="footer">
        <twig:Tabler:Footer transparent copyright="Copyright © 2026 Acme" endLinks="{{ [{label: 'Documentation', href: '/docs'}] }}" />
    </twig:block>
</twig:Tabler:Page>
```

## Header actions

The `actions` block is forwarded to the `actions` block of the `PageHeader`: put a `PageHeader:Actions` in it. The
header is rendered when `title`, `pretitle` or `actions` is set.

```twig {"preview":true}
<twig:Tabler:Page pretitle="Billing" title="Invoices">
    <twig:block name="actions">
        <twig:Tabler:PageHeader:Actions>
            <twig:Tabler:Button variant="primary"><twig:Tabler:Icon name="plus" class="icon" /> New invoice</twig:Tabler:Button>
        </twig:Tabler:PageHeader:Actions>
    </twig:block>
    <twig:Tabler:Card text="No invoice yet." />
</twig:Tabler:Page>
```

## Container

`container` sets the `container-*` of the header and the body: `xl` by default, `sm`, `md`, `lg`, `xxl`, `fluid`, or
Tabler's narrower `narrow`, `tight` and `slim`. `fluid` adds `layout-fluid` to the page, which turns every container of
the page full-width, those of the navbar and the footer included.

```twig
<twig:Tabler:Page title="Reports" fluid>…</twig:Tabler:Page>
```

## Composed

Direct children fill the `content` block, inside the body: to build the wrapper yourself, replace the `wrapper` block
with a `Page:Wrapper`. There is no `Page:Header`: wrap a `PageHeader` in a container. Here the whole page is fluid.

```twig {"preview":true}
<twig:Tabler:Page>
    <twig:block name="wrapper">
        <twig:Tabler:Page:Wrapper>
            <div class="container-fluid">
                <twig:Tabler:PageHeader pretitle="Reports" title="Sales" />
            </div>
            <twig:Tabler:Page:Body container="fluid">
                <twig:Tabler:Card title="This quarter" text="$12,800 in 214 orders." />
            </twig:Tabler:Page:Body>
            <twig:Tabler:Footer container="fluid" copyright="Copyright © 2026 Acme" />
        </twig:Tabler:Page:Wrapper>
    </twig:block>
</twig:Tabler:Page>
```

The `header`, `body` and `footer` blocks can also be replaced one by one, for instance the `body` block with a
`Page:Body` of another container, or two of them.

## Centered page

`center` adds `page-center`, which centers the children of the page vertically, such as the card of a sign-in page.
The wrapper fills the page, so replace the `wrapper` block with the centered content.

```twig {"preview":true}
<twig:Tabler:Page center style="min-height: 20rem">
    <twig:block name="wrapper">
        <div class="container container-tight py-4">
            <twig:Tabler:Card title="Sign in" text="Welcome back to Acme." />
        </div>
    </twig:block>
</twig:Tabler:Page>
```

## Layout options on `<body>` and `<html>`

Some of Tabler's layout options are set on `<body>` or `<html>`, which a component cannot reach: set them in the base
template of your app. The `data-bs-*` attributes on `<html>` are also what Tabler's theme settings script
(`tabler-theme.js`) writes, from a choice stored in `localStorage`.

| Option              | Where                                                                              | Effect                                                                   |
| ------------------- | ---------------------------------------------------------------------------------- | ------------------------------------------------------------------------ |
| Boxed               | `<body class="layout-boxed">` or `<html data-bs-layout="boxed">`                   | Centers the page in a frame, which a vertical navbar stays inside        |
| Fluid               | The `fluid` prop, `<body class="layout-fluid">` or `<html data-bs-layout="fluid">` | Full-width containers                                                    |
| Navigation position | `<html data-bs-navbar-position="vertical">` or `"combined"`                        | Which navbar shows when the page renders both: see below                 |
| Sticky navbar       | `<html data-bs-navbar="sticky">`                                                   | Keeps the horizontal navbar at the top; or wrap it in a `.sticky-top`    |
| Floating navigation | `<html data-bs-navbar-style="floating">`                                           | Same as the `floating` prop of `Navbar`, on whichever navbar shows       |
| Navigation theme    | `<html data-bs-navbar-theme="dark">` or `"primary"`                                | Colors whichever navbar shows; or `data-bs-theme="dark"` on the `Navbar` |
| Folded sidebar      | `<html data-bs-sidebar="folded">` or `"folded-hover"`                              | Same as the `folded` prop of `Navbar`, on every vertical navbar          |
| Right to left       | `<html dir="rtl">` and the `tabler.rtl.css` stylesheet                             | Mirrors the layout                                                       |

Tabler also styles a skip link, for the start of the `<body>`, past the navigation to the page body. To give the body
the `id` it points at, replace the `body` block with a `Page:Body`, and render the children in it with
`outerBlocks`:

```twig
{# in <body>: <a href="#content" class="visually-hidden-focusable skip-link">Skip to main content</a> #}
<twig:Tabler:Page title="Dashboard">
    <twig:block name="body">
        <twig:Tabler:Page:Body id="content">{{ block(outerBlocks.content) }}</twig:Tabler:Page:Body>
    </twig:block>
    …
</twig:Tabler:Page>
```

### Vertical and horizontal navbars together

A page can render both navbars, the vertical one first. Since Tabler 1.5, the vertical one is then hidden unless
`<html>` has `data-bs-navbar-position="vertical"`, which hides the horizontal one instead, or `"combined"`, which keeps
both on screen:

```twig
{# <html data-bs-navbar-position="combined"> #}
<twig:Tabler:Page title="Dashboard">
    <twig:block name="navbar">
        <twig:Tabler:Navbar vertical expand="lg">…</twig:Tabler:Navbar>
        <twig:Tabler:Navbar>…</twig:Tabler:Navbar>
    </twig:block>
    …
</twig:Tabler:Page>
```

### Overlapping navbar

For the `navbar-overlap` layout, where the navbar background runs behind the page header, add the class to a dark
horizontal navbar: `<twig:Tabler:Navbar class="navbar-overlap" data-bs-theme="dark">`, and `text-white` to the page
header, through the `header` block.

## Props

| Prop        | Type    | Default | Description                                                                      |
| ----------- | ------- | ------- | -------------------------------------------------------------------------------- |
| `title`     | string? | `null`  | Page title, rendered with `PageHeader`                                           |
| `pretitle`  | string? | `null`  | Small overline above the title, rendered with `PageHeader`                       |
| `container` | string  | `'xl'`  | Suffix of the `container-*` of the header and the body                           |
| `fluid`     | bool    | `false` | Full-width containers in the whole page (`layout-fluid`)                         |
| `center`    | bool    | `false` | Centers the children of the page vertically (`page-center`), e.g. a sign-in card |

Other attributes go to the root `<div class="page">`.

## Sub-components

| Component      | Renders                                                          |
| -------------- | ---------------------------------------------------------------- |
| `Page:Wrapper` | `<div class="page-wrapper">`                                     |
| `Page:Body`    | `<main class="page-body">` around a `<div class="container-xl">` |

### `Page:Body` props

| Prop        | Type   | Default  | Description                                                                   |
| ----------- | ------ | -------- | ----------------------------------------------------------------------------- |
| `container` | string | `'xl'`   | Suffix of the inner `container-*`                                             |
| `tag`       | string | `'main'` | `main`, the main landmark of the page, or `div` when the page already has one |

Other attributes go to the `<main>`, such as `class="page-body-card"` for a body on a surface background.

## Blocks

| Block     | Default                                                                                       |
| --------- | --------------------------------------------------------------------------------------------- |
| `navbar`  | Nothing: put a `Navbar` in it, or a vertical one then a horizontal one                        |
| `wrapper` | The `.page-wrapper` with `header`, `body` and `footer`                                        |
| `header`  | A `PageHeader` with `pretitle`, `title` and `actions` in a container, when one of them is set |
| `actions` | Nothing: put a `PageHeader:Actions` in it                                                     |
| `body`    | A `<main class="page-body">` and its container around `content`                               |
| `content` | The direct children, inside the body container                                                |
| `footer`  | Nothing: put a `Footer` in it                                                                 |
