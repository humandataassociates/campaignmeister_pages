---
layout: default
title: docs
permalink: docs
nav_exclude: true
---

# Docs

The site setting are in the `_config.yml`.

```yaml
# Site settings
title: Campaign meister
description: Content for the campaign meister
baseurl: "/campaignmeister_pages" # the subpath of your site, e.g. /blog
url: "https://humandataassociates.github.io" # the base hostname & protocol for your site, e.g. http://example.com

permalink: pretty
exclude: ["Gemfile", "Gemfile.lock","LICENSE.txt", "README.md"]

# Enable or disable the site search
# Support true (default) or false
search_enabled: true

# Heading anchor links appear on hover over h1-h6 tags
# in page content allowing users to deep link to a particular
# heading on a page.
#
# Supprts true (default) or false/nil
heading_anchors: false

# Aux links for the upper right navigation
aux_links:
  "Docs on GitHub":
    - "github.com/humandataassociates/campaignmeister_pages"

# Footer content appears at the bottom of every page's main content
footer_content: "Copyright &copy; 2019 humandataassociates. Distributed by an <a href=\"https://github.com/humandataassociates/campaignmeister_pages/tree/master/LICENSE.txt\">MIT license.</a>"

compress_html:
  clippings: all
  comments: all
  endings: all
  startings: []
  blank_lines: false
  profile: false

# Plugins
plugins:
  - jekyll-feed
  - github-pages

```

## Main navigation

The main navigation of the site is on the left side of the page at large screens.


## Ordering pages

To specify a page order, use the `nav_order` parameter in your pages' YAML front matter.

#### Example

```yaml
---
layout: default
title: Useful Links
nav_order: 5
---
```

---
## Excluding pages

For specific pages that you do not wish to include in the main navigation, e.g. a 404 page or a landing page, use the `nav_exclude: true` parameter in the YAML front matter for that page.

#### Example

```yaml
---
layout: default
title: 404
nav_exclude: true
---
```

---

## Pages with children

Sometimes you will want to create a page with many children (a section). First, it is recommended that you keep pages that are related in a directory together... For example, in these site, we keep all of the written documentation in the `./` root directory and each of the sections in subdirectories like `./the-zen-of-campaign-measurement` and `./using-campaignmeister`. This gives us an organization like:

```
+-- ..
|
|   |-- the-zen-of-campaign-measurement
|   |   |-- the-zen-of-campaign-measurement.md  (parent page)
|   |   |-- what-are-campaign-tags.md
|   |   |-- best-practices-campaign-tagging.md
|   |
|   |-- using-campaignmeister
|   |   |-- using-campaignmeister.md      (parent page)
|   |   |-- setting-up-your-environment.md
|   |   |-- setting-up-a-new-campaign.md
|   |   |-- reviewing-and-updating-an-existing-campaign.md
|   |
|   |-- (other md files, pages with no children)
|
+-- ..
```

On the parent pages, add 2 YAML front matter parameters:
-  `has_children: true` (tells us that this is a parent page)
-  `permalink:` set this to the site directory that contains the child pages

#### Example

```yaml
---
layout: default
title: The Zen of Campaign Measurement
nav_order: 2
has_children: true
permalink: /the-zen-of-campaign-measurement
---
```

Here we're setting up the 'The Zen of Campaign Measurement' landing page that is available at `/the-zen-of-campaign-measurement`, which has children and is ordered second in the main nav.

### Child pages

On child pages, simply set the `parent:` YAML front matter to whatever the parent's page title is and set a nav order (this number is now scoped within the section).

#### Example

```yaml
---
layout: default
title: Why Campaign Measurement
parent: The Zen of Campaign Measurement
nav_order: 2
---
```

The 'Why Campaign Measurement' page appears as a child of 'The Zen of Campaign Measurement' and appears second in the 'The Zen of Campaign Measurement' section.