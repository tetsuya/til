# lsof

## -i:<port>
Find the process that is listening on a port

```
$ lsof -i:3000
COMMAND   PID    USER   FD   TYPE             DEVICE SIZE/OFF NODE NAME
ruby    11169 tetsuya   17u  IPv6 0x188cbc8e81b5c037      0t0  TCP localhost:hbci (LISTEN)
ruby    11169 tetsuya   18u  IPv4 0x188cbc8e85455407      0t0  TCP localhost:hbci (LISTEN)
```

see: https://stackoverflow.com/a/3855359/1285818
