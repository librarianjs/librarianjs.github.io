---
layout: page
title: Configuration
permalink: /configuration
---

You can integrate librarian with your particular tech stack with plugins.

{% highlight javascript %}
const librarian = require('librarian')
const S3Storage = require('librarian-s3-storage')
const MysqlData = require('librarian-mysql-data')
const MemoryCache = require('librarian-memory-cache')

librarian({
  storage: new S3Storage({ ... }),
  data: new MysqlData({ ... }),
  cache: new MemoryCache({ ... }),
}).listen(8888)
{% endhighlight %}

See [plugins](/plugins) for more details.

## Cross Origin Requests

Any `cors` option you provide will be passed directly into the [cors](https://www.npmjs.com/package/cors) module.
If you leave this option out, CORS will not be used.

{% highlight javascript %}
const librarian = require('librarian')

librarian({
  cors: ['GET', 'POST']
}).listen(8888)
{% endhighlight %}
