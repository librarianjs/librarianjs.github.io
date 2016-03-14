---
layout: default
---
# Getting Started

## Installation

{% highlight bash %}
$ npm install librarian
{% endhighlight %}

## Server Usage

{% highlight javascript %}
const librarian = require('librarian')
let app = librarian()
app.listen(8888)
{% endhighlight %}

See [configuration](/configuration) for more options.

## Client Usage

### Request JS

{% highlight javascript %}
const request = require('request')
const fs = require('fs')
const request = require('request')

let fileStream = fs.createReadStream(__dirname + '/test-image.png')
fileStream.pipe(request.post('http://localhost:8888'))
{% endhighlight %}

### Browser Form

{% highlight html %}
<form method="POST" action="http://localhost:8888" enctype="multipart/form-data">
  <input type="file" name="file">
  <button type="submit">Upload</button>
</form>
{% endhighlight %}
