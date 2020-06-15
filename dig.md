# dig
domain information groper

```
$ dig tetsuya.dev

; <<>> DiG 9.10.6 <<>> tetsuya.dev
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 3259
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 1452
;; QUESTION SECTION:
;tetsuya.dev.			IN	A

;; ANSWER SECTION:
tetsuya.dev.		3596	IN	A	104.198.14.52

;; Query time: 94 msec
;; SERVER: 1.1.1.1#53(1.1.1.1)
;; WHEN: Tue Jun 16 22:42:00 JST 2020
;; MSG SIZE  rcvd: 67
```

## +[no]all
Set or clear all display flags.

```
$ dig tetsuya.dev +noall

; <<>> DiG 9.10.6 <<>> tetsuya.dev +noall
;; global options: +cmd
```

## +[no]answer
Control display of answer section.

```
$ dig tetsuya.dev +noanswer

; <<>> DiG 9.10.6 <<>> tetsuya.dev +noanswer
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 59989
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 1452
;; QUESTION SECTION:
;tetsuya.dev.			IN	A

;; Query time: 12 msec
;; SERVER: 1.1.1.1#53(1.1.1.1)
;; WHEN: Tue Jun 16 23:16:16 JST 2020
;; MSG SIZE  rcvd: 67
```

### combination
```
$ dig tetsuya.dev +noall +answer

; <<>> DiG 9.10.6 <<>> tetsuya.dev +noall +answer
;; global options: +cmd
tetsuya.dev.		2976	IN	A	104.198.14.52
```

## +[no]short
Display nothing except short form of answer. `+noshort` is equivalent to `+all`

```
$ dig tetsuya.dev +short
104.198.14.52
```

## Query type {A|MX|TXT|CNAME|NS}
Query a specific DNS record type

```
$ dig tetsuya.dev mx

; <<>> DiG 9.10.6 <<>> tetsuya.dev mx
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 887
;; flags: qr rd ra; QUERY: 1, ANSWER: 5, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 1452
;; QUESTION SECTION:
;tetsuya.dev.			IN	MX

;; ANSWER SECTION:
tetsuya.dev.		3447	IN	MX	5 gmr-smtp-in.l.google.com.
tetsuya.dev.		3447	IN	MX	10 alt1.gmr-smtp-in.l.google.com.
tetsuya.dev.		3447	IN	MX	20 alt2.gmr-smtp-in.l.google.com.
tetsuya.dev.		3447	IN	MX	30 alt3.gmr-smtp-in.l.google.com.
tetsuya.dev.		3447	IN	MX	40 alt4.gmr-smtp-in.l.google.com.

;; Query time: 19 msec
;; SERVER: 1.1.1.1#53(1.1.1.1)
;; WHEN: Tue Jun 16 22:59:39 JST 2020
;; MSG SIZE  rcvd: 175
```

### combination
```
$ dig tetsuya.dev mx +short
5 gmr-smtp-in.l.google.com.
10 alt1.gmr-smtp-in.l.google.com.
20 alt2.gmr-smtp-in.l.google.com.
30 alt3.gmr-smtp-in.l.google.com.
40 alt4.gmr-smtp-in.l.google.com.
```

## +[no]trace
Shows the answer from each server used to resolve a domain name. `+notrace` is equivalent to `+all`

```
$ dig tetsuya.dev +trace

; <<>> DiG 9.10.6 <<>> tetsuya.dev +trace
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
