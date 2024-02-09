---
up:
  - "[[Welcome]]"
in:
  - "[[Collections]]"
created: 2024-02-09
tags:
  - map/view
---
```dataviewjs
var temp='';
for (let group of dv.pages('"Efforts"').groupBy(p => p.area)) {
	for (let row of group.rows) {
		temp +=('\n> ' + row.file.link)}
	let mkdw = '> [!globe]+ ### ' + group.key + temp
	dv.span(mkdw)
	temp=''
 }
```

Back to `= this.up`