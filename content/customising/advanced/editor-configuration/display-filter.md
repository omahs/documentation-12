---
title: Display Filter
---

Display Filters are filters with a UI. They are configurable per dashboard and allow the user to define what should be shown in the result list.

There are 3 types of Display Filters: `listV2`, `metadataPropertyName` and `customVueComponent`.
Some Display Filters are provided by Livingdocs and can be configured without additional code. It is possible though to provide your own custom filters, [there is a guide]({{< ref "/guides/editor/custom-dashboard-filters" >}}) explaining the details.

Usually you configure `displayFilters` in dashboard configurations like this:

```js
{
  handle: "myDashboard",
  displayFilters: [
    // shorthand for {filterName: "aFilterName"}
    "aFilterName",

    // some filters take a config object
    {
      filterName: "anotherFilterName",
      config: {
        some: "configToPass"
       }
    },

    // gives you a filter for this metadata property, caveats apply, see below. {{< added-in "release-2023-03" >}}
    {metadataPropertyName: "myMetadataProperty"}
  ],
  // ...
}

```

There are 2 types of filters provided by Livingdocs for you to configure, some you define by `filterName`, some by `metadataPropertyName`.
They are separately listed here:

## Named Filters

- `documentState`, unpublished, published, not yet published, my articles, needs proofreading, currently proofreading
- `timeRange`, filter the search results in time ranges such as last 24 hours
- `liDateTimeRange`, filter the search results in time ranges (quick filter + from/to range)
  ```js
  // simple config - filters by updatedAt
  displayFilters: ['liDateTimeRange']

  // custom config
  //   documentPropertyName: Supports 'createdAt'/'updatedAt', defaults to updatedAt
  //   metadataPropertyName: Supports any of your metadata date fields
  displayFilters: [{filterName: 'liDateTimeRange', config: {documentPropertyName: 'createdAt'}}]
  displayFilters: [{filterName: 'liDateTimeRange', config: {metadataPropertyName: 'publicationDate'}}]
  ```
- `sortBy`: `relevance` (default), `creation_date`, `updated_at`, `alphabetical`
- `language`: uses the project configuration for [available languages]({{< ref "/reference/project-config/settings.md" >}}) to offer a select box to filter for languages (requires multi-language feature to be enabled)
- `contentType`: uses the content-types configuration in your server to filter for different content-types, e.g. galleries or regular articles.
- `channels` give the user a dropdown to filter by a specific channel. The concept of channels will be removed, if you aren't using them yet, don't start doing so.

## Metadata Filters

{{< added-in "release-2023-03" block >}}

Listed here are the supported metadata types, you would configure the filters for them with a `metadataPropertyName` with the `handle` of a property of this type that is configured in your `contentType`s/`mediaType`s.
Support for more types will be added as needed. Contact your Customer Solutions Manager for potential [Implementation Partnerships](https://livingdocs.io/en/livingdocs-2022-2023-roadmap).
### Supported Types

- `li-integer`
- `li-category`
