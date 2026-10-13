# Accordion

A stack of sections, each with a header button that shows or hides its panel. It uses the Bootstrap collapse plugin
bundled in `tabler.js`. By default, opening a section closes the one that was open.

```twig {"preview":true}
<twig:Tabler:Accordion id="billing-faq" items="{{ [
    {title: 'When am I charged?', text: 'Your card is charged on the first day of each billing period, in euros.', open: true},
    {title: 'Can I change my plan?', text: 'Upgrades apply at once and are prorated. Downgrades apply at the next renewal.'},
    {title: 'Where are my invoices?', text: 'Every invoice is sent by email and listed under Settings, then Billing.'},
] }}" />
```

`items` is an array of `{title, text, open?, icon?, id?, level?, toggleIcon?}`. Each item gets the id `<id>-<n>`,
starting at 1, unless it has its own `id`, and uses the accordion `id` as its `data-bs-parent`, so that opening one
closes the others. Without an `id`, the accordion gets a random one (`accordion-<n>`): set your own when the ids must
stay the same between renders, for example to link to a section or to restore the open one.

## Installation

::: installation

## Items

`Accordion:Item` renders one section from its props. Give each item an `id` for its panel, and the id of the
accordion as `parent`: opening the item then closes the others. Mark the section to show on load `open`.

```twig {"preview":true}
<twig:Tabler:Accordion id="project-settings">
    <twig:Tabler:Accordion:Item id="project-general" parent="project-settings" title="General" text="Project name, description and default branch." open />
    <twig:Tabler:Accordion:Item id="project-members" parent="project-settings" title="Members" text="12 members, 3 of them maintainers." />
    <twig:Tabler:Accordion:Item id="project-integrations" parent="project-settings" title="Integrations" text="Slack and GitHub are connected." />
</twig:Tabler:Accordion>
```

The header is an `<h3>` by default. Set `level` on the item (1 to 6, any other value falls back to 3) to fit the
outline of the page. The button
inherits the font size of the heading, so the level changes the size of the label too. With `items`, set `level` on the
accordion for every generated item, or on an entry for that item only. `toggleIcon` works the same way.

## Always open

`alwaysOpen` leaves out `data-bs-parent` on the generated items, so several sections can stay open at once. Several
items can then be `open` on load. With `Accordion:Item`, leave out `parent` instead.

```twig {"preview":true}
<twig:Tabler:Accordion id="release-notes" alwaysOpen items="{{ [
    {title: 'Version 2.4.0', text: 'Adds CSV export to the reports page.', open: true},
    {title: 'Version 2.3.2', text: 'Fixes the date filter on invoices.', open: true},
    {title: 'Version 2.3.1', text: 'Speeds up the user search.'},
] }}" />
```

## Flush

`flush` removes the outer border and the rounded corners, to fit the accordion edge to edge in a card or a list:

```twig {"preview":true}
<div class="card">
    <div class="card-header">
        <h3 class="card-title">Notification settings</h3>
    </div>
    <twig:Tabler:Accordion id="notification-settings" flush items="{{ [
        {title: 'Email', text: 'A daily digest at 8:00, plus an email for each failed payment.', open: true},
        {title: 'Push', text: 'Mentions and direct messages only.'},
        {title: 'SMS', text: 'Security alerts, to +33 6 12 34 56 78.'},
    ] }}" />
</div>
```

## Tabs

`tabs` spaces the items out and gives each one its own border and rounded corners:

```twig {"preview":true}
<twig:Tabler:Accordion id="support-topics" tabs items="{{ [
    {title: 'Reset a password', text: 'Open the user, then click Send reset link. The link expires after 24 hours.', open: true},
    {title: 'Export data', text: 'Reports, then Export. Large exports are sent by email.'},
    {title: 'Close an account', text: 'Only an owner can close the account, from Settings, then Danger zone.'},
] }}" />
```

## Inverted

`inverted` moves the toggle indicator to the start of the header, before the label:

```twig {"preview":true}
<twig:Tabler:Accordion id="order-steps" inverted items="{{ [
    {title: 'Shipping address', text: '12 rue de la Paix, 75002 Paris, France.', open: true},
    {title: 'Delivery method', text: 'Standard delivery, 3 to 5 business days.'},
    {title: 'Payment', text: 'Visa ending in 4242.'},
] }}" />
```

## Icons and toggles

