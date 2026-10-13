# Table

A styled `<table>`. Write the `<thead>` and `<tbody>` yourself; the component sets the classes and the scroll wrapper.

```twig {"preview":true}
<twig:Tabler:Table>
    <thead>
        <tr><th>Name</th><th>Email</th><th>Role</th></tr>
    </thead>
    <tbody>
        <tr><td>Jane Cooper</td><td>jane@example.com</td><td>Admin</td></tr>
        <tr><td>Wade Warren</td><td>wade@example.com</td><td>Editor</td></tr>
        <tr><td>Esther Howard</td><td>esther@example.com</td><td>Viewer</td></tr>
    </tbody>
</twig:Tabler:Table>
```

## Installation

::: installation

## Styles

`striped` adds zebra rows, `hover` highlights the row under the pointer, `bordered` draws a border around every cell.
Combine them freely:

```twig {"preview":true}
<twig:Tabler:Table striped hover>
    <thead>
        <tr><th>Invoice</th><th>Customer</th><th class="text-end">Amount</th></tr>
    </thead>
    <tbody>
        <tr><td>INV-0142</td><td>Acme Corp</td><td class="text-end">€1,250.00</td></tr>
        <tr><td>INV-0143</td><td>Globex</td><td class="text-end">€480.00</td></tr>
        <tr><td>INV-0144</td><td>Initech</td><td class="text-end">€3,100.00</td></tr>
    </tbody>
</twig:Tabler:Table>
<twig:Tabler:Table bordered>
    <thead>
        <tr><th>Invoice</th><th>Customer</th><th class="text-end">Amount</th></tr>
    </thead>
    <tbody>
        <tr><td>INV-0142</td><td>Acme Corp</td><td class="text-end">€1,250.00</td></tr>
        <tr><td>INV-0143</td><td>Globex</td><td class="text-end">€480.00</td></tr>
    </tbody>
</twig:Tabler:Table>
```

`size="sm"` tightens the cell padding, `borderless` removes the borders, and `nowrap` keeps the cell text on one line.
`transparent` removes the background of the header cells, and `center` centers the cells horizontally:

```twig {"preview":true}
<twig:Tabler:Table size="sm" borderless="{{ true }}" nowrap="{{ true }}">
    <thead>
        <tr><th>Date</th><th>Event</th><th>User</th></tr>
    </thead>
    <tbody>
        <tr><td>2026-10-12 09:42</td><td>Invoice INV-0144 sent to Initech</td><td>jane@example.com</td></tr>
        <tr><td>2026-10-12 09:15</td><td>Customer Globex updated</td><td>wade@example.com</td></tr>
        <tr><td>2026-10-11 17:03</td><td>Payment of €480.00 received</td><td>system</td></tr>
    </tbody>
</twig:Tabler:Table>
```

## Vertical centering

`vcenter` centers the cells vertically, for rows with avatars or buttons:

```twig {"preview":true}
<twig:Tabler:Table vcenter>
    <thead>
        <tr><th>User</th><th>Role</th><th></th></tr>
    </thead>
    <tbody>
        {% for user in [
            {name: 'Jane Cooper', email: 'jane@example.com', role: 'Admin', avatar: '/examples/avatar-1.jpg'},
            {name: 'Wade Warren', email: 'wade@example.com', role: 'Editor', avatar: '/examples/avatar-2.jpg'},
        ] %}
            <tr>
                <td>
                    <div class="d-flex align-items-center">
                        <twig:Tabler:Avatar image="{{ user.avatar }}" class="me-2" />
                        <div>
                            <div>{{ user.name }}</div>
                            <div class="text-secondary">{{ user.email }}</div>
                        </div>
                    </div>
                </td>
                <td>{{ user.role }}</td>
                <td class="text-end"><a href="#">Edit</a></td>
            </tr>
        {% endfor %}
    </tbody>
</twig:Tabler:Table>
```

## Stacked rows on phones

`mobile` stacks each row into a block below a breakpoint (`table-mobile-{breakpoint}`): `sm`, `md`, `lg`, `xl` or
`xxl`. The header row is hidden, and each cell is labelled by its `data-label` attribute: write the cells with
`Table:Cell` and its `label` prop. Narrow the window to see it:

