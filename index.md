---
title: Truth About HTTP/2 Performance
---

As more and more sites switch to HTTPS, and more servers add HTTP/2 support, it can be difficult to determine which server has the best performance. This site aims to settle that question.

## Benchmark result summary

### Apache vs Caddy vs H2o vs LiteSpeed vs Nginx
Benchmark test results as of September 6, 2019, conducted on Digital Ocean 1GB droplets.

#### WordPress Home Page (HTTP/2)
All server setups use best available WordPress cache plugin.

  Server Name   | Requests/sec | Ratio | 
----------------|-------------:|:-----:
Apache 2.4.41   |    389.40    |  1.00X
Caddy 0.11.4    |    441.00    |  1.13X
H2o 2.2.6       |    721.90    |  1.85X
LiteSpeed 5.4.1 |  29159.00    |  **74.95X**
Nginx 1.16.1    |   3324.40    |  8.53X

### WordPress Home Page (HTTP/2 vs HTTP/1.1)
Compare HTTP/2 and HTTP/1.1 (with Keep-alive connections)

  Server Name   |    HTTP/2    | HTTP/1.1   |  HTTP/2 vs HTTP/1.1   |
----------------|-------------:|-----------:|:---------------------:
Apache 2.4.41   |    389.40    |  476.72    |         0.81X
Caddy 0.11.4    |    441.00    |  433.36    |         1.02X
H2o 2.2.6       |    721.90    |  621.08    |         1.16X
LiteSpeed 5.4.1 |  29159.00    |  14290.00  |       **2.04X**
Nginx 1.16.1    |   3324.40    |  3201.17   |         1.04X

[Benchmark Result: Apache vs Caddy vs H2o vs LiteSpeed vs Nginx in DigitalOcean 1GB droplet](https://http2benchmark.org/results/benchmark-apache-caddy-h2o-litespeed-nginx-digitalocean.html)

## Methodology

We provide an easy-to-use script so that you may set up and run the benchmarks yourself. If you don’t believe the published results, you can verify them on your own server.

### How benchmarking is performed

*   Micro benchmarks are included, to show the fundamental performance attributes of each server.
*   Real-world web application benchmarks illustrate what is possible.
*   Test clients send requests with an “`Accept-encoding: gzip`” header, to more closely simulate real browsers.

### How can you contribute

The [http2benchmark](https://github.com/http2benchmark/http2benchmark) project is an open-source project hosted on GitHub. 

Contributions are welcome, including:

*   Suggestions for other server software that should be covered
*   Submissions for a configuration tuning that you think would get better results
*   Recommendations for additional test cases
*   Your own test results to share

Give your feedback in the [project’s Issues](https://github.com/http2benchmark/http2benchmark/issues) area or create a [Pull Request](https://github.com/http2benchmark/http2benchmark/pulls), and add any of the following: 

*   Server setup scripts and configurations
*   Server configuration tunings
*   Your benchmark results

## How to to run your own benchmark

[You can easily run http2benchmark on your own server by following this guide.](https://http2benchmark.org/guide.html)

    It takes less than an hour of two $5 Digital Ocean droplets to verify the test results.
    Total cost is less than $0.02. Give it a try. :-) 

### Server software compared

*   [Apache](http://httpd.apache.org/) with W3TC cache for WordPress
*   [Caddy](https://caddyserver.com/) with W3TC cache for WordPress
*   [H2O](https://h2o.examp1e.net/) with W3TC cache for WordPress
*   [LiteSpeed Enterprise](https://www.litespeedtech.com/products/litespeed-web-server)
    with Litespeed Cache for WordPress
*   [Nginx](http://nginx.org/)
    with FastCGI cache for WordPress

### Server software to be added soon

*   [OpenLiteSpeed](https://openlitespeed.org/)

### Test clients used

*   [h2load](https://nghttp2.org/documentation/h2load-howto.html) for benchmarking HTTP/2
*   [wrk](https://github.com/wg/wrk) for benchmarking regular HTTPS in the HTTP/1.1 protocol

### Micro benchmarks

1. Small static HTML file that can be compressed
2. Small static image files that cannot be compressed.

### Application benchmark

*   [WordPress](https://wordpress.org/) with cache plugin: 
    *   [LSCache](https://wordpress.org/plugins/litespeed-cache/) for LiteSpeed
    *   [W3 Total Cache](https://wordpress.org/plugins/w3-total-cache/) for Apache, Caddy and H2o
    *   FastCGI Cache for Nginx

## Benchmark Results

###  [Apache vs Caddy vs H2o vs LiteSpeed vs Nginx in DigitalOcean 1GB droplet](https://http2benchmark.org/results/benchmark-apache-caddy-h2o-litespeed-nginx-digitalocean.html) September 6, 2019

###  [LiteSpeed 5.4 vs Nginx 1.16 in DigitalOcean 1GB Droplet](https://http2benchmark.org/results/nginx-vs-litespeed-digitalocean.html) July 23, 2019
 
###  [LiteSpeed 5.4 vs Nginx 1.16 in Vultr “High Frequency Compute” 2-GB instance](https://http2benchmark.org/results/nginx-vs-litespeed-vultr.html)  July 23, 2019

## Feedback

