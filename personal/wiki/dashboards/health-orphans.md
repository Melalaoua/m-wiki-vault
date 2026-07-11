---
type: dashboard
title: "Personal — Health & orphans"
---

# Personal — Health & orphans

## No incoming links

```dataview
TABLE file.link
FROM "personal/wiki" AND -"personal/wiki/dashboards" AND -"personal/wiki/projects"
WHERE length(file.inlinks) = 0
```

## Open contradictions

```dataview
TABLE file.link
FROM "personal/wiki"
WHERE contradiction
```

## Empty stubs

```dataview
TABLE file.link
FROM "personal/wiki"
WHERE type = "stub"
```
