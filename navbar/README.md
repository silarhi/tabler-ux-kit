# Navbar

The main navigation of an app: a header across the top of the page, or a vertical sidebar.

```twig {"preview":true}
<twig:Tabler:Navbar expand="sm">
    <twig:Tabler:Navbar:Toggler target="navbar-menu" />
    <twig:Tabler:Navbar:Brand href="/">Acme Admin</twig:Tabler:Navbar:Brand>
    <twig:Tabler:Navbar:Nav id="navbar-menu" collapse>
        <twig:Tabler:Navbar:Item href="/" icon="home" active>Dashboard</twig:Tabler:Navbar:Item>
        <twig:Tabler:Navbar:Item href="/users" icon="users">Users</twig:Tabler:Navbar:Item>
        <twig:Tabler:Navbar:Item href="/invoices" icon="file-invoice">Invoices</twig:Tabler:Navbar:Item>
    </twig:Tabler:Navbar:Nav>
</twig:Tabler:Navbar>
```

`Navbar:Toggler` opens the `Navbar:Nav` whose `id` it targets, below the `expand` breakpoint. The examples on this page
use `expand="sm"`, so the menu is expanded in the narrow preview; the default is `md`. Tabler hides the item icons of
a horizontal navbar between the `expand` breakpoint and the next one, where space is tight.

## Installation

::: installation

## Collapsed menu

Below the `expand` breakpoint, the nav collapses behind the toggler (it needs `tabler.js`). With `expand="xl"`, it is
collapsed here: click the toggler.

```twig {"preview":true}
<twig:Tabler:Navbar expand="xl">
    <twig:Tabler:Navbar:Toggler target="navbar-collapsed-menu" />
    <twig:Tabler:Navbar:Brand href="/">Acme Admin</twig:Tabler:Navbar:Brand>
    <twig:Tabler:Navbar:Nav id="navbar-collapsed-menu" collapse>
        <twig:Tabler:Navbar:Item href="/" icon="home" active>Dashboard</twig:Tabler:Navbar:Item>
        <twig:Tabler:Navbar:Item href="/users" icon="users">Users</twig:Tabler:Navbar:Item>
        <twig:Tabler:Navbar:Item href="/invoices" icon="file-invoice">Invoices</twig:Tabler:Navbar:Item>
    </twig:Tabler:Navbar:Nav>
</twig:Tabler:Navbar>
```

## Side group

Put a `Navbar:Side` in the `side` block of `Navbar:Nav` for a trailing group: it renders after the list, inside the
collapse panel. Tabler 1.6.1 does not align it in a horizontal navbar, where it follows the list directly: add
`class="ms-auto"`, as here, to push it to the end side.

```twig {"preview":true}
<twig:Tabler:Navbar expand="sm">
    <twig:Tabler:Navbar:Toggler target="navbar-side-menu" />
    <twig:Tabler:Navbar:Brand href="/">Acme Admin</twig:Tabler:Navbar:Brand>
    <twig:Tabler:Navbar:Nav id="navbar-side-menu" collapse>
        <twig:Tabler:Navbar:Item href="/" icon="home" active>Dashboard</twig:Tabler:Navbar:Item>
        <twig:Tabler:Navbar:Item href="/users" icon="users">Users</twig:Tabler:Navbar:Item>
        <twig:block name="side">
            <twig:Tabler:Navbar:Side class="ms-auto">
                <twig:Tabler:Navbar:Item href="/help" icon="help">Help</twig:Tabler:Navbar:Item>
                <twig:Tabler:Navbar:Item href="/settings" icon="settings">Settings</twig:Tabler:Navbar:Item>
            </twig:Tabler:Navbar:Side>
        </twig:block>
    </twig:Tabler:Navbar:Nav>
</twig:Tabler:Navbar>
```

## Dark

`dark` adds `navbar-dark`, which only switches the text colors to light ones: give the navbar a dark background too,
with a `bg-*` class as here. `data-bs-theme="dark"` on the navbar switches both.

