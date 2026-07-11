---
type: dashboard
title: "Personal — Reading queue"
---

# Personal — Reading queue

Raw originals banked but not yet ingested, oldest capture first. Consulted by choice — never posted.

```dataview
TABLE captured AS "Captured"
FROM "personal/raw"
WHERE captured AND length(file.inlinks) = 0
SORT captured ASC
```
