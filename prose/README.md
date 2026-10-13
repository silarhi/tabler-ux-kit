# Prose

Styles freeform HTML you do not control the markup of: rendered Markdown, CMS content, release notes.

```twig {"preview":true}
<twig:Tabler:Prose>
    <h2>Release notes</h2>
    <p>Version <strong>2.4.0</strong> adds invoice exports and fixes a few bugs.</p>
    <h3>New</h3>
    <ul>
        <li>Export invoices as CSV or PDF.</li>
        <li>Filter deployments by environment.</li>
    </ul>
    <blockquote>Exports run in the background: you get an email when the file is ready.</blockquote>
    <p>Run the migration before upgrading: <code>php bin/console doctrine:migrations:migrate</code>.</p>
</twig:Tabler:Prose>
```

## Installation

::: installation

## Rendered Markdown

Pass the HTML with the `raw` filter. Only do this with HTML you trust or have sanitized:

```twig
<twig:Tabler:Prose>{{ article.html|raw }}</twig:Tabler:Prose>
```

## Props

`Prose` has no props: attributes go to the root `<div class="prose">`.
