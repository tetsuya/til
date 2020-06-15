# grep
## default
```
$ ps aux | grep puma
tetsuya          88092   0.1  0.6  4451156 101168 s001  S+   12:30PM   0:03.57 puma 4.3.3 (tcp://localhost:3000) [playground]
tetsuya          88145   0.0  0.0  4286472    836 s003  S+   12:30PM   0:00.01 grep --color=auto puma
tetsuya          88136   0.0  0.0  4475620   6456 s001  S+   12:30PM   0:00.01 puma: cluster worker 1: 88092 [playground]
tetsuya          88135   0.0  0.0  4475620   6476 s001  S+   12:30PM   0:00.01 puma: cluster worker 0: 88092 [playground]
```

## -e / --regexp
Specify a pattern used during the search of the input: an input line is selected if it matches any of the specified patterns.

```
$ ps aux | grep puma | grep -e cluster -e worker
tetsuya          88136   0.0  0.0  4475620   6728 s001  S+   12:30PM   0:00.02 puma: cluster worker 1: 88092 [playground]
tetsuya          88135   0.0  0.0  4475620   6744 s001  S+   12:30PM   0:00.02 puma: cluster worker 0: 88092 [playground]
```

## -E / --extended-regexp
Interpret pattern as an extended regular expression.

```
$ ps aux | grep puma | grep -E 'cluster|worker'
tetsuya          88136   0.0  0.0  4475620   6728 s001  S+   12:30PM   0:00.02 puma: cluster worker 1: 88092 [playground]
tetsuya          88135   0.0  0.0  4475620   6744 s001  S+   12:30PM   0:00.02 puma: cluster worker 0: 88092 [playground]
```

## -v / --invert-match
Selected lines are those not matching any of the specified patterns.

```
$ ps aux | grep puma | grep -v 'grep'
tetsuya          88136   0.0  0.0  4475620   6476 s001  S+   12:30PM   0:00.01 puma: cluster worker 1: 88092 [playground]
tetsuya          88135   0.0  0.0  4475620   6492 s001  S+   12:30PM   0:00.01 puma: cluster worker 0: 88092 [playground]
tetsuya          88092   0.0  0.6  4449096 101148 s001  S+   12:30PM   0:03.57 puma 4.3.3 (tcp://localhost:3000) [playground]
```

### Combination
```
$ ps aux | grep puma | grep -Ev  'grep|tcp'
tetsuya          88136   0.0  0.0  4475620   6476 s001  S+   12:30PM   0:00.01 puma: cluster worker 1: 88092 [playground]
tetsuya          88135   0.0  0.0  4475620   6492 s001  S+   12:30PM   0:00.01 puma: cluster worker 0: 88092 [playground]
```

## -i / --ignore-case
Perform case insensitive matching. By default, grep is case sensitive.

```
$ ps aux | grep PUMA
tetsuya          88896   0.0  0.0  4278280    732 s003  R+   12:37PM   0:00.01 grep --color=auto PUMA

$ ps aux | grep -i PUMA
tetsuya          88926   0.0  0.0  4277256    788 s003  R+   12:37PM   0:00.01 grep --color=auto -i PUMA
tetsuya          88136   0.0  0.0  4475620   7056 s001  S+   12:30PM   0:00.06 puma: cluster worker 1: 88092 [playground]
tetsuya          88135   0.0  0.0  4475620   7064 s001  S+   12:30PM   0:00.06 puma: cluster worker 0: 88092 [playground]
tetsuya          88092   0.0  0.6  4449096 101168 s001  S+   12:30PM   0:03.61 puma 4.3.3 (tcp://localhost:3000) [playground]
```
