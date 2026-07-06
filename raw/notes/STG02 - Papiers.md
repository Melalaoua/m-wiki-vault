tags:: #master/StageS4 

```dataviewjs
for (let group of dv.pages("#papiers/stages2").groupBy(p => p.groupe)) {
	dv.header(4, group.key);
	dv.table(["Papiers", "Authors", "Sous-groupe", "Pertinence", "Links"],
		group.rows
			.sort(k => k.pertinence, 'desc')
			.map(k => [k.file.link, k["authors"], k["sous-groupe"], k.pertinence, k.links]))
}
```

