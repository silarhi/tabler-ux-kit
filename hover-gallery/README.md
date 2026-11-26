# Hover gallery

Several images in the space of one, for product cards, portfolios and listings. The first image shows; each image is an
invisible column, and the one under the pointer covers the gallery. No JavaScript, and on touch screens the gallery
turns into a strip to swipe. Requires Tabler 1.7+.

```twig {"preview":true}
<twig:Tabler:HoverGallery indicators class="rounded w-50" images="{{ [
    {src: '/examples/photo-1.jpg', alt: 'Open-plan office with desks'},
    {src: '/examples/photo-2.jpg', alt: 'Meeting room with a long table'},
    {src: '/examples/photo-3.jpg', alt: 'Lounge with sofas by the windows'},
] }}" />
```

`images` is an array of `{src, alt}`, rendered with `HoverGallery:Item`. `indicators` adds a bar per image at the
bottom edge, lit for the image on display, on a soft dark gradient that keeps them visible on any photo.

## Installation

::: installation

## Aspect ratio

The gallery is a square and the images are cropped to fill it. Set `--tblr-hover-gallery-aspect-ratio` in a `style`
attribute for another shape:

```twig {"preview":true}
<twig:Tabler:HoverGallery class="rounded w-50" style="--tblr-hover-gallery-aspect-ratio: 16 / 9" images="{{ [
    {src: '/examples/photo-1.jpg', alt: 'Open-plan office with desks'},
    {src: '/examples/photo-2.jpg', alt: 'Meeting room with a long table'},
    {src: '/examples/photo-3.jpg', alt: 'Lounge with sofas by the windows'},
] }}" />
```

## Composed

Children replace the generated items: place one `HoverGallery:Item` per image, with `src` and `alt`, or your own
`<img>` (a `srcset`, a `loading` attribute…) as its content. `card-img-top` puts the gallery in place of a card image:

```twig {"preview":true}
<twig:Tabler:Card class="w-50">
    <twig:Tabler:HoverGallery indicators class="card-img-top">
        <twig:Tabler:HoverGallery:Item src="/examples/photo-1.jpg" alt="Open-plan office with desks" />
        <twig:Tabler:HoverGallery:Item src="/examples/photo-2.jpg" alt="Meeting room with a long table" />
        <twig:Tabler:HoverGallery:Item src="/examples/photo-3.jpg" alt="Lounge with sofas by the windows" />
    </twig:Tabler:HoverGallery>
    <twig:Tabler:Card:Body>
        <twig:Tabler:Card:Title>Coworking, Capitole</twig:Tabler:Card:Title>
        <div class="text-secondary">From €290 a month</div>
    </twig:Tabler:Card:Body>
</twig:Tabler:Card>
```

## Accessibility

Give every image an `alt` saying what this photo shows, not only the product name. Keyboard users only see the first
image: keep the information of the others elsewhere on the page. In a link, the whole gallery leads to one place.

## Props

| Prop         | Type   | Default | Description                                                                                 |
| ------------ | ------ | ------- | ------------------------------------------------------------------------------------------- |
| `images`     | array? | `null`  | `{src, alt?}` entries, rendered with `HoverGallery:Item`                                    |
| `indicators` | bool   | `false` | A bar per image at the bottom edge, lit for the one on display (`hover-gallery-indicators`) |

Other attributes go to the root `<div class="hover-gallery">`.

`HoverGallery:Item`:

| Prop  | Type    | Default | Description                       |
| ----- | ------- | ------- | --------------------------------- |
| `src` | string? | `null`  | Image URL, rendered as an `<img>` |
| `alt` | string  | `''`    | What this photo shows             |

Other attributes go to the `<div class="hover-gallery-item">`.

## Sub-components

| Component           | Renders                                               |
| ------------------- | ----------------------------------------------------- |
| `HoverGallery:Item` | `<div class="hover-gallery-item">` around one `<img>` |

## Blocks

| Block     | Default                                                                 |
| --------- | ----------------------------------------------------------------------- |
| `content` | A `HoverGallery:Item` for each entry of `images`: replace it to compose |

The `content` block of `HoverGallery:Item` holds the `<img>` of its `src` and `alt` props.
