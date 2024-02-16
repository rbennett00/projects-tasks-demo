---
up:
  - "[[Welcome]]"
in:
  - "[[Collections]]"
created: 2024-02-09
tags:
  - map/view
---

This page uses DataviewJS to list all of the projects/efforts in the 'Efforts'  folder, grouped by Area (using the area property in the project template), sorted by rank. The first codeblock is more complex because it puts each Area in a callout. If you don't care about that and just want a basic Dataview-style look, you can use the second codeblock instead (just remove the double-% above and below it).


```dataviewjs
async function drawCallout(header, entries) { 
	header = ">" + header + "\n><p style='height:0px; padding: 0px; margin: 0px;'>";
    const id = (Math.random() + 1).toString(36).substring(7);
    const target = `span.dataview.rbennett${id} span div.callout`;
    await dv.span(header, { cls: `dataview rbennett${id}` });
    const div = document.querySelectorAll(target + " div.callout-content")[0];
	await dv.api.table(["(" + entries.length + ")","Rank","Status"], entries, div, dv.component);
}

for (let group of dv.pages('"Efforts"').groupBy(p => p.area)) {
	await drawCallout("[!globe]+ ### " + group.key, group.rows.sort(k => k.rank, 'desc').map(k => [k.file.link, k.rank, k.project_status]));
};

//delete the extra row in the table header
const unwantedElements = document.querySelectorAll('.dataview.small-text');
unwantedElements.forEach(element => { 
	element.parentNode.removeChild(element);
	});
```


%%
```dataviewjs
for (let group of dv.pages('"Efforts"').groupBy(p => p.area)) {
	dv.header(3, group.key);
	dv.table(["Effort", "Rank", "Status"],
		group.rows
			.sort(k => k.rank, 'desc')
			.map(k => [k.file.link, k.rank, k.project_status]))
 }
```
%%

Back to `= this.up`
