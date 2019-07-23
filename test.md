
## Benchmark Results

###   Digital Ocean Droplet 1
    * Date: 07/23/2019
    * Server: 1GB memory, 1-core Intel(R) Xeon(R) CPU E5-2650 v4 @ 2.20GHz
    * Client: 2GB memory , 1-core Intel(R) Xeon(R) Gold 6140 CPU @ 2.30GHz
    * Network Bandwidth: 1.8Gbps

#### LSWS 5.4 vs Nginx 1.16 HTTP/2 

Command: `h2load -n 100000 -c 100 -m 10 -H "Accept-encoding: gzip, deflate" https://<IP>/1kstatic.html`

<sub><sup> tiny text</sup></sub>
   
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

