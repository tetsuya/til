# Splunk

## sort
```
| sort _time desc
```

see: [sort - Splunk Documentation](https://docs.splunk.com/Documentation/Splunk/latest/SearchReference/Sort)

## stats
```
| stats count by status
```

## chart
```
| chart stats count by status, host
```

see: [Search commands > stats, chart, and timechart | Splunk](https://www.splunk.com/en_us/blog/tips-and-tricks/search-commands-stats-chart-and-timechart.html)