```twig {"preview":true}
<twig:Tabler:Table mobile="md">
    <thead>
        <tr><th>Invoice</th><th>Customer</th><th>Status</th><th class="text-end">Amount</th></tr>
    </thead>
    <tbody>
        <tr>
            <twig:Tabler:Table:Cell label="Invoice">INV-0142</twig:Tabler:Table:Cell>
            <twig:Tabler:Table:Cell label="Customer">Acme Corp</twig:Tabler:Table:Cell>
            <twig:Tabler:Table:Cell label="Status"><twig:Tabler:Badge variant="success" light="{{ true }}">Paid</twig:Tabler:Badge></twig:Tabler:Table:Cell>
            <twig:Tabler:Table:Cell label="Amount" class="text-end">€1,250.00</twig:Tabler:Table:Cell>
        </tr>
        <tr>
            <twig:Tabler:Table:Cell label="Invoice">INV-0143</twig:Tabler:Table:Cell>
            <twig:Tabler:Table:Cell label="Customer">Globex</twig:Tabler:Table:Cell>
            <twig:Tabler:Table:Cell label="Status"><twig:Tabler:Badge variant="warning" light="{{ true }}">Pending</twig:Tabler:Badge></twig:Tabler:Table:Cell>
            <twig:Tabler:Table:Cell label="Amount" class="text-end">€480.00</twig:Tabler:Table:Cell>
        </tr>
    </tbody>
</twig:Tabler:Table>
```

## Truncated cells

`Table:Cell` with `truncate` cuts a long text with an ellipsis instead of stretching the table: the cell takes the
remaining width (`td-truncate`) and wraps its content in a `<div class="text-truncate">`. Here `nowrap` keeps the
other cells on one line:

```twig {"preview":true}
<twig:Tabler:Table nowrap="{{ true }}">
    <thead>
        <tr><th>Invoice</th><th>Note</th><th class="text-end">Amount</th></tr>
    </thead>
    <tbody>
        <tr>
            <td>INV-0142</td>
            <twig:Tabler:Table:Cell truncate="{{ true }}">Paid in two parts: the first by bank transfer on October 9, the second by card after the customer asked for a corrected invoice with the new billing address.</twig:Tabler:Table:Cell>
            <td class="text-end">€1,250.00</td>
        </tr>
        <tr>
            <td>INV-0143</td>
            <twig:Tabler:Table:Cell truncate="{{ true }}">Reminder sent.</twig:Tabler:Table:Cell>
            <td class="text-end">€480.00</td>
        </tr>
    </tbody>
</twig:Tabler:Table>
```

## Sortable headers and selectable rows

`Table:Sort` renders a header button with a sort arrow (`table-sort`), to put in a `<th>`. `field` is rendered as
`data-sort`, and `direction` (`asc` or `desc`) marks the current sort. The classes only style the header: sort the rows
yourself, e.g. with List.js, which reads `data-sort`, or with a link that reloads the page sorted.

`selectable` highlights the rows whose `Table:Check` is checked (`table-selectable`), with CSS only. `Table:Check`
renders the row checkbox; give each one an `aria-label` naming its row. A "select all" checkbox in the header needs
your own JavaScript:

```twig {"preview":true}
<twig:Tabler:Table selectable="{{ true }}" vcenter="{{ true }}">
    <thead>
        <tr>
            <th class="w-1"><twig:Tabler:Table:Check aria-label="Select all invoices" /></th>
            <th><twig:Tabler:Table:Sort field="invoice" direction="asc">Invoice</twig:Tabler:Table:Sort></th>
            <th><twig:Tabler:Table:Sort field="customer">Customer</twig:Tabler:Table:Sort></th>
            <th class="text-end"><twig:Tabler:Table:Sort field="amount">Amount</twig:Tabler:Table:Sort></th>
        </tr>
    </thead>
    <tbody>
        {% for invoice in [
            {number: 'INV-0142', customer: 'Acme Corp', amount: '€1,250.00', checked: true},
            {number: 'INV-0143', customer: 'Globex', amount: '€480.00', checked: false},
            {number: 'INV-0144', customer: 'Initech', amount: '€3,100.00', checked: false},
        ] %}
            <tr>
                <td>
                    <twig:Tabler:Table:Check name="invoices[]" value="{{ invoice.number }}" checked="{{ invoice.checked }}" aria-label="Select {{ invoice.number }}" />
                </td>
                <td>{{ invoice.number }}</td>
                <td>{{ invoice.customer }}</td>
                <td class="text-end">{{ invoice.amount }}</td>
            </tr>
        {% endfor %}
    </tbody>
</twig:Tabler:Table>
```

## In a card

`card` runs the table edge to edge in a card, aligned with the card padding and without a bottom margin
(`card-table`). Classes and other attributes go to the `<table>`, not to the wrapper:

