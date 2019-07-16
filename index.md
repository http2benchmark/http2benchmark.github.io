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

The [HTTP2Benchmark](https://github.com/http2benchmark/http2benchmark) project is an open-source project hosted on GitHub. 

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

### Server software compared

*   Apache 2.4
*   LiteSpeed Enterprise 5.4
*   Nginx 1.6

### Server software to be added soon

*   Caddy
*   H2O
*   OpenLiteSpeed

### Test clients used

*   H2load for benchmarking HTTP2
*   Wrk for benchmarking regular HTTPS in the HTTP/1.1 protocol

### Micro benchmarks

1. Small static HTML file that can be compressed
2. Small static image files that cannot be compressed.

### Application benchmark

*   WordPress with cache plugin: 
    *   LSCache for LiteSpeed
    *   WP Super Cache for Apache
    *   FastCGI Cache for Nginx

## Results
