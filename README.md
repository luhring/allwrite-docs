# eggplant

Writing in Google Drive is enjoyable. When something is enjoyable, we tend to do it more often and with better quality.

This API connects with your Google Drive and provides endpoints which returns the pages within Drive in a organized and usable format. With these endpoints, beautiful (or not) user interfaces can be created.

This is not a SaaS product and 100% open source. You just need to host it yourself.

# Table of Contents

* [How it works](#how-it-works)
* [API](#api)

## How it works

Within the folder specified in the configuration file, you simply need to create pages and folders. Pages can have children infinitely deep by using directories. Files and folders are both made public and ordered by using a special format in their page name:

```
|n| Page Title
```

The number between the two pipes (`n`) is what the menu is sorted by. It can be any number. If a page or directory does not have this format, it will not be public. This is useful when writing pages that should not yet be public.

## API

`GET /menu` Returns an array of page fragments.

```json
[
  {
    "name": "Getting Start",
    "slug": "getting-started",
    "updated": 1500057521,
    "children": []
  },
  {
    "name": "Configure",
    "slug": false,
    "updated": 1500057521,
    "children": [
      {
        "name": "Hello World",
        "slug": "configure/hello-world",
        "updated": 1500057521,
        "children": false
      }
    ]
  }
]
```

`GET /page(/:slug)` Pull a page based on its slug. If not provided, `|0|` page will be used.

```json
{
  "name": "Configure",
  "slug": "configure",
  "updated": 1500057521,
  "html": "<html here>",
  "md": "<markdown here>",
  "children": [
    {
      "name": "Hello World",
      "slug": "configure/hello-world",
      "updated": 1500057521,
      "children": false
     }
  ]
}
```
