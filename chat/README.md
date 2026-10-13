# Chat

A conversation: a support ticket thread, comments on an order, messages between team members.

```twig {"preview":true}
{% set messages = [
    {author: 'Jane Cooper', date: '10:24', text: 'Hi, invoice INV-0142 was charged twice this month.', avatar: '/examples/avatar-1.jpg'},
    {author: 'Wade Warren', date: '10:26', text: 'Sorry about that. I can see both payments, let me check.', avatar: '/examples/avatar-2.jpg', me: true},
    {author: 'Wade Warren', date: '10:31', text: 'The second payment is refunded. It shows up in 3 to 5 days.', avatar: '/examples/avatar-2.jpg', me: true},
    {author: 'Jane Cooper', date: '10:32', text: 'Great, thank you!', avatar: '/examples/avatar-1.jpg'},
] %}
<twig:Tabler:Chat messages="{{ messages }}" />
```

`messages` is an array of messages, each with the optional keys `author`, `date`, `text`, `avatar` (an image URL) and
`me`. Each one renders as a `Chat:Message` row inside `Chat:Bubbles`. A message with `me: true` is sent by the current
user: its bubble is tinted (`chat-bubble-me`) and the row is pushed to the end, with the avatar after the bubble.

## Installation

::: installation

## Messages

To mix messages with other content, or to loop yourself, put `Chat:Message` rows in `Chat:Bubbles`, which stacks them
with a gap. `Chat:Message` takes the same props as a message of the array. Without `author` and `date`, the bubble has
no title line; without `avatar`, the row has no avatar column:

```twig {"preview":true}
<twig:Tabler:Chat>
    <twig:Tabler:Chat:Bubbles>
        <twig:Tabler:Chat:Message author="Esther Howard" date="09:12" text="Can you add me to the billing team?" avatar="/examples/avatar-3.jpg" />
        <twig:Tabler:Chat:Message author="Wade Warren" date="09:15" text="Done, you have access now." avatar="/examples/avatar-2.jpg" me />
        <twig:Tabler:Chat:Message author="Esther Howard" text="Thanks, I can see the invoices." />
    </twig:Tabler:Chat:Bubbles>
</twig:Tabler:Chat>
```

The bubble column (`col col-lg-6`) fills the row next to the avatar, and half of the row from the `lg` breakpoint, as
in Tabler. A long message wraps inside it.

## Avatars

The `avatar` prop renders a plain `<span class="avatar">` with the picture. Override the `avatar` block of
`Chat:Message` to show something else, such as initials with `Avatar`:

```twig {"preview":true}
<twig:Tabler:Chat>
    <twig:Tabler:Chat:Bubbles>
        <twig:Tabler:Chat:Message author="Jane Cooper" date="14:02" text="Is the export ready?">
            <twig:block name="avatar"><twig:Tabler:Avatar variant="primary">JC</twig:Tabler:Avatar></twig:block>
        </twig:Tabler:Chat:Message>
        <twig:Tabler:Chat:Message author="Wade Warren" date="14:05" text="Yes, it is in your downloads." me>
            <twig:block name="avatar"><twig:Tabler:Avatar variant="success">WW</twig:Tabler:Avatar></twig:block>
        </twig:Tabler:Chat:Message>
    </twig:Tabler:Chat:Bubbles>
</twig:Tabler:Chat>
```

## Composed

Pass children to `Chat:Message` to replace its bubble: the row keeps the avatar and the alignment. Build the bubble
with `Chat:Bubble` and its sub-components. A `me` row does not tint the bubble you pass: set `me` on the
`Chat:Bubble` too.

```twig {"preview":true}
<twig:Tabler:Chat>
    <twig:Tabler:Chat:Bubbles>
        <twig:Tabler:Chat:Message avatar="/examples/avatar-1.jpg">
            <twig:Tabler:Chat:Bubble>
                <twig:Tabler:Chat:Bubble:Title>
                    <twig:Tabler:Chat:Bubble:Author>Jane Cooper</twig:Tabler:Chat:Bubble:Author>
                    <twig:Tabler:Chat:Bubble:Date>16:40</twig:Tabler:Chat:Bubble:Date>
                </twig:Tabler:Chat:Bubble:Title>
                <twig:Tabler:Chat:Bubble:Body>
                    <p>My desk at the new Paris office is ready.</p>
                    <img src="/examples/photo-1.jpg" width="240" class="rounded img-fluid mt-2" alt="A laptop on a desk next to a vase of white flowers">
                </twig:Tabler:Chat:Bubble:Body>
            </twig:Tabler:Chat:Bubble>
        </twig:Tabler:Chat:Message>
        <twig:Tabler:Chat:Message avatar="/examples/avatar-2.jpg" me>
            <twig:Tabler:Chat:Bubble me>
                <twig:Tabler:Chat:Bubble:Title>
                    <twig:Tabler:Chat:Bubble:Author>Wade Warren</twig:Tabler:Chat:Bubble:Author>
                    <twig:Tabler:Chat:Bubble:Date>16:42</twig:Tabler:Chat:Bubble:Date>
                </twig:Tabler:Chat:Bubble:Title>
                <twig:Tabler:Chat:Bubble:Body>
                    <p>Looks great. The move is planned for <strong>March 3</strong>.</p>
                </twig:Tabler:Chat:Bubble:Body>
            </twig:Tabler:Chat:Bubble>
        </twig:Tabler:Chat:Message>
    </twig:Tabler:Chat:Bubbles>
</twig:Tabler:Chat>
```

`Chat:Bubble:Body` holds any content: wrap text in paragraphs, and put images below the text.

## Blocks

`Chat:Bubble` takes `author`, `date`, `text` and `me` too. Override its `title` or `body` block, and the other one keeps
rendering from the props. Here the body holds a link and bold text:

