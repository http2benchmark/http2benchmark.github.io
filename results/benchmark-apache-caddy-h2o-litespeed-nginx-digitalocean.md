---
title: Apache vs Caddy vs H2o vs LiteSpeed vs Nginx
---

## Digital Ocean 1GB Droplet
* Date: September 6, 2019
* Server: 1GB memory, 1-core Intel(R) Xeon(R) CPU E5-2650 v4 @ 2.20GHz
* Client: 2GB memory, 1-core Intel(R) Xeon(R) Gold 6140 CPU @ 2.30GHz
* Network Bandwidth: 1.8Gbps

Test commands:
`h2load -n 100000 -c 100 -m 10 -H "Accept-encoding: gzip, deflate" https://<IP>/<URL>`
`wrk -d 5 -c 100 -H "Accept-encoding: gzip, deflate" https://<IP>/<URL>`

### Raw Results
```
h2load - 1kstatic.html
lsws 5.4.1      finished in       1.19 seconds,   83789.60 req/s,       9.95 MB/s,          0 failures,   96.21% header compression
nginx 1.16.1    finished in       5.72 seconds,   17477.20 req/s,       3.88 MB/s,          0 failures,   35.52% header compression
apache 2.4.41   finished in      40.08 seconds,    2494.80 req/s,       0.36 MB/s,          0 failures,   86.99% header compression
h2o 2.2.6       finished in       9.05 seconds,   11044.50 req/s,       1.31 MB/s,          0 failures,   95.08% header compression
caddy 0.11.4    finished in      26.76 seconds,    3737.40 req/s,       0.50 MB/s,          0 failures,   95.19% header compression
wrk - 1kstatic.html
lsws 5.4.1      finished in       5.02 seconds,   29775.80 req/s,      11.26 MB/s,        N/A failures,      N/A header compression
nginx 1.16.1    finished in       5.01 seconds,   13408.30 req/s,       4.86 MB/s,        N/A failures,      N/A header compression
apache 2.4.41   finished in       5.01 seconds,    3874.87 req/s,       1.55 MB/s,        N/A failures,      N/A header compression
h2o 2.2.6       finished in       5.00 seconds,   15595.40 req/s,       5.80 MB/s,        N/A failures,      N/A header compression
caddy 0.11.4    finished in       5.00 seconds,    4352.56 req/s,       1.57 MB/s,        N/A failures,      N/A header compression
h2load - 1knogzip.jpg
lsws 5.4.1      finished in       1.65 seconds,   60510.60 req/s,      60.78 MB/s,          0 failures,   96.66% header compression
nginx 1.16.1    finished in       3.67 seconds,   27267.10 req/s,      29.93 MB/s,          0 failures,   39.11% header compression
apache 2.4.41   finished in      15.88 seconds,    6295.50 req/s,       6.44 MB/s,          0 failures,   86.16% header compression
h2o 2.2.6       finished in       1.71 seconds,   58352.60 req/s,      58.77 MB/s,          0 failures,   91.71% header compression
caddy 0.11.4    finished in      24.40 seconds,    4098.70 req/s,       4.11 MB/s,          0 failures,   94.87% header compression
wrk - 1knogzip.jpg
lsws 5.4.1      finished in       5.02 seconds,   27796.50 req/s,      36.10 MB/s,        N/A failures,      N/A header compression
nginx 1.16.1    finished in       5.02 seconds,   17230.10 req/s,      20.77 MB/s,        N/A failures,      N/A header compression
apache 2.4.41   finished in       5.01 seconds,    4789.95 req/s,       5.85 MB/s,        N/A failures,      N/A header compression
h2o 2.2.6       finished in       5.01 seconds,   26642.90 req/s,      31.89 MB/s,        N/A failures,      N/A header compression
caddy 0.11.4    finished in       5.01 seconds,    5085.11 req/s,       5.96 MB/s,        N/A failures,      N/A header compression
h2load - wordpress
lsws 5.4.1      finished in       3.43 seconds,   29159.00 req/s,     113.28 MB/s,          0 failures,   96.64% header compression
nginx 1.16.1    finished in      30.08 seconds,    3324.40 req/s,      13.53 MB/s,          0 failures,   26.72% header compression
apache 2.4.41   finished in     256.78 seconds,     389.40 req/s,       1.45 MB/s,          0 failures,   87.82% header compression
h2o 2.2.6       finished in     138.52 seconds,     721.90 req/s,       2.68 MB/s,          0 failures,   95.77% header compression
caddy 0.11.4    finished in     226.72 seconds,     441.00 req/s,       1.63 MB/s,          0 failures,    95.3% header compression
wrk - wordpress
lsws 5.4.1      finished in       5.02 seconds,   14290.00 req/s,      60.17 MB/s,        N/A failures,      N/A header compression
nginx 1.16.1    finished in       5.01 seconds,    3201.17 req/s,      13.50 MB/s,        N/A failures,      N/A header compression
apache 2.4.41   finished in       5.01 seconds,     476.72 req/s,       1.95 MB/s,        N/A failures,      N/A header compression
h2o 2.2.6       finished in       5.02 seconds,     621.08 req/s,       2.53 MB/s,        N/A failures,      N/A header compression
caddy 0.11.4    finished in       5.01 seconds,     433.36 req/s,       1.76 MB/s,        N/A failures,      N/A header compression
```