```twig {"preview":true}
<twig:Tabler:Card>
    <twig:Tabler:Card:Header>
        <twig:Tabler:Card:Title>Recent deployments</twig:Tabler:Card:Title>
    </twig:Tabler:Card:Header>
    <twig:Tabler:Table card="{{ true }}">
        <thead>
            <tr><th>Environment</th><th>Commit</th><th>Deployed</th></tr>
        </thead>
        <tbody>
            <tr><td>Production</td><td><code>a3f9c21</code></td><td>2 hours ago</td></tr>
            <tr><td>Staging</td><td><code>e81b0d4</code></td><td>Yesterday</td></tr>
        </tbody>
    </twig:Tabler:Table>
</twig:Tabler:Card>
```

## Without the scroll wrapper

The table is wrapped in a `<div class="table-responsive">` by default. Pass `responsive="{{ false }}"` to render the
bare `<table>` (see [boolean props](https://tabler-ux-components.silarhi.dev/getting-started/composition/#boolean-props)):

```twig {"preview":true}
<twig:Tabler:Table responsive="{{ false }}">
    <thead>
        <tr><th>Key</th><th>Value</th></tr>
    </thead>
    <tbody>
        <tr><td>APP_ENV</td><td>prod</td></tr>
        <tr><td>APP_DEBUG</td><td>0</td></tr>
    </tbody>
</twig:Tabler:Table>
```

## Props

| Prop          | Type    | Default | Description                                                                         |
| ------------- | ------- | ------- | ----------------------------------------------------------------------------------- |
| `responsive`  | bool    | `true`  | Wraps the table in `<div class="table-responsive">`                                 |
| `vcenter`     | bool    | `false` | Centers cells vertically (`table-vcenter`)                                          |
| `center`      | bool    | `false` | Centers cells horizontally (`table-center`)                                         |
| `striped`     | bool    | `false` | Zebra rows (`table-striped`)                                                        |
| `hover`       | bool    | `false` | Highlights the hovered row (`table-hover`)                                          |
| `bordered`    | bool    | `false` | Borders on every cell (`table-bordered`)                                            |
| `borderless`  | bool    | `false` | No borders (`table-borderless`)                                                     |
| `transparent` | bool    | `false` | No background on the header cells (`table-transparent`)                             |
| `nowrap`      | bool    | `false` | Cell text does not wrap (`table-nowrap`)                                            |
| `selectable`  | bool    | `false` | Highlights the rows whose `Table:Check` is checked (`table-selectable`)             |
| `size`        | string  | `'md'`  | `sm` `md`: `sm` tightens the cell padding (`table-sm`)                              |
| `mobile`      | string? | `null`  | `sm` `md` `lg` `xl` `xxl`: stacks the rows below this breakpoint (`table-mobile-*`) |
| `card`        | bool    | `false` | Edge to edge inside a card, no bottom margin (`card-table`)                         |

Other attributes go to the `<table>`.

`Table:Sort`:

| Prop        | Type    | Default | Description                                    |
| ----------- | ------- | ------- | ---------------------------------------------- |
| `field`     | string? | `null`  | Sort key, rendered as `data-sort`              |
| `direction` | string? | `null`  | `asc` `desc`: marks the current sort direction |

Other attributes go to the `<button class="table-sort">`.

`Table:Cell`:

| Prop       | Type    | Default | Description                                                                          |
| ---------- | ------- | ------- | ------------------------------------------------------------------------------------ |
| `label`    | string? | `null`  | Column name shown when `mobile` stacks the row (`data-label`)                        |
| `truncate` | bool    | `false` | Cuts the content with an ellipsis (`td-truncate`, content in a `.text-truncate` div) |

Other attributes go to the `<td>`. `Table:Check` has no props: its attributes (`name`, `value`,
`checked`, `aria-label`…) go to the `<input type="checkbox">`.

## Sub-components

| Component     | Renders                                                                                   |
| ------------- | ----------------------------------------------------------------------------------------- |
| `Table:Sort`  | `<button type="button" class="table-sort">`: a sortable header                            |
| `Table:Check` | `<input type="checkbox" class="form-check-input table-selectable-check">`: a row checkbox |
| `Table:Cell`  | `<td>`: a cell with a mobile label or a truncated content                                 |

## Blocks

| Block     | Default                                                   |
| --------- | --------------------------------------------------------- |
| `content` | Empty: the children, the `<thead>` and `<tbody>`, go here |

`Table:Sort` and `Table:Cell` have an empty `content` block too, for the header label and the cell content.
