# Working with content adapters in Hugo

This demo shows how to use Hugo’s [Content Adapters](https://gohugo.io/content-management/content-adapters/) to dynamically build pages from remote data sources, such as JSON files and CSV data from Google Sheet.

## Prerequisites

You will need [Hugo](https://gohugo.io/) version 0.126.0 or higher installed locally.


## Installation

Clone this repository:

```
git clone https://github.com/harrycresswell/content-adapters.git

```

## Local development

To start a local development server at at https://localhost:1313/ run:

```
hugo server
```

## Getting started

Head to `content/books/_content.gotmpl` to find [Hugo’s content adapter example](https://gohugo.io/content-management/content-adapters/#example) as seen in the Hugo docs. This example takes remote JSON data and creates pages for a collection of books. You can see these books by navigating to /books in a browser.

Head to `content/locations/_content.gotmpl` to find a content adapter template used to generate pages from Google Sheets data, as explained in [dynamically generate pages from Google Sheets using Hugo’s Content Adapters](/). I recommend reading this post to get a better understanding of what this content adapter is doing and how it generates pages.

`themes/starter/layouts/locations/single.html` is the layout template used to display the content on the generated pages.

[Generating Hugo pages from Google Sheets data](https://docs.google.com/spreadsheets/d/11uVKGlWucpT31cc_by595yOaNSW_qpa4B1mTvP8nW5k/edit?usp=sharing) is the sheet used as the data source.

The sheet needs to published to the web in .CSV format for Hugo to have access to the data. To do this, open a copy of the sheet, then head to **File > Share > Publish to web**. Then under the **Link** tab, make sure **Entire Document** is set to *Comma-separated values (.csv)*.

If you are adapting this demo by using your own sheet, then you will have to update the value of `$url` inside `content/locations/_content.gotmpl` with the URL from your sheet that Google provides.


## Production build

Whe your ready to build a production ready site, update the baseUrl inside config.toml then run:

```
hugo --cleanDestinationDir
```

This will clean the `/public` folder and run a fresh build ready for production.


## Licence

MIT