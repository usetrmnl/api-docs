---
description: Valid plugin categories to increase search exposure.
---

# Categories API

When developing a Public or Recipe style plugin, you may add indexed categories to improve visibility in search results.

[https://trmnl.com/api/categories](https://trmnl.com/api/categories)

```json
{ "data": ["album", "analytics", "art", "calendar", ..., "sports", "travel"] }
```

Categories live on your plugin's `author_bio` [custom field](https://help.trmnl.com/en/articles/10513740-custom-plugin-form-builder) as a comma-separated `category` key:

```yaml
- keyname: about
  field_type: author_bio
  name: About This Plugin
  category: calendar,life
```

**A recipe submission without a category is sent back for changes.** Once published, anyone can filter by category on [Recipes](https://trmnl.com/recipes) or the [Recipes API](recipes-api.md) with `search=%23calendar` (`#` URL-encoded).

{% hint style="info" %}
Recipes in the `morbid` category are hidden from search results unless someone searches `#morbid` directly.
{% endhint %}
