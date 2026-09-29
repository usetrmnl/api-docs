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

Leave a layout empty and we render the shared markup on its own for that layout -- handy if you'd rather write one responsive template than four. Shared markup is `markup_shared` in the [API](https://trmnl.com/api-docs) and `shared.liquid` in a plugin archive.

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

Template names may only contain letters, numbers, underscores + slashes (e.g. `components/header`). Like any `{% render %}`, a template only sees the variables you pass in, so hand it what it needs: `{% render "say_hello", name: trmnl.user.first_name %}`.
