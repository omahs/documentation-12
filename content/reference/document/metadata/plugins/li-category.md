---
title: li-category
type: metadata-plugins
menus:
  reference:
    parent: Metadata Plugins List
summary: Single category selection.
support:
  document: true
  media: false
  tableDashboard: true
  include: false
  displayFilter: true
  dynamicIndexing: true
  systemMetadata: false
  planningSystem: false
defaultUI: Select input, with category tree view and search
storageFormat: |
  {
    id: <String>,
    path: <String>
  }
contentTypeConfig: |2
        handle: 'myHandle',
        type: 'li-category',
        config: {
          index: true         // optional, default: false. {{< added-in "release-2023-07" >}}
        }
---
