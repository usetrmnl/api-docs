---
description: Search and sort community plugins.
---

# Recipes API

### Quickstart

Execute a search at https://trmnl.com/recipes, then append JSON to the URL.

```
# search for "weather"
https://trmnl.com/recipes?search=weather&sort-by=newest

# in JSON format
https://trmnl.com/recipes.json?search=weather&sort-by=newest
```

### List Recipes

<mark style="color:green;">`GET`</mark> `/recipes.json`

Returns published recipes only. Unlisted recipes stay out of the list, but you can still fetch one by ID (below).

{% hint style="info" %}
Need more than read access -- recipe markup, or installing a recipe on your account? Use the authenticated [`/api/recipes`](https://trmnl.com/api-docs) endpoints instead.
{% endhint %}

**Example Request**\
`https://trmnl.com/recipes.json?sort-by=install`

**Query Params**

All are optional.

<table><thead><tr><th width="194.3828125">Name</th><th width="180.94921875">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>search</code></td><td>string</td><td>Full-text search. Partial words OK, plus small typos in the name. Ignored under 3 characters. Prefix with <code>#</code> to filter by <a href="categories-api.md">category</a>, URL-encoded as <code>%23calendar</code></td></tr><tr><td><code>sort-by</code></td><td>string</td><td>Option by which to rank results (default <code>newest</code>)</td></tr><tr><td><code>user_id</code></td><td>integer</td><td>ID of the author, e.g. 51</td></tr><tr><td><code>per_page</code></td><td>integer</td><td>Results count (maximum 100, default 25)</td></tr><tr><td><code>page</code></td><td>integer</td><td>Page number (default 1)</td></tr></tbody></table>

Valid `sort-by` options:

* oldest
* newest
* popularity (installs + forks)
* fork
* install

Searches are limited to 60 requests per minute per IP address. Past that you'll get a `429`.

**Example Response**

{% tabs %}
{% tab title="200" %}
```json
{
  "data": [{
      "id": 49610,
      "user_id": 1158,
      "name": "Weather Chum",
      "description": "Todays weather, hourly and forecast",
      "published_at": "2025-05-14T05:32:00.000Z",
      "icon_url": "https://trmnl-public.s3.us-east-2.amazonaws.com/ajjlbek4cabcvhk3s1lxggn8cgon",
      "icon_content_type": "image/png",
      "screenshot_url": "https://trmnl-public.s3.us-east-2.amazonaws.com/kh7q90o1biy072d2et0u7t3qf8km",
      "author_bio": null,
      "custom_fields": [
        {
          "keyname": "user_location",
          "field_type": "string",
          "name": "Weather Location",
          "placeholder": "New York, NY",
          "description": "Choose a location",
          "help_text": "Please be precise. Examples: \u003C/br\u003E Paris, France (City/country) \u003C/br\u003E 10101 (Pass US Zipcode, UK Postcode, Canada Postal code)\u003C/br\u003E 33.7501,84.3885 (Lat/long)\u003C/br\u003E",
          "required": true
        },
        {
          "keyname": "metric",
          "name": "Temperature Metric",
          "description": "Celsius or Fahrenheit?",
          "field_type": "select",
          "options": [
            "Fahrenheit",
            "Celsius"
          ],
          "default": "Fahrenheit"
        }
      ],
      "stats": {
        "installs": 1102,
        "forks": 383
      }
  }],
  "total": 38,
  "from": 1,
  "to": 25,
  "per_page": 25,
  "current_page": 1,
  "prev_page_url": null,
  "next_page_url": "/recipes.json?page=2&per_page=25&search=weather&sort-by=popularity"
}
```
{% endtab %}
{% endtabs %}

`author_bio` is the recipe's `author_bio` custom field, repeated at the top level for convenience (`null` when the recipe has none). `stats` counts `installs` + `forks` of the recipe.

### Get a single Recipe

<mark style="color:green;">`GET`</mark> `/recipes/{id}.json`

Works for published + unlisted recipes. An unknown ID redirects (`302`) to `/recipes` instead of returning a `404`.

**Example Request**\
`https://trmnl.com/recipes/16382.json`

**Example Response**

{% tabs %}
{% tab title="200" %}
```json
{
  "data": {
    "id": 16382,
    "user_id": 934,
    "name": "Matrix",
    "description": "The Digital Rain",
    "published_at": "2025-02-10T11:33:00.000Z",
    "icon_url": "https://trmnl-public.s3.us-east-2.amazonaws.com/mtpxyr22spnwjheeh5kv1p7tpk6n",
    "icon_content_type": "image/png",
    "screenshot_url": "https://trmnl-public.s3.us-east-2.amazonaws.com/7i54we946jo1uhiq4y29dqwdtxgm",
    "author_bio": {
      "keyname": "doesnt_matter",
      "name": "About This Plugin",
      "field_type": "author_bio",
      "description": "Matrix brings the iconic digital rain from the movies to your screen. By default, it displays the current date in the classic style, but you can also customize it to show any message you want.",
      "category": "calendar,life"
    },
    "custom_fields": [
      {
        "keyname": "doesnt_matter",
        "name": "About This Plugin",
        "field_type": "author_bio",
        "description": "Matrix brings the iconic digital rain from the movies to your screen. By default, it displays the current date in the classic style, but you can also customize it to show any message you want.",
        "category": "calendar,life"
      },
      {
        "keyname": "message",
        "field_type": "string",
        "name": "Message",
        "default": "%date",
        "help_text": "%date to display current date"
      }
    ],
    "stats": {
      "installs": 285,
      "forks": 37
    }
  }
}
```
{% endtab %}
{% endtabs %}
