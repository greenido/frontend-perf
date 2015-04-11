# Performance: why and how?

## Why care about Performance?

* Fast sites convert better.
* Fast sites make users happier.
* Fast sites serve more pageloads, thus things like ads.
* Fast sites are cheaper — for both hosting and mobile data plans.

## Fundamentals of Performance

> Many facets of performance are improving over time. One such change is
> HTTP/2, and it will cause sweeping changes to the layers above. Some of
> the current optimizations that are a good idea now will actually *hurt*
> your site's performance using HTTP/2. We will mark any potential regressions
> so you can keep the future in mind.

### HTTP/1.1

**Concatenate, minify, compress, shard.**

**Concatenation** means to combine several assets into one asset. When Drupal combines multiple stylesheets into an aggregate, that is concatenation.

**Minifaction** is when all unimportant information is removed from a file. This typically means all whitespace and line-breaks are removed. Generous use of whitespace is required to maintain organized files, but the typical user never looks at your files.

**Compression** is when your server zips up an asset before sending it to the browser. In most cases it is more efficient to zip the asset, send the smaller verion, and unzip it in the browser, rather than transferring the uncompressed asset over the internet.

**Domain sharding** is when you set up multiple subdomains in order to "trick" the browser into opening more HTTP connections to a single website. Typically you'll see a domain that has several subdomains: css.example.com, js.example.com etc. Since a browser will only open a certain number of HTTP connections to a single host, domain sharding allows for more simultaneous connections to your server.

### HTTP/2

**Ignore all the above advice.**

Using HTTP/2, the server and browser can more efficiently use the connection they create between each other, and multiple files can be sent using one single connection. Thus, the gain achieved by concatenating when using HTTP1.1 is now a **restriction** that the server has no choice but to obey when using HTTP2.

HTTP/2 was created to address all of the performance workarounds described in the HTTP/1.1 section. So if your server is using the newer protocol, none of those workarounds are necessary.