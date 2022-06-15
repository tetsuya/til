# dig
domain information groper

```
$ dig tetsuya.dev

; <<>> DiG 9.10.6 <<>> tetsuya.dev
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 759
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 1232
;; QUESTION SECTION:
;tetsuya.dev.			IN	A

;; ANSWER SECTION:
tetsuya.dev.		300	IN	A	172.67.217.28
tetsuya.dev.		300	IN	A	104.21.24.54

;; Query time: 79 msec
;; SERVER: 2407:c800:7f01:2000:219:110:2:24#53(2407:c800:7f01:2000:219:110:2:24)
;; WHEN: Wed Jun 15 06:36:41 UTC 2022
;; MSG SIZE  rcvd: 72
```

## Display only answer section
```
$ dig +noall +answer tetsuya.dev
tetsuya.dev.		300	IN	A	172.67.217.28
tetsuya.dev.		300	IN	A	104.21.24.54
```

### +[no]all
Set or clear all display flags.

```
$ dig +noall tetsuya.dev

```

### +[no]answer
Control display of answer section.

```
$ dig +noanswer tetsuya.dev

; <<>> DiG 9.10.6 <<>> +noanswer tetsuya.dev
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 6003
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 1232
;; QUESTION SECTION:
;tetsuya.dev.			IN	A

;; Query time: 43 msec
;; SERVER: 2407:c800:7f01:2000:219:110:2:24#53(2407:c800:7f01:2000:219:110:2:24)
;; WHEN: Wed Jun 15 06:37:24 UTC 2022
;; MSG SIZE  rcvd: 72
```

## Query type {A|MX|TXT|CNAME|NS}
Query a specific DNS record type

```
$ dig +short NS tetsuya.dev
thomas.ns.cloudflare.com.
jocelyn.ns.cloudflare.com.
```

### +[no]short
Display answer in short form. `+noshort` is equivalent to `+all`

```
$ dig +short tetsuya.dev
104.21.24.54
172.67.217.28
```

## Use different DNS server

You can specify a different server by using `@server`. This can be an IPv4 address, an IPv6 address, or the name of the server.

```
$ dig @thomas.ns.cloudflare.com. +noall +answer tetsuya.dev
tetsuya.dev.		300	IN	A	172.67.217.28
tetsuya.dev.		300	IN	A	104.21.24.54
```

### [Cloudflare Public DNS](https://www.cloudflare.com/ja-jp/learning/dns/what-is-1.1.1.1/)
```
$ dig @1.1.1.1 +noall +answer +stats tetsuya.dev
tetsuya.dev.		300	IN	A	104.21.24.54
tetsuya.dev.		300	IN	A	172.67.217.28
;; Query time: 329 msec
;; SERVER: 1.1.1.1#53(1.1.1.1)
;; WHEN: Wed Jun 15 06:40:20 UTC 2022
;; MSG SIZE  rcvd: 72
```

### [Google Public DNS](https://developers.google.com/speed/public-dns)
```
$ dig @8.8.8.8 +noall +answer +stats tetsuya.dev
tetsuya.dev.		300	IN	A	172.67.217.28
tetsuya.dev.		300	IN	A	104.21.24.54
;; Query time: 92 msec
;; SERVER: 8.8.8.8#53(8.8.8.8)
;; WHEN: Wed Jun 15 06:40:30 UTC 2022
;; MSG SIZE  rcvd: 72
```

## +[no]trace
Shows the answer from each server used to resolve a domain name. `+notrace` is equivalent to `+all`

