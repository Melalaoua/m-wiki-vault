---
type: dashboard
title: "Personal — Activity & status"
---

# Personal — Activity & status

## Touched in the last two weeks

```dataview
TABLE updated AS "Last touched", status
FROM "personal/wiki" AND -"personal/wiki/dashboards"
WHERE updated AND date(updated) >= date(today) - dur(14 days)
SORT updated DESC
```

## Every page, by status

```dataview
TABLE rows.file.link AS "Pages"
FROM "personal/wiki" AND -"personal/wiki/dashboards"
WHERE status
GROUP BY status
```
