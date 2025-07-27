---
description: Keep yourself DRY!
---

# Reusing Markup

Each private plugin has a place to store **Shared** markup.&#x20;

Under the hood, the implementation is simple: **shared markup is prepended to every view layout before rendering**.

This makes it a great place to define common JS and CSS resources without having to copy-and-paste them between every layout.

```liquid
<!-- shared markup -->
<style>
.shout { text-transform: uppercase; }
</style>

<!-- view markup -->
<span class="shout">Brawndo! It's got what plants crave!</span>
```

### Reusable Liquid Templates

You can also define custom Liquid templates (or "partials", or "components" – pick your favorite terminology) to reuse chunks of markup in any view layout.

Our Liquid implementation provides a new tag, `{% template [name] %}` , which works together with the standard  `{% render %}` tag so that templates can be both defined and used within the same context.

```liquid
<!-- shared markup -->
{% template say_hello %}
Hello there, {{ name }}.
{% endtemplate %}

<!-- view markup -->
{% render "say_hello", name: "General Kenobi" %}
```
