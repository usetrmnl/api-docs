---
description: Search and sort community plugins.
---

# Recipes API

#### Quickstart

Execute a search at https://usetrmnl.com/recipes, then append JSON to the URL.

```
# search for "weather"
https://usetrmnl.com/recipes?search=weather&sort-by=newest

# in JSON format
https://usetrmnl.com/recipes.json?search=weather&sort-by=newest
```

#### GET /recipes

Provide a query with `search=xxx`, "sort-by" parameter is optional.

Example request: `https://usetrmnl.com/recipes.json?search=weather`

Example response:

```
{
  "data": [{
      "id": 49610,
      "name": "Weather Chum",
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
    }]
  "total": 12,
  "from": 1,
  "to": 12,
  "per_page": 25,
  "current_page": 1,
  "prev_page_url": null,
  "next_page_url": "/recipes?page=2&search=weather&sort_by=popularity"
}
```

#### GET recipes/{id}

Fetch a single plugin by ID.&#x20;

Example request: `https://usetrmnl.com/recipes/16382.json`

Example response:

```
{
  "data": {
    "id": 16382,
    "name": "Matrix",
    "icon_url": "https://trmnl-public.s3.us-east-2.amazonaws.com/mtpxyr22spnwjheeh5kv1p7tpk6n",
    "screenshot_url": "https://trmnl.s3.us-east-2.amazonaws.com/jly9u094jtsc2bwmnhlnmwjnsokk?response-content-disposition=inline%3B%20filename%3D%22plugin-2025-04-10T12-47-23Z-776f51%22%3B%20filename%2A%3DUTF-8%27%27plugin-2025-04-10T12-47-23Z-776f51&response-content-type=image%2Fbmp&X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIA47CRUQUU4VKBBMOF%2F20251024%2Fus-east-2%2Fs3%2Faws4_request&X-Amz-Date=20251024T210933Z&X-Amz-Expires=300&X-Amz-SignedHeaders=host&X-Amz-Signature=828e75fc333464c3ba13654c70434d307a8ca48053cd102f4a10a55e953c3ce2",
    "author_bio": {
      "keyname": "doesnt_matter",
      "name": "About This Plugin",
      "field_type": "author_bio",
      "description": "Matrix brings the iconic digital rain from the movies to your screen. By default, it displays the current date in the classic style, but you can also customize it to show any message you want."
    },
    "custom_fields": [
      {
        "keyname": "doesnt_matter",
        "name": "About This Plugin",
        "field_type": "author_bio",
        "description": "Matrix brings the iconic digital rain from the movies to your screen. By default, it displays the current date in the classic style, but you can also customize it to show any message you want."
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
