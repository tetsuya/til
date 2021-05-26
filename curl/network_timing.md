# Network Timing with cURL

##  -w / --write-out

```
$ curl -w "dnslookup: %{time_namelookup} | tcp_established: %{time_connect} | ssl_handshake_done: %{time_appconnect} | pretransfer: %{time_pretransfer} | TTFB: %{time_starttransfer} | total: %{time_total} | size: %{size_download}\n" -o /dev/null -s https://blog.tetsuya.dev
dnslookup: 0.026756 | connect: 0.040709 | appconnect: 0.087856 | pretransfer: 0.088194 | starttransfer: 0.111317 | total: 0.113380 | size: 12203
```

| format | description |
| :----: | :---------: |
| time_namelookup | The time, in seconds, it took from the start until the name resolving was completed. |
| time_connect | The time, in seconds, it took from the start until the TCP connect to the remote host (or proxy) was completed. |
| time_appconnect | The time, in seconds, it took from the start until the SSL/SSH/etc connect/handshake to the remote host was  completed. |
| time_pretransfer | The  time,  in seconds, it took from the start until the file transfer was just about to begin. This includes all pre-transfer commands and negotiations that are specific to the particular protocol(s) involved. |
| time_starttransfer | The  time, in seconds, it took from the start until the first byte was just about to be transferred. This includes time_pretransfer and also the time the server needed to calculate the result. |
| time_total | The total time, in seconds, that the full operation lasted. |


## References
* [How do I debug latency issues using curl? - Heroku Help](https://help.heroku.com/NY64S5NL/how-do-i-debug-latency-issues-using-curl)
* [Timing web requests with cURL and Chrome - The Cloudflare Blog](https://blog.cloudflare.com/a-question-of-timing/)