```twig {"preview":true}
<twig:Tabler:Chat>
    <twig:Tabler:Chat:Bubbles>
        <twig:Tabler:Chat:Message avatar="/examples/avatar-3.jpg">
            <twig:Tabler:Chat:Bubble author="Esther Howard" date="11:08">
                <twig:block name="body">
                    <twig:Tabler:Chat:Bubble:Body>
                        <p>The refund for <a href="#">INV-0142</a> is <strong>approved</strong>.</p>
                    </twig:Tabler:Chat:Bubble:Body>
                </twig:block>
            </twig:Tabler:Chat:Bubble>
        </twig:Tabler:Chat:Message>
    </twig:Tabler:Chat:Bubbles>
</twig:Tabler:Chat>
```

See [Composition](https://tabler-ux-components.silarhi.dev/getting-started/composition/) for how blocks work.

## Typing indicator

`Chat:Typing` is a bubble with an italic text followed by animated dots. Its text comes from the children or from
`label` (default "Typing"); always keep a text, the dots alone say nothing. Put it in a `Chat:Message` row to align it
with an avatar. Placed directly in `Chat:Bubbles`, it sits at the start, as wide as its text.

```twig {"preview":true}
<twig:Tabler:Chat>
    <twig:Tabler:Chat:Bubbles>
        <twig:Tabler:Chat:Message author="Wade Warren" date="10:24" text="The Q3 report is ready, do you want the PDF?" avatar="/examples/avatar-2.jpg" me />
        <twig:Tabler:Chat:Message avatar="/examples/avatar-1.jpg">
            <twig:Tabler:Chat:Typing>Jane Cooper is typing</twig:Tabler:Chat:Typing>
        </twig:Tabler:Chat:Message>
    </twig:Tabler:Chat:Bubbles>
</twig:Tabler:Chat>
```

## Accessibility

Keep the messages in reading order and an author name on each bubble: the color and the side alone must not tell who
sent a message. The avatar is a decorative background image with no text alternative.

## Props

`Chat`:

| Prop       | Type   | Default | Description                                                                          |
| ---------- | ------ | ------- | ------------------------------------------------------------------------------------ |
| `messages` | array? | `null`  | Messages (`author`, `date`, `text`, `avatar`, `me`), rendered as `Chat:Message` rows |

Other attributes go to the root `<div class="chat">`.

`Chat:Message`:

| Prop     | Type    | Default | Description                                                     |
| -------- | ------- | ------- | --------------------------------------------------------------- |
| `author` | string? | `null`  | Sender name, passed to the bubble                               |
| `date`   | string? | `null`  | Time of the message, passed to the bubble                       |
| `text`   | string? | `null`  | Message text, passed to the bubble                              |
| `avatar` | string? | `null`  | Sender avatar image URL                                         |
| `me`     | bool    | `false` | Sent by the current user: tinted bubble, row aligned to the end |

Other attributes go to the root `<div>` of the row.

`Chat:Bubble`:

| Prop     | Type    | Default | Description                                            |
| -------- | ------- | ------- | ------------------------------------------------------ |
| `author` | string? | `null`  | Sender name, rendered with `Chat:Bubble:Title`         |
| `date`   | string? | `null`  | Time of the message, rendered with `Chat:Bubble:Title` |
| `text`   | string? | `null`  | Message text, in a `<p>` inside `Chat:Bubble:Body`     |
| `me`     | bool    | `false` | Sent by the current user (`chat-bubble-me`)            |

Other attributes go to the root `<div class="chat-bubble">`.

## Sub-components

| Component            | Renders                                                                                                                                   |
| -------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| `Chat:Bubbles`       | `<div class="chat-bubbles">`: stacks the rows with a gap                                                                                  |
| `Chat:Message`       | `<div>` with a `row`: the avatar column and the bubble column, see its props above                                                        |
| `Chat:Bubble`        | `<div class="chat-bubble">`: one message, see its props above                                                                             |
| `Chat:Bubble:Title`  | `<div class="chat-bubble-title">` with a `row`; `author` and `date` (default `null`)                                                      |
| `Chat:Bubble:Author` | `<div class="col chat-bubble-author">`                                                                                                    |
| `Chat:Bubble:Date`   | `<div class="col-auto chat-bubble-date">`                                                                                                 |
| `Chat:Bubble:Body`   | `<div class="chat-bubble-body">`                                                                                                          |
| `Chat:Typing`        | `<div class="chat-bubble align-self-start">` with the text and `<span class="animated-dots">`; `label` (default `'Typing'`) sets the text |

`Chat:Bubble:Title` renders its `author` and `date` props with `Chat:Bubble:Author` and `Chat:Bubble:Date`; children go
inside its `row` instead.

## Blocks

Blocks of `Chat`:

| Block     | Default                                                                  |
| --------- | ------------------------------------------------------------------------ |
| `content` | `Chat:Bubbles` with a `Chat:Message` per message, when `messages` is set |

Blocks of `Chat:Message`:

| Block     | Default                                                                 |
| --------- | ----------------------------------------------------------------------- |
| `avatar`  | `<span class="avatar">` with the `avatar` image, when set               |
| `content` | `Chat:Bubble` with `author`, `date`, `text` and `me`: the bubble column |

Blocks of `Chat:Bubble`:

| Block     | Default                                                               |
| --------- | --------------------------------------------------------------------- |
| `title`   | `Chat:Bubble:Title` with `author` and `date`, when one of them is set |
| `body`    | `Chat:Bubble:Body` with the `text` prop in a `<p>`, when set          |
| `content` | `title` and `body`: replace it to compose freely                      |

`Chat:Typing` has a `content` block, which defaults to the `label` prop.
