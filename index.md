---
title: Welcome to http2benchmark.org
---

As more and more sites switch to HTTPS, and more servers add HTTP/2 support, it can be difficult to determine which server has the best performance. This site aims to settle that question.

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

## Benchmark Setup

[You can easily run http2benchmark on your own server by following this guide.](https://http2benchmark.org/guide.html)

### Server software compared

*   [Apache 2.4](http://httpd.apache.org/)
*   [LiteSpeed Enterprise 5.4](https://www.litespeedtech.com/products/litespeed-web-server)
*   [Nginx 1.6](http://nginx.org/)

### Server software to be added soon

*   [Caddy](https://caddyserver.com/)
*   [H2O](https://h2o.examp1e.net/)
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
    *   [W3 Total Cache](https://wordpress.org/plugins/w3-total-cache/) for Apache
    *   FastCGI Cache for Nginx

## Benchmark Results

###   Digital Ocean Droplet 1
    * Date: 07/23/2019
    * Server: 1GB memory, 1-core Intel(R) Xeon(R) CPU E5-2650 v4 @ 2.20GHz
    * Client: 2GB memory , 1-core Intel(R) Xeon(R) Gold 6140 CPU @ 2.30GHz
    * Network Bandwidth: 1.8Gbps

#### LSWS 5.4 vs Nginx 1.16 HTTP/2 

Command: `h2load -n 100000 -c 100 -m 10 -H "Accept-encoding: gzip, deflate" https://<IP>/1kstatic.html`

Test Name | LSWS 5.4    | Nginx 1.16 | Ratio
----------|------------ | -------------|------
1kstatic.html (req/s) | 156422.00 | 18734.10| 8.35
1knogzip.jpg (req/s) | 132162.00 | 27898.10| 4.73
wordpress homepage (req/s) | 36089.90 | 3597.00 | 10.03

#### LSWS 5.4 vs Nginx 1.16 HTTPS 

Command: `wrk -d 5 -c 100 -H "Accept-encoding: gzip, deflate" https://<IP>/1kstatic.html`

Test Name | LSWS 5.4    | Nginx 1.16 | Ratio
----------|------------ | -------------|------
1kstatic.html (req/s) | 41794.80 | 15580.20 | 2.68
1knogzip.jpg (req/s) | 40326.40 | 21976.70 | 1.83
wordpress homepage (req/s) | 16414.00 | 3410.70 | 4.81

###   Vultr “High Frequency Compute”
    * Date: 07/23/2019
    * Server: 2GB memory, 1-core 3GHz+ CPUs ( 3792MHz )
    * Client: 2GB memory, 1-core 3GHz+ CPUs ( 3792MHz )
    * Network Bandwidth: 7.7Gbps

#### LSWS 5.4 vs Nginx 1.16 HTTP/2 

Command: `h2load -n 100000 -c 100 -m 10 -H "Accept-encoding: gzip, deflate" https://<IP>/1kstatic.html`

Test Name | LSWS 5.4    | Nginx 1.16 | Ratio
----------|------------ | -------------|------
1kstatic.html (req/s) | 212222.00 | 33909.20| 6.26
1knogzip.jpg (req/s) | 203938.00 | 45258.70| 4.50

#### LSWS 5.4 vs Nginx 1.16 HTTPS 

Command: `wrk -d 5 -c 100 -H "Accept-encoding: gzip, deflate" https://<IP>/1kstatic.html`

Test Name | LSWS 5.4    | Nginx 1.16 | Ratio
----------|------------ | -------------|------
1kstatic.html (req/s) | 78968.90 | 25513.00 | 3.09
1knogzip.jpg (req/s) | 66455.80 | 37813.80 | 1.75

## Feedback

