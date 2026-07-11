---
type: dashboard
title: "PhD — Activity & status"
---

# PhD — Activity & status

## Touched in the last two weeks

```dataview
TABLE updated AS "Last touched", status
FROM "phd/wiki" AND -"phd/wiki/dashboards"
WHERE updated AND date(updated) >= date(today) - dur(14 days)
SORT updated DESC
```

## Every page, by status

```dataview
TABLE rows.file.link AS "Pages"
FROM "phd/wiki" AND -"phd/wiki/dashboards"
WHERE status
GROUP BY status
```
