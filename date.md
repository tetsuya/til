# date

Display date and time:

```
$ date
Fri Dec 24 14:06:49 JST 2021
```

To show the time on different timezone, set `TZ` environment variable:

```
$ TZ=Australia/Melbourne date
Fri Dec 24 16:06:53 AEDT 2021
```

## -u
Display the date in UTC

```
$ date -u
Fri Dec 24 05:06:56 UTC 2021
```

## -d
Parse date in your local timezone. This option does **NOT** work on macOS.

```
$ date -d '2021-12-24 00:00 UTC'
Fri Dec 24 09:00:00 JST 2021
```

You can specify timezone here too:

```
$ TZ=Australia/Melbourne date -d '2021-12-24 00:00 UTC'
Fri Dec 24 11:00:00 AEDT 2021
```
