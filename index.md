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

## POST Response

{% highlight json %}
{
  "id": "e10a0a08-1688-4dff-8a26-fea6ff32e2d4",
  "size": 125731,
  "name": "test-image.png",
  "mimeType": "image/jpeg"
}
{% endhighlight %}

## Image Retrieval

### Browser

{% highlight html %}
<!-- normal -->
<img src="http://localhost:8888/e10a0a08-1688-4dff-8a26-fea6ff32e2d4">

<!-- resized -->
<img src="http://localhost:8888/e10a0a08-1688-4dff-8a26-fea6ff32e2d4?width=50">

<!-- resized -->
<img src="http://localhost:8888/e10a0a08-1688-4dff-8a26-fea6ff32e2d4?height=50">

<!-- resized -->
<img src="http://localhost:8888/e10a0a08-1688-4dff-8a26-fea6ff32e2d4?max=50">

{% endhighlight %}

### RequestJS

{% highlight javascript %}
const request = require('request')
const fs = require('fs')

let fileStream = fs.createWriteStream(__dirname + '/test-image.png')
request
  .post('http://localhost:8888/e10a0a08-1688-4dff-8a26-fea6ff32e2d4')
  .post(fileStream)
{% endhighlight %}
