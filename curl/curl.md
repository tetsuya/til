# curl
cURL

## -I / --head
Show document info only

```
$ curl -I https://tetsuya.herokuapp.com
HTTP/1.1 503 Service Unavailable
Connection: keep-alive
Server: Cowboy
Date: Tue, 20 Jul 2021 02:07:31 GMT
Content-Length: 506
Content-Type: text/html; charset=utf-8
Cache-Control: no-cache, no-store
```

## --tls-max <VERSION>
Specify TLS minor version

```
$ curl -Iv --tls-max 1.0 https://tetsuya.herokuapp.com
...
* TLSv1.0 (OUT), TLS handshake, Client hello (1):
* TLSv1.0 (IN), TLS handshake, Server hello (2):
* TLSv1.0 (IN), TLS handshake, Certificate (11):
* TLSv1.0 (IN), TLS handshake, Server key exchange (12):
* TLSv1.0 (IN), TLS handshake, Server finished (14):
* TLSv1.0 (OUT), TLS handshake, Client key exchange (16):
* TLSv1.0 (OUT), TLS change cipher, Change cipher spec (1):
* TLSv1.0 (OUT), TLS handshake, Finished (20):
* TLSv1.0 (IN), TLS change cipher, Change cipher spec (1):
* TLSv1.0 (IN), TLS handshake, Finished (20):
* SSL connection using TLSv1.0 / ECDHE-RSA-AES128-SHA
...
```
