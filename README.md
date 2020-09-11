# az-kusto-query

### Calculate requests count by url and target
```
requests
| where timestamp > datetime("2020-09-11T07:28:00.000Z") and timestamp < datetime("2020-09-11T08:28:00.000Z")
| extend urlOnly = tostring(split(tolower(url), '?')[0])
| where tolower(urlOnly) has '/api'
| summarize totalCount=sum(itemCount) by urlOnly, cloud_RoleName
| order by totalCount desc
```
