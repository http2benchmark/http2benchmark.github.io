---
title: Nginx vs LiteSpeed
---

##   Digital Ocean 1GB Droplet
    * Date: 07/23/2019
    * Server: 1GB memory, 1-core Intel(R) Xeon(R) CPU E5-2650 v4 @ 2.20GHz
    * Client: 2GB memory, 1-core Intel(R) Xeon(R) Gold 6140 CPU @ 2.30GHz
    * Network Bandwidth: 1.8Gbps

### HTTP/2: LSWS 5.4 vs Nginx 1.16  

Command: `h2load -n 100000 -c 100 -m 10 -H "Accept-encoding: gzip, deflate" https://<IP>/<URL>`

Test Name | LSWS 5.4    | Nginx 1.16 | LSWS vs Nginx
----------|------------:| ------------:|:-----:
1kstatic.html (req/s) | 156,422.00 | 18,734.10| 8.35 : 1
1knogzip.jpg (req/s) | 132,162.00 | 27,898.10| 4.73 : 1
wordpress homepage (req/s) | 36,089.90 | 3,597.00 | 10.03 : 1

### HTTPS: LSWS 5.4 vs Nginx 1.16 

Command: `wrk -d 5 -c 100 -H "Accept-encoding: gzip, deflate" https://<IP>/<URL>`

Test Name | LSWS 5.4    | Nginx 1.16 | LSWS vs Nginx
----------|------------:| -----------:|:-----:
1kstatic.html (req/s) | 41,794.80 | 15,580.20 | 2.68 : 1
1knogzip.jpg (req/s) | 40,326.40 | 21,976.70 | 1.83 : 1
wordpress homepage (req/s) | 16,414.00 | 3,410.70 | 4.81 : 1
