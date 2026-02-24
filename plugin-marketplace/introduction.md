---
description: TRMNL's plugin marketplace lets anyone publish and share their work.
---

# Introduction

Our plugin marketplace is where developers can make plugins for other users to install. Since November 2025 [TRMNL pays developers](https://trmnl.com/blog/creator-fund) for their work.

There are 2 approaches to publishing plugins for other users — Recipe, or Third Party. Review the differences between them before continuing:

{% embed url="https://help.trmnl.com/en/articles/10546870-compare-custom-plugin-types" %}

**Recipes** live inside TRMNL and do not require 3rd party dependencies, user auth, etc. This is our recommended path for plugin development. You can provide [custom form fields](https://help.trmnl.com/en/articles/10513740-custom-plugin-form-builder), monitor [usage analytics](https://trmnl.com/blog/plugin-analytics), and optionally middleman with your own services for even more control. Browse 100s of published Recipes [here](https://trmnl.com/recipes), or start building [here](https://help.trmnl.com/en/articles/9510536-private-plugins).

**Third Party plugins** require a simplified OAuth2 flow with TRMNL. In this scenario, the plugin author (you) maintains user PII and is responsible for data privacy and security. TRMNL fetches markup from your server at regular intervals and generates images for the connected user's device. To build a Third Party plugin, continue reading this guide. Or browse native + third party plugins [here](https://trmnl.com/integrations).
