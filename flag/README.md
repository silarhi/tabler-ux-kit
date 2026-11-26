# Flag

A flag drawn at a 5:4 ratio, from the 304 flags of [Tabler Flags](https://github.com/tabler/tabler-flags). Requires
Tabler 1.7+ and its flags plugin: load `tabler-flags.css` (or `tabler-flags.min.css`) next to `tabler.css`, from
`@tabler/core/dist/css/` or the CDN.

```twig {"preview":true}
<div class="d-flex gap-2">
    <twig:Tabler:Flag code="fr" label="France" />
    <twig:Tabler:Flag code="de" label="Germany" />
    <twig:Tabler:Flag code="BR" label="Brazil" />
    <twig:Tabler:Flag code="gb-sct" label="Scotland" />
    <twig:Tabler:Flag code="european-union" label="European Union" />
</div>
```

`code` is the ISO 3166 code of the country (`fr`, `br`) or of a subdivision (`gb-sct`), and the slug of a flag without
one (`european-union`, `nato`, `african-union`). It is lowercased, so `BR` works too. The full list is on
[Tabler's flags page](https://docs.tabler.io/ui/plugins/flags#flags-list).

## Installation

::: installation

## Sizes

`size` takes the [avatar](https://tabler-ux-components.silarhi.dev/components/content/avatar/) sizes, `xxs` to `2xl`, so a flag and an avatar in one list line
up. Without it, the flag is the size of an avatar:

```twig {"preview":true}
<div class="d-flex align-items-end gap-2">
    {% for size in ['2xl', 'xl', 'lg', 'md', 'sm', 'xs', 'xxs'] %}
        <twig:Tabler:Flag code="us" size="{{ size }}" label="United States" />
    {% endfor %}
</div>
```

## Accessibility

A flag is a picture: `label` names it (`role="img"` and an `aria-label`), for a flag on its own. Without `label`, it is
decoration, hidden with `aria-hidden="true"`: put the country name in text next to it, as here.

```twig {"preview":true}
<twig:Tabler:ListGroup>
    {% for office in [
        {code: 'fr', city: 'Toulouse', country: 'France'},
        {code: 'ca', city: 'Montréal', country: 'Canada'},
        {code: 'jp', city: 'Osaka', country: 'Japan'},
    ] %}
        <twig:Tabler:ListGroup:Item title="{{ office.city }}" description="{{ office.country }}">
            <twig:block name="media">
                <twig:Tabler:ListGroup:Media><twig:Tabler:Flag code="{{ office.code }}" size="sm" /></twig:Tabler:ListGroup:Media>
            </twig:block>
        </twig:Tabler:ListGroup:Item>
    {% endfor %}
</twig:Tabler:ListGroup>
```

A flag is not a language: on a language switcher, write the language name, in that language.

## Props

| Prop    | Type    | Default | Description                                                                             |
| ------- | ------- | ------- | --------------------------------------------------------------------------------------- |
| `code`  | string  | —       | ISO 3166 code or slug of the flag (`flag-country-{code}`), lowercased                   |
| `size`  | string? | `null`  | `xxs` `xs` `sm` `md` `lg` `xl` `2xl` (`flag-{size}`)                                    |
| `label` | string? | `null`  | Accessible name (`role="img"`, `aria-label`); unset, the flag gets `aria-hidden="true"` |

Other attributes go to the `<span class="flag">`.

## Sub-components

None: a flag has no parts.

## Blocks

None: the flag is an empty `<span>`, drawn by the stylesheet.
