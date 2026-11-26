# NumberInput

A number field between a decrease and an increase button (`.number-input`). `tabler.js` (`data-bs-toggle="number-input"`)
wires the buttons, the arrow keys, Home and End, and keeps stepping while a button is held. The
value stays within `min` and `max` and is rounded to the precision of `step`. Requires Tabler 1.7+.

```twig {"preview":true}
<twig:Tabler:NumberInput name="quantity" value="1" min="1" max="99" label="Quantity" />
```

The box and its buttons are rendered server-side, so the page does not shift when `tabler.js` starts. The input stays
the only field a form sees: the buttons write to it, and it fires the usual `input` and `change` events.

## Installation

::: installation

## Step

A fractional `step` sets the precision: with `step="0.25"`, the value always shows two decimals:

```twig {"preview":true}
<twig:Tabler:NumberInput name="hours" value="1.50" min="0" max="10" step="0.25" label="Hours" />
```

## Label and type

`id` pairs the input with a `<label for>`; without a visible label, give it an accessible name with `label`. The input
is a `type="text"` by default: `tabler.js` gives it `role="spinbutton"` and a numeric `inputmode`, and no native spin
buttons appear. `type="number"` keeps the browser's own validation:

```twig {"preview":true}
<label class="form-label" for="seats">Seats</label>
<twig:Tabler:NumberInput id="seats" name="seats" type="number" value="5" min="0" max="10" />
```

## Sizes

```twig {"preview":true}
<div class="d-flex flex-column align-items-start gap-2">
    {% for size in ['sm', 'md', 'lg'] %}
        <twig:Tabler:NumberInput size="{{ size }}" value="1" min="0" label="Quantity" />
    {% endfor %}
</div>
```

## Disabled and read-only

`disabled` and `readonly` lock the field; the buttons follow. `repeat="{{ false }}"` stops the buttons from repeating
while held:

```twig {"preview":true}
<div class="d-flex flex-column align-items-start gap-2">
    <twig:Tabler:NumberInput value="3" disabled="{{ true }}" label="Quantity" />
    <twig:Tabler:NumberInput value="3" readonly="{{ true }}" repeat="{{ false }}" label="Quantity" />
</div>
```

## Composed

The tag content replaces the buttons and the input: place `NumberInput:Button` and `NumberInput:Input` yourself, for
other icons or labels, a validation class, `required`, or a wider input (`--tblr-number-input-input-width`). An empty
button shows Tabler's minus or plus; any content replaces it:

```twig {"preview":true}
<twig:Tabler:NumberInput>
    <twig:Tabler:NumberInput:Button action="decrement" label="Fewer">
        <twig:Tabler:Icon name="chevron-down" />
    </twig:Tabler:NumberInput:Button>
    <twig:Tabler:NumberInput:Input name="amount" value="1000" min="0" step="100" label="Amount" style="--tblr-number-input-input-width: 6rem" />
    <twig:Tabler:NumberInput:Button action="increment" label="More">
        <twig:Tabler:Icon name="chevron-up" />
    </twig:Tabler:NumberInput:Button>
</twig:Tabler:NumberInput>
```

## Props

| Prop             | Type            | Default      | Description                                                                |
| ---------------- | --------------- | ------------ | -------------------------------------------------------------------------- |
| `name`           | string?         | `null`       | The `name` of the input                                                    |
| `id`             | string?         | `null`       | The `id` of the input, for a `<label for>`                                 |
| `value`          | number\|string? | `null`       | The initial value                                                          |
| `min`            | number\|string? | `null`       | The lower bound                                                            |
| `max`            | number\|string? | `null`       | The upper bound                                                            |
| `step`           | number\|string? | `null`       | The amount per step (`1` when unset); a fractional step sets the precision |
| `type`           | string          | `'text'`     | `text`, or `number` to keep the browser's validation                       |
| `label`          | string?         | `null`       | The accessible name of the input (`aria-label`)                            |
| `size`           | string          | `'md'`       | `sm` `md` `lg` (`number-input-sm`, `number-input-lg`)                      |
| `disabled`       | bool            | `false`      | Disables the input and both buttons                                        |
| `readonly`       | bool            | `false`      | Makes the input read-only; `tabler.js` disables the buttons                |
| `repeat`         | bool            | `true`       | Keeps stepping while a button is held (`data-bs-repeat="false"` when not)  |
| `decrementLabel` | string          | `'Decrease'` | The `aria-label` of the decrease button                                    |
| `incrementLabel` | string          | `'Increase'` | The `aria-label` of the increase button                                    |

Other attributes go to the root `<div class="number-input">`; compose with `NumberInput:Input` to set any attribute of
the input.

### NumberInput:Button

| Prop       | Type    | Default | Description                                           |
| ---------- | ------- | ------- | ----------------------------------------------------- |
| `action`   | string  |         | `decrement` or `increment`                            |
| `label`    | string? | `null`  | The `aria-label`; defaults to `Decrease` / `Increase` |
| `disabled` | bool    | `false` | Renders the button disabled                           |

### NumberInput:Input

Takes the `type`, `name`, `id`, `value`, `min`, `max`, `step`, `label`, `disabled` and `readonly` props of
`NumberInput`. Other attributes go to the `<input>`.

## Sub-components

| Component            | Renders                                                                       |
| -------------------- | ----------------------------------------------------------------------------- |
| `NumberInput:Button` | `<button type="button" class="btn btn-icon" data-bs-number-input-action="…">` |
| `NumberInput:Input`  | `<input class="form-control">`, the field between the buttons                 |

## Blocks

| Block       | Default                                                     |
| ----------- | ----------------------------------------------------------- |
| `decrement` | `NumberInput:Button` with `decrementLabel`                  |
| `input`     | `NumberInput:Input` with the input props                    |
| `increment` | `NumberInput:Button` with `incrementLabel`                  |
| `content`   | `decrement`, `input` and `increment`: replace it to compose |
