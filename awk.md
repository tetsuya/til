# awk

```
$ ps aux | grep puma
tetsuya          88092   0.1  0.6  4451156 101168 s001  S+   12:30PM   0:03.57 puma 4.3.3 (tcp://localhost:3000) [playground]
tetsuya          88145   0.0  0.0  4286472    836 s003  S+   12:30PM   0:00.01 grep --color=auto puma
tetsuya          88136   0.0  0.0  4475620   6456 s001  S+   12:30PM   0:00.01 puma: cluster worker 1: 88092 [playground]
tetsuya          88135   0.0  0.0  4475620   6476 s001  S+   12:30PM   0:00.01 puma: cluster worker 0: 88092 [playground]

$ ps aux | grep puma | awk '{print $2}'
88092
88145
88136
88135
```

## -F 

Set a field separator.

```
$ cat alphabet.csv
a,b,c,d,e,f,g,h,i,j,k,l,m,l,o,p,q,r,s,t,u,v,w,x,y,z

$ cat alphabet.csv | awk -F ',' '{print $3}'
c
```