```twig {"preview":true}
<twig:Tabler:Navbar expand="sm" dark class="bg-dark">
    <twig:Tabler:Navbar:Brand href="/">Acme Admin</twig:Tabler:Navbar:Brand>
    <twig:Tabler:Navbar:Nav>
        <twig:Tabler:Navbar:Item href="/" icon="home" active>Dashboard</twig:Tabler:Navbar:Item>
        <twig:Tabler:Navbar:Item href="/users" icon="users">Users</twig:Tabler:Navbar:Item>
    </twig:Tabler:Navbar:Nav>
</twig:Tabler:Navbar>
```

## Floating

`floating` detaches the navbar from the edges around it, with a margin and rounded corners:

```twig {"preview":true}
<twig:Tabler:Navbar expand="sm" floating>
    <twig:Tabler:Navbar:Brand href="/">Acme Admin</twig:Tabler:Navbar:Brand>
    <twig:Tabler:Navbar:Nav>
        <twig:Tabler:Navbar:Item href="/" icon="home" active>Dashboard</twig:Tabler:Navbar:Item>
        <twig:Tabler:Navbar:Item href="/users" icon="users">Users</twig:Tabler:Navbar:Item>
    </twig:Tabler:Navbar:Nav>
</twig:Tabler:Navbar>
```

## Vertical sidebar

`vertical` renders an `<aside>`, fixed to the start edge of the page from the `expand` breakpoint, with a fluid
container. `Navbar:SectionTitle` labels a group of items, `Navbar:Side` pins its items to the bottom of the scrolling
nav, and `Navbar:Footer`, outside the nav, holds a zone below it, such as the user menu.

```twig {"preview":true}
<twig:Tabler:Navbar vertical expand="sm">
    <twig:Tabler:Navbar:Toggler target="sidebar-menu" />
    <twig:Tabler:Navbar:Brand href="/">Acme Admin</twig:Tabler:Navbar:Brand>
    <twig:Tabler:Navbar:Nav id="sidebar-menu" collapse>
        <twig:Tabler:Navbar:SectionTitle>Overview</twig:Tabler:Navbar:SectionTitle>
        <twig:Tabler:Navbar:Item href="/" icon="home" active>Dashboard</twig:Tabler:Navbar:Item>
        <twig:Tabler:Navbar:Item href="/deployments" icon="rocket">Deployments</twig:Tabler:Navbar:Item>
        <twig:Tabler:Navbar:SectionTitle>Billing</twig:Tabler:Navbar:SectionTitle>
        <twig:Tabler:Navbar:Item href="/invoices" icon="file-invoice">Invoices</twig:Tabler:Navbar:Item>
        <twig:Tabler:Navbar:Item href="/customers" icon="users">Customers</twig:Tabler:Navbar:Item>
        <twig:block name="side">
            <twig:Tabler:Navbar:Side>
                <twig:Tabler:Navbar:Item href="/help" icon="help">Help</twig:Tabler:Navbar:Item>
            </twig:Tabler:Navbar:Side>
        </twig:block>
    </twig:Tabler:Navbar:Nav>
    <twig:Tabler:Navbar:Footer>
        <twig:Tabler:Navbar:Item href="/me" icon="user">Jane Doe</twig:Tabler:Navbar:Item>
    </twig:Tabler:Navbar:Footer>
</twig:Tabler:Navbar>
```

## Folded sidebar

`folded` shrinks a vertical sidebar into an icon rail: item titles are hidden and section titles become short
separators. `folded="hover"` unfolds it on hover and keyboard focus, as here:

```twig {"preview":true}
<twig:Tabler:Navbar vertical expand="sm" folded="hover">
    <twig:Tabler:Navbar:Toggler target="folded-menu" />
    <twig:Tabler:Navbar:Brand href="/"><twig:Tabler:Icon name="bolt" /></twig:Tabler:Navbar:Brand>
    <twig:Tabler:Navbar:Nav id="folded-menu" collapse>
        <twig:Tabler:Navbar:SectionTitle>Overview</twig:Tabler:Navbar:SectionTitle>
        <twig:Tabler:Navbar:Item href="/" icon="home" active>Dashboard</twig:Tabler:Navbar:Item>
        <twig:Tabler:Navbar:Item href="/deployments" icon="rocket">Deployments</twig:Tabler:Navbar:Item>
        <twig:Tabler:Navbar:SectionTitle>Billing</twig:Tabler:Navbar:SectionTitle>
        <twig:Tabler:Navbar:Item href="/invoices" icon="file-invoice">Invoices</twig:Tabler:Navbar:Item>
    </twig:Tabler:Navbar:Nav>
    <twig:Tabler:Navbar:Footer>
        <twig:Tabler:Navbar:Item href="/me" icon="user">Jane Doe</twig:Tabler:Navbar:Item>
    </twig:Tabler:Navbar:Footer>
</twig:Tabler:Navbar>
```

