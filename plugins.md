---
layout: page
title: Plugins
permalink: /plugins
---

## Data Plugins

Data plugins store information about an upload file.

- id
- size
- name
- mimeType

The default data plugin is [in memory storage](https://github.com/librarianjs/memory-data).
This is not appropriate for production data, as a server restart will wipe all data away.

### Available Options

- ✔ [In Memory](https://github.com/librarianjs/memory-data) (default)
- ✔ [MySQL](https://github.com/librarianjs/mysql-data)
- ✘ PostreSQL ([Help Develop](/creating-a-data-plugin))
- ✘ MongoDB ([Help Develop](/creating-a-data-plugin))

## Storage Plugins

Storage plugins handle the raw binary storage of the file.

The default storage plugin is [in memory storage](https://github.com/librarianjs/memory-storage).
This is not appropriate for production data, as a server restart will wipe all data away.

### Available Options

- ✔ [In Memory](https://github.com/librarianjs/memory-storage) (default)
- ✔ [Amazon S3](https://github.com/librarianjs/s3-storage)
- ✔ [File System](https://github.com/librarianjs/fs-storage)
- ✘ Google Cloud ([Help Develop](/creating-a-storage-plugin))
- ✘ MySQL ([Help Develop](/creating-a-storage-plugin))

## Cache Plugins

- ✔ None (default)
- ✔ [In Memory](https://github.com/librarianjs/memory-cache)
- ✘ Redis ([Help Develop](/creating-a-cache-plugin))
- ✘ File System ([Help Develop](/creating-a-cache-plugin))


Cache plugins are very similar to storage plugins, but the files they store expire eventually. The cache restriction (time, limited space, etc) is implementation specific.

There is no cache plugin by default, so files will be read directly from storage every time. This is the only type of plugin where an [in memory version](https://github.com/librarianjs/memory-storage) can be appropriate for production data in some scenarios.
