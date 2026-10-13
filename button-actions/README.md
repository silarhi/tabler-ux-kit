# ButtonActions

Groups the small icon buttons that act on one item: edit, download, delete. Put
[Buttons](https://tabler-ux-components.silarhi.dev/components/actions/button/) with `appearance="action"` in it: each one is a square, borderless icon button
that only shows a background on hover (`btn-action`). The wrapper lines them up in a row (`btn-actions`), without a
gap: each button is a square larger than its icon, which leaves room between the icons. Both are hidden when the page
is printed.

```twig {"preview":true}
<twig:Tabler:Card>
    <twig:Tabler:Card:Header>
        <twig:Tabler:Card:Title>Invoice INV-0142</twig:Tabler:Card:Title>
        <twig:Tabler:Card:Actions>
            <twig:Tabler:ButtonActions>
                <twig:Tabler:Button appearance="action" href="/invoices/142/edit" aria-label="Edit"><twig:Tabler:Icon name="edit" /></twig:Tabler:Button>
                <twig:Tabler:Button appearance="action" href="/invoices/142.pdf" aria-label="Download"><twig:Tabler:Icon name="download" /></twig:Tabler:Button>
                <twig:Tabler:Button appearance="action" aria-label="Delete"><twig:Tabler:Icon name="trash" /></twig:Tabler:Button>
            </twig:Tabler:ButtonActions>
        </twig:Tabler:Card:Actions>
    </twig:Tabler:Card:Header>
    <twig:Tabler:Card:Body>Acme Corp, €1,250.00, due on November 1.</twig:Tabler:Card:Body>
</twig:Tabler:Card>
```

An action button has no text, so give each one an `aria-label`.

## Installation

::: installation

## In a table

Put the actions in the last cell of each row, and name the item in each `aria-label`. A dropdown fits in too: give its
`Dropdown:Toggle` the `btn-action` class and `noCaret`:

```twig {"preview":true}
<twig:Tabler:Table vcenter="{{ true }}">
    <thead>
        <tr><th>Invoice</th><th>Customer</th><th class="w-1"><span class="visually-hidden">Actions</span></th></tr>
    </thead>
    <tbody>
        {% for invoice in [{number: 'INV-0142', customer: 'Acme Corp'}, {number: 'INV-0143', customer: 'Globex'}] %}
            <tr>
                <td>{{ invoice.number }}</td>
                <td>{{ invoice.customer }}</td>
                <td>
                    <twig:Tabler:ButtonActions>
                        <twig:Tabler:Button appearance="action" href="/invoices/{{ invoice.number }}/edit" aria-label="Edit {{ invoice.number }}"><twig:Tabler:Icon name="edit" /></twig:Tabler:Button>
                        <twig:Tabler:Dropdown>
                            <twig:Tabler:Dropdown:Toggle noCaret="{{ true }}" class="btn-action" aria-label="More actions for {{ invoice.number }}"><twig:Tabler:Icon name="dots-vertical" /></twig:Tabler:Dropdown:Toggle>
                            <twig:Tabler:Dropdown:Menu end="{{ true }}">
                                <twig:Tabler:Dropdown:Item href="/invoices/{{ invoice.number }}/duplicate">Duplicate</twig:Tabler:Dropdown:Item>
                                <twig:Tabler:Dropdown:Item href="/invoices/{{ invoice.number }}/cancel">Cancel</twig:Tabler:Dropdown:Item>
                            </twig:Tabler:Dropdown:Menu>
                        </twig:Tabler:Dropdown>
                    </twig:Tabler:ButtonActions>
                </td>
            </tr>
        {% endfor %}
    </tbody>
</twig:Tabler:Table>
```

## Props

`ButtonActions` has no props. Other attributes go to the root `<div class="btn-actions">`.

## Blocks

| Block     | Default                          |
| --------- | -------------------------------- |
| `content` | Empty: the children, the buttons |
