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

## table

Returns a table that is formed by only the fields that are specified in the arguments.

```
| table _time, event
```

## Remove duplicates

Both `dedup` and `uniq` works as a filter on the search results to remove any search result that is an exact duplicate. `dudup` however only looks at fields specified.

### dedup
```
| dedup field1
```

### uniq
```
| uniq
```
