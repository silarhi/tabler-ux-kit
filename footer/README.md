# Footer

The footer at the bottom of a page: a copyright line and links on the start side, more links on the end side. Put it
in the `footer` block of a [`Page`](../page/), or at the end of a `Page:Wrapper`: Tabler pushes it to the bottom of the
page. It is hidden when the page is printed (`d-print-none`).

```twig {"preview":true}
<twig:Tabler:Footer
    copyright="Copyright © 2026 Acme. All rights reserved."
    links="{{ [{label: 'v1.2.0', href: '/changelog'}] }}"
    endLinks="{{ [{label: 'Documentation', href: '/docs'}, {label: 'License', href: '/license'}, {label: 'Source code', href: '/source'}] }}"
/>
```

`links` and `endLinks` are arrays of `{label, href}`: an item with an `href` is a muted `link-secondary` link, one
without is plain text. Both sides stack and center below the `lg` breakpoint, the end side first.

## Installation

::: installation

## Transparent

`transparent` drops the background and the top border of the footer (`footer-transparent`), so it blends with the
page behind it, as on Tabler's own layouts.

```twig {"preview":true}
<twig:Tabler:Footer transparent copyright="Copyright © 2026 Acme. All rights reserved." />
```

## Composed

Replace the `copyright` block for a copyright line with markup, here a link, and the `start` or `end` block for a side
of your own, built with `Footer:Links` and `Footer:Item`. Here the end side is a labeled navigation landmark. Direct
children fill the `content` block, which holds the whole row inside the container: they replace both sides.

```twig {"preview":true}
<twig:Tabler:Footer transparent>
    <twig:block name="copyright">
        <twig:Tabler:Footer:Item>Copyright © 2026 <a href="/" class="link-secondary">Acme</a>. All rights reserved.</twig:Tabler:Footer:Item>
    </twig:block>
    <twig:block name="end">
        <nav aria-label="Footer">
            <twig:Tabler:Footer:Links>
                <twig:Tabler:Footer:Item href="/docs">Documentation</twig:Tabler:Footer:Item>
                <twig:Tabler:Footer:Item href="/sponsor"><twig:Tabler:Icon name="heart" class="icon icon-inline text-pink" /> Sponsor</twig:Tabler:Footer:Item>
            </twig:Tabler:Footer:Links>
        </nav>
    </twig:block>
</twig:Tabler:Footer>
```

## Props

| Prop          | Type    | Default | Description                                                                |
| ------------- | ------- | ------- | -------------------------------------------------------------------------- |
| `copyright`   | string? | `null`  | Copyright line, the first item of the start side                           |
| `links`       | array   | `[]`    | Items `{label, href?}` after the copyright, on the start side              |
| `endLinks`    | array   | `[]`    | Items `{label, href?}` of the end side                                     |
| `transparent` | bool    | `false` | No background nor top border (`footer-transparent`)                        |
| `container`   | string  | `'xl'`  | Suffix of the inner `container-*`; match the one of the page, e.g. `fluid` |

Other attributes go to the root `<footer>`.

## Sub-components

| Component      | Renders                                                                                |
| -------------- | -------------------------------------------------------------------------------------- |
| `Footer:Links` | `<ul class="list-inline list-inline-dots mb-0">`: items separated by dots              |
| `Footer:Item`  | `<li class="list-inline-item">`, around an `<a class="link-secondary">` with an `href` |

### `Footer:Item` props

| Prop   | Type    | Default | Description                                     |
| ------ | ------- | ------- | ----------------------------------------------- |
| `href` | string? | `null`  | Link target; without it, the item is plain text |

Other attributes go to the `<li>`, not to the link.

## Blocks

| Block       | Default                                                                                          |
| ----------- | ------------------------------------------------------------------------------------------------ |
| `copyright` | A `Footer:Item` with the `copyright` prop, when set                                              |
| `start`     | A `Footer:Links` with `copyright` and an item per entry of `links`, when there is one            |
| `end`       | A `Footer:Links` with an item per entry of `endLinks`, when there is one                         |
| `content`   | The `.row` with the `end` then the `start` column (`flex-row-reverse`), each only when not empty |
