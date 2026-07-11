---
type: dashboard
title: "PhD — Health & orphans"
---

# PhD — Health & orphans

## No incoming links

```dataview
TABLE file.link
FROM "phd/wiki" AND -"phd/wiki/dashboards" AND -"phd/wiki/projects"
WHERE length(file.inlinks) = 0
```

## Open contradictions

```dataview
TABLE file.link
FROM "phd/wiki"
WHERE contradiction
```

## Empty stubs

```dataview
TABLE file.link
FROM "phd/wiki"
WHERE type = "stub"
```