```
$ dig +trace tetsuya.dev

; <<>> DiG 9.10.6 <<>> +trace tetsuya.dev
;; global options: +cmd
.			511067	IN	NS	a.root-servers.net.
.			511067	IN	NS	b.root-servers.net.
.			511067	IN	NS	c.root-servers.net.
.			511067	IN	NS	d.root-servers.net.
.			511067	IN	NS	e.root-servers.net.
.			511067	IN	NS	f.root-servers.net.
.			511067	IN	NS	g.root-servers.net.
.			511067	IN	NS	h.root-servers.net.
.			511067	IN	NS	i.root-servers.net.
.			511067	IN	NS	j.root-servers.net.
.			511067	IN	NS	k.root-servers.net.
.			511067	IN	NS	l.root-servers.net.
.			511067	IN	NS	m.root-servers.net.
.			511067	IN	RRSIG	NS 8 0 518400 20200629050000 20200616040000 48903 . aWTFYLbKkhzdBbDxrCPRpJSnEsvwvspYZgJW5NlUmY321DG+yPa6i1z3 YXuNJaBJx0r/XHREn8L9yDJBJWVjmS6VYl7pQLzAXU9B4p889J1PoZoV 8dhG0HNMxda1jfotGCG+xRiLczPLGxMC4fi4wrxYQUj0G2c+dggThwsy T1eRqr74CcU+Ube/RZ09q3li3zg/UxzIVpmbCMmi1gtz93XuhHhcbs3l lVeCo90eaCk7n9Ay9cHOQRKlf7pRwiKLGDznKtI3m+PLpALeMgJzYjsz MKHlvlChy0ss1Utd24u6c9ikeA5dfg6C65f/5eMpqUCF+/KbaEIUoFp/ yzpNew==
;; Received 525 bytes from 1.1.1.1#53(1.1.1.1) in 24 ms

dev.			172800	IN	NS	ns-tld1.charlestonroadregistry.com.
dev.			172800	IN	NS	ns-tld2.charlestonroadregistry.com.
dev.			172800	IN	NS	ns-tld3.charlestonroadregistry.com.
dev.			172800	IN	NS	ns-tld4.charlestonroadregistry.com.
dev.			172800	IN	NS	ns-tld5.charlestonroadregistry.com.
dev.			86400	IN	DS	60074 8 2 B942E2CE5AEBF62FCA59D05707E6DBB795211D540D8ADBA02E9E89E8 33424785
dev.			86400	IN	RRSIG	DS 8 1 86400 20200629050000 20200616040000 48903 . kM+Q1cGw0xXAJErILQn9b+xsSrl7cLQk47yU85GNf7+uEvlI4BLRG+L4 1o0cx7FFrveK23dtcMw2Jc+Kha1QPSbw1E6X09XniMDXoezqhF31s0fr yKK3Y2kkxXQpHUVT/NxXWLbJ6ZAi3ctWI6Woh2SbBzb86Ggmma5EDbnG v6rDvOZaEfg/RDO4ccXpSxv9kJNY8mZNlB3hk+gLqlLM2GnWfLC+pnN/ nUJJP15zk8qV+hokk8NXUIC2mmO7QFjbK0+6bIXS2Yq1pvfZYkLumKgb LoWiuaVWcAK3S/rKEKuNW6JGX38DSw2CcROayyvV86zuMhIhKDo7kVj5 zdiaaA==
;; Received 731 bytes from 199.7.83.42#53(l.root-servers.net) in 134 ms

tetsuya.dev.		10800	IN	NS	ns-cloud-a1.googledomains.com.
tetsuya.dev.		10800	IN	NS	ns-cloud-a2.googledomains.com.
tetsuya.dev.		10800	IN	NS	ns-cloud-a3.googledomains.com.
tetsuya.dev.		10800	IN	NS	ns-cloud-a4.googledomains.com.
0rgudcvqtbf3oand8leokj1f7pk73qiu.dev. 300 IN NSEC3 1 0 1 B7B0891083980E59 0RH185F5P63J2D8I8NKQM07F33LJ80CU  NS
0rgudcvqtbf3oand8leokj1f7pk73qiu.dev. 300 IN RRSIG NSEC3 8 2 300 20200704202942 20200612202942 56224 dev. Yxuto/A4xoN8hpN9QlG4TXOAuPJ5+7j4qUT2bV20TfeREGVh1JfkaniU VhMHull4VTW0H6ORR7TKRW+DBXSx/g0nha9JTPYhQHk81R15b4AXm/qm lmbtUofnEFOtY2ndKxtFrPBbEevw+BYH6FC8k1R9PQEEdQE6JU1Ccv/r XRw=
;; Received 406 bytes from 216.239.32.105#53(ns-tld1.charlestonroadregistry.com) in 42 ms

tetsuya.dev.		3600	IN	A	104.198.14.52
;; Received 56 bytes from 216.239.38.106#53(ns-cloud-a4.googledomains.com) in 81 ms
```