`icon` adds a leading [Tabler icon](https://tabler.io/icons) before the label. `plus` swaps the chevron for a plus
that turns into a close icon when the section opens. On the accordion, `plus` applies to every generated item; `icon`
is set per item.

```twig {"preview":true}
<twig:Tabler:Accordion id="account-sections" plus items="{{ [
    {title: 'Profile', text: 'Jane Cooper, jane.cooper@example.com.', icon: 'user', open: true},
    {title: 'Security', text: 'Two-factor authentication is enabled.', icon: 'lock'},
    {title: 'Billing', text: 'Pro plan, renews on November 1.', icon: 'credit-card'},
] }}" />
```

`toggleIcon` on `Accordion:Item` (or `Accordion:Button`) picks another icon for the indicator. It rotates half a turn
when the section opens:

```twig {"preview":true}
<twig:Tabler:Accordion id="server-logs">
    <twig:Tabler:Accordion:Item id="server-logs-web" parent="server-logs" title="web-01" text="Nginx restarted at 09:42." toggleIcon="caret-down" open />
    <twig:Tabler:Accordion:Item id="server-logs-db" parent="server-logs" title="db-01" text="Backup finished at 03:00, 2.4 GB." toggleIcon="caret-down" />
</twig:Tabler:Accordion>
```

## Blocks

The `title` and `body` blocks of `Accordion:Item` replace the label and the panel content, while the item keeps the
header, the button and the collapse wiring. Wrap the `body` block in `Accordion:Body` to keep the padding:

```twig {"preview":true}
<twig:Tabler:Accordion id="team-access">
    <twig:Tabler:Accordion:Item id="team-access-admins" parent="team-access" open>
        <twig:block name="title">
            Administrators <twig:Tabler:Badge variant="primary" light="{{ true }}" class="ms-2">2</twig:Tabler:Badge>
        </twig:block>
        <twig:block name="body">
            <twig:Tabler:Accordion:Body>
                <strong>Jane Cooper</strong> and <strong>Paul Martin</strong> can manage billing and members.
            </twig:Tabler:Accordion:Body>
        </twig:block>
    </twig:Tabler:Accordion:Item>
    <twig:Tabler:Accordion:Item id="team-access-viewers" parent="team-access" title="Viewers" text="Viewers can read reports but not edit them." />
</twig:Tabler:Accordion>
```

See [Composition](https://tabler-ux-components.silarhi.dev/getting-started/composition/) for how blocks work.

## Composed

To build a section from its parts, pass children to `Accordion:Item`: they replace its `content` block. Keep the ids in
sync: the `target` of `Accordion:Button` is the `id` of `Accordion:Collapse`, without `#`. The `icon` and `toggle`
blocks of `Accordion:Button` frame its label:

```twig {"preview":true}
<twig:Tabler:Accordion id="api-docs">
    <twig:Tabler:Accordion:Item>
        <twig:Tabler:Accordion:Header>
            <twig:Tabler:Accordion:Button target="api-docs-auth" open>
                <twig:block name="icon">
                    <twig:Tabler:Accordion:Icon><twig:Tabler:Icon name="key" aria-hidden="true" /></twig:Tabler:Accordion:Icon>
                </twig:block>
                Authentication
                <twig:block name="toggle">
                    <twig:Tabler:Accordion:Toggle plus />
                </twig:block>
            </twig:Tabler:Accordion:Button>
        </twig:Tabler:Accordion:Header>
        <twig:Tabler:Accordion:Collapse id="api-docs-auth" parent="api-docs" open>
            <twig:Tabler:Accordion:Body>
                Send the token in the <code>Authorization</code> header: <code>Bearer &lt;token&gt;</code>.
            </twig:Tabler:Accordion:Body>
        </twig:Tabler:Accordion:Collapse>
    </twig:Tabler:Accordion:Item>
    <twig:Tabler:Accordion:Item>
        <twig:Tabler:Accordion:Header>
            <twig:Tabler:Accordion:Button target="api-docs-limits">
                <twig:block name="icon">
                    <twig:Tabler:Accordion:Icon><twig:Tabler:Icon name="gauge" aria-hidden="true" /></twig:Tabler:Accordion:Icon>
                </twig:block>
                Rate limits
                <twig:block name="toggle">
                    <twig:Tabler:Accordion:Toggle plus />
                </twig:block>
            </twig:Tabler:Accordion:Button>
        </twig:Tabler:Accordion:Header>
        <twig:Tabler:Accordion:Collapse id="api-docs-limits" parent="api-docs">
            <twig:Tabler:Accordion:Body>
                600 requests per minute and per token. Over the limit, the API answers <code>429</code>.
            </twig:Tabler:Accordion:Body>
        </twig:Tabler:Accordion:Collapse>
    </twig:Tabler:Accordion:Item>
</twig:Tabler:Accordion>
```

## Accessibility

`Accordion:Button` is a `<button type="button">` with `aria-controls` set to the panel id and `aria-expanded` set
from `open`. Bootstrap updates `aria-expanded` and the `collapsed` class when the section opens or closes. The leading
icon and the toggle indicator are `aria-hidden="true"`. Each button sits in a heading (`Accordion:Header`), so screen
reader users can jump from section to section.

## Props

`Accordion`:

| Prop         | Type    | Default | Description                                                                                         |
| ------------ | ------- | ------- | --------------------------------------------------------------------------------------------------- |
| `id`         | string? | `null`  | DOM id, the `data-bs-parent` of the generated items and the prefix of their ids; random when `null` |
| `items`      | array?  | `null`  | `{title, text, open?, icon?, id?, level?, toggleIcon?}` entries, rendered with `Accordion:Item`     |
| `flush`      | bool    | `false` | No outer border nor rounded corners (`accordion-flush`)                                             |
| `inverted`   | bool    | `false` | Toggle indicator at the start of the header (`accordion-inverted`)                                  |
| `tabs`       | bool    | `false` | Spaced items, each fully bordered (`accordion-tabs`)                                                |
| `alwaysOpen` | bool    | `false` | Generated items stay open when another one opens (no `data-bs-parent`)                              |
| `plus`       | bool    | `false` | Generated items use the plus indicator (`accordion-button-toggle-plus`)                             |
| `level`      | int     | `3`     | Heading level of the generated items, 1 to 6; an entry's `level` wins                               |
| `toggleIcon` | string? | `null`  | Toggle indicator icon of the generated items; an entry's `toggleIcon` wins                          |

Other attributes go to the root `<div class="accordion">`.

`Accordion:Item`:

| Prop         | Type    | Default | Description                                                                           |
| ------------ | ------- | ------- | ------------------------------------------------------------------------------------- |
| `id`         | string? | `null`  | Id of the panel, targeted by the button                                               |
| `parent`     | string? | `null`  | Id of the accordion: when set, opening this item closes the others (`data-bs-parent`) |
| `title`      | string? | `null`  | Button label                                                                          |
| `text`       | string? | `null`  | Panel text, rendered with `Accordion:Body`                                            |
| `open`       | bool    | `false` | Expanded on load                                                                      |
| `icon`       | string? | `null`  | Leading Tabler icon name, rendered with `Accordion:Icon`                              |
| `plus`       | bool    | `false` | Plus indicator that turns into a close icon (`accordion-button-toggle-plus`)          |
| `toggleIcon` | string? | `null`  | Tabler icon name of the indicator (default `chevron-down`, or `plus`)                 |
| `level`      | int     | `3`     | Heading level of the header, 1 to 6; any other value renders an `<h3>`                |

Other attributes go to the `<div class="accordion-item">`.

`Accordion:Button` takes `target` (the panel id, without `#`), `open`, `icon`, `plus` and `toggleIcon`, as on the
item. `Accordion:Collapse` takes `id`, `parent` and `open` (`show`). `Accordion:Toggle` takes `plus` and `icon` (the
indicator icon name). `Accordion:Header` takes `level` (default `3`). On each of them, other attributes go to the
rendered element.

## Sub-components

| Component            | Renders                                                                                  |
| -------------------- | ---------------------------------------------------------------------------------------- |
| `Accordion:Item`     | `<div class="accordion-item">`: one section, with its header and its panel               |
| `Accordion:Header`   | `<h3 class="accordion-header">` (or the `level` set): holds the button                   |
| `Accordion:Button`   | `<button class="accordion-button" data-bs-toggle="collapse">`: the label and indicator   |
| `Accordion:Icon`     | `<span class="accordion-button-icon">`: a leading icon before the label                  |
| `Accordion:Toggle`   | `<span class="accordion-button-toggle">`: the indicator at the end, a chevron by default |
| `Accordion:Collapse` | `<div class="accordion-collapse collapse">`: the panel the button opens                  |
| `Accordion:Body`     | `<div class="accordion-body">`: the padded content of the panel                          |

## Blocks

`Accordion`:

| Block     | Default                                                |
| --------- | ------------------------------------------------------ |
| `content` | An `Accordion:Item` for each entry of the `items` prop |

`Accordion:Item`:

| Block     | Default                                                                                    |
| --------- | ------------------------------------------------------------------------------------------ |
| `title`   | The `title` prop                                                                           |
| `body`    | `Accordion:Body` with the `text` prop, when set                                            |
| `header`  | `Accordion:Header` with an `Accordion:Button` holding the `title` block                    |
| `content` | `header`, then `Accordion:Collapse` holding the `body` block: replace it to compose freely |

`Accordion:Button`:

| Block    | Default                                                    |
| -------- | ---------------------------------------------------------- |
| `icon`   | `Accordion:Icon` with the `icon` prop, when set            |
| `toggle` | `Accordion:Toggle`, with the `plus` and `toggleIcon` props |

The content of `Accordion:Button` is its label. `Accordion:Toggle` has a `content` block too: it holds the indicator
icon, so pass children to use your own SVG.
