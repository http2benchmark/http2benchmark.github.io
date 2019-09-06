---
title: Nginx vs LiteSpeed
---
##   Vultr “High Frequency Compute” 2-GB instance
    * Date: July 23, 2019
    * Server: 2GB memory, 1-core 3GHz+ CPUs ( 3792MHz )
    * Client: 2GB memory, 1-core 3GHz+ CPUs ( 3792MHz )
    * Network Bandwidth: 7.7Gbps

### HTTP/2: LSWS 5.4 vs Nginx 1.16 

Command: `h2load -n 100000 -c 100 -m 10 -H "Accept-encoding: gzip, deflate" https://<IP>/<URL>`

Test Name | LSWS 5.4    | Nginx 1.16 | LSWS vs Nginx
----------|------------:| -----------:|:-----:
1kstatic.html (req/s) | 212,222.00 | 33,909.20| 6.26 : 1
1knogzip.jpg (req/s) | 203,938.00 | 45,258.70| 4.50 : 1
wordpress homepage (req/s) | 69,421.10 | 6,045.70 | 11.48 : 1

### HTTPS: LSWS 5.4 vs Nginx 1.16 

Command: `wrk -d 5 -c 100 -H "Accept-encoding: gzip, deflate" https://<IP>/<URL>`

Test Name | LSWS 5.4    | Nginx 1.16 | LSWS vs Nginx
----------|------------:| -----------:|:-----:
1kstatic.html (req/s) | 78,968.90 | 25,513.00 | 3.09 : 1
1knogzip.jpg (req/s) | 66,455.80 | 37,813.80 | 1.75 : 1
wordpress homepage (req/s) | 31,285.80 | 6,117.31 | 5.11 : 1