## Props

| Prop        | Type         | Default | Description                                                                                                       |
| ----------- | ------------ | ------- | ----------------------------------------------------------------------------------------------------------------- |
| `expand`    | string       | `'md'`  | Breakpoint where the menu un-collapses: `sm` `md` `lg` `xl` `none`                                                |
| `dark`      | bool         | `false` | Light text colors for a dark background (`navbar-dark`)                                                           |
| `container` | string?      | `null`  | Suffix of the inner `container-*`: `xl`, or `fluid` when `vertical`, by default                                   |
| `vertical`  | bool         | `false` | Vertical sidebar (`navbar-vertical`), rendered as an `<aside>`                                                    |
| `folded`    | bool\|string | `false` | Vertical only: `true` for an icon rail (`navbar-folded`), `'hover'` to unfold it on hover (`navbar-folded-hover`) |
| `floating`  | bool         | `false` | Gap between the navbar and the edges around it (`navbar-floating`)                                                |

Other attributes go to the root `<header>`, or `<aside>` when `vertical`.

## Sub-components

| Component             | Renders                                                                                      |
| --------------------- | -------------------------------------------------------------------------------------------- |
| `Navbar:Brand`        | `<a class="navbar-brand">` with an `href`, `<span class="navbar-brand">` without             |
| `Navbar:Toggler`      | `<button class="navbar-toggler" data-bs-toggle="collapse">`, targeting `#{target}`           |
| `Navbar:Nav`          | `<ul class="navbar-nav">`, inside a `<div class="collapse navbar-collapse">` with `collapse` |
| `Navbar:Item`         | `<li class="nav-item">` around an `<a class="nav-link">`, with an optional icon              |
| `Navbar:SectionTitle` | `<li class="nav-section-title">`: hidden in a horizontal navbar                              |
| `Navbar:Side`         | `<div class="navbar-side">` around a `<ul class="navbar-nav">`                               |
| `Navbar:Footer`       | `<div class="navbar-footer">` around a `<ul class="navbar-nav">`                             |

### `Navbar:Brand` props

| Prop   | Type    | Default | Description                                       |
| ------ | ------- | ------- | ------------------------------------------------- |
| `href` | string? | `null`  | Link target, usually the home page; renders `<a>` |

### `Navbar:Toggler` props

| Prop     | Type   | Default  | Description                                    |
| -------- | ------ | -------- | ---------------------------------------------- |
| `target` | string | required | `id` of the `Navbar:Nav` it opens, without `#` |

### `Navbar:Nav` props

| Prop       | Type    | Default | Description                                                                   |
| ---------- | ------- | ------- | ----------------------------------------------------------------------------- |
| `collapse` | bool    | `false` | Wraps the list in a `.collapse.navbar-collapse` panel, for a `Navbar:Toggler` |
| `id`       | string? | `null`  | `id` of the collapse panel; only rendered with `collapse`                     |

Other attributes go to the `<ul>`.

### `Navbar:Item` props

| Prop     | Type    | Default | Description                                                       |
| -------- | ------- | ------- | ----------------------------------------------------------------- |
| `href`   | string? | `null`  | Link target; `#` when `null`                                      |
| `active` | bool    | `false` | Marks the current page (`active`, `aria-current="page"`)          |
| `icon`   | string? | `null`  | Leading Tabler icon or UX Icons name, rendered with `Tabler:Icon` |

Other attributes go to the `<li>`, not to the link.

## Blocks

| Block                 | Default                                                                                |
| --------------------- | -------------------------------------------------------------------------------------- |
| `side` (`Navbar:Nav`) | Nothing: put a `Navbar:Side` in it; rendered after the list, inside the collapse panel |
