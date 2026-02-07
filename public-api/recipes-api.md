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

This endpoint is in alpha testing and may be moved (to `/api/recipes`) or changed (to `/api/plugins`) before the end of 2025.

**Example Request**\
`https://trmnl.com/recipes.json?sort-by=install`

**Query Params**

All are optional.

<table><thead><tr><th width="194.3828125">Name</th><th width="180.94921875">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>search</code></td><td>string</td><td>Name of the plugin (partial match OK)</td></tr><tr><td><code>sort-by</code></td><td>string</td><td>Option by which to rank results</td></tr><tr><td><code>user_id</code></td><td>integer</td><td>ID of the author, e.g. 51</td></tr><tr><td><code>per_page</code></td><td>integer</td><td>Results count (maximum 100, default 25)</td></tr></tbody></table>

Valid `sort-by` options:

* oldest
* newest
* popularity
* fork
* install

**Example Response**

{% tabs %}
{% tab title="200" %}
```json
{
  "data": [{
      "id": 49610,
      "user_id": 1158,
      "name": "Weather Chum",
      "published_at": "2025-05-14T05:32:00.000Z",
      "icon_url": "https://trmnl-public.s3.us-east-2.amazonaws.com/ajjlbek4cabcvhk3s1lxggn8cgon",
      "screenshot_url": "https://trmnl.s3.us-east-2.amazonaws.com/qv5d2r4hg4gxe0tnwhiatdfhuqzj?response-content-disposition=inline%3B%20filename%3D%22plugin-2025-04-30T19-47-15Z-21f687%22%3B%20filename%2A%3DUTF-8%27%27plugin-2025-04-30T19-47-15Z-21f687&response-content-type=image%2Fpng&X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIA47CRUQUU4VKBBMOF%2F20251024%2Fus-east-2%2Fs3%2Faws4_request&X-Amz-Date=20251024T210603Z&X-Amz-Expires=300&X-Amz-SignedHeaders=host&X-Amz-Signature=c5795146177d7f539b0743890018338b8a9d7188d685d1e54dde83d842eb404d",
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
        "installs": 1,
        "forks": 1230
      }
  }],
  "total": 12,
  "from": 1,
  "to": 12,
  "per_page": 25,
  "current_page": 1,
  "prev_page_url": null,
  "next_page_url": "/recipes?page=2&search=weather&sort_by=popularity"
}
```
{% endtab %}
{% endtabs %}

### Get a single Recipe

<mark style="color:green;">`GET`</mark> `/recipes/{id}.json`

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
    "published_at":"2025-02-10T11:33:00.000Z",
    "icon_url": "https://trmnl-public.s3.us-east-2.amazonaws.com/mtpxyr22spnwjheeh5kv1p7tpk6n",
    "screenshot_url": "https://trmnl.s3.us-east-2.amazonaws.com/jly9u094jtsc2bwmnhlnmwjnsokk?response-content-disposition=inline%3B%20filename%3D%22plugin-2025-04-10T12-47-23Z-776f51%22%3B%20filename%2A%3DUTF-8%27%27plugin-2025-04-10T12-47-23Z-776f51&response-content-type=image%2Fbmp&X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIA47CRUQUU4VKBBMOF%2F20251024%2Fus-east-2%2Fs3%2Faws4_request&X-Amz-Date=20251024T210933Z&X-Amz-Expires=300&X-Amz-SignedHeaders=host&X-Amz-Signature=828e75fc333464c3ba13654c70434d307a8ca48053cd102f4a10a55e953c3ce2",
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
      "installs": 25,
      "forks": 176
    }
  }
}
```
{% endtab %}
{% endtabs %}
