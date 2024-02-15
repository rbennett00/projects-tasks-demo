---
up:
  - "[[Welcome]]"
in:
  - "[[Collections]]"
created: 2024-02-09
tags:
  - map/view
---

This page uses DataviewJS to list all of the projects/efforts in the 'Efforts'  folder, grouped by Area (using the area property in the project template), sorted by rank. The first codeblock is more complex because it puts each Area in a callout. If you don't care about that and just want a basic Dataview-style look, you can use the second codeblock instead (just remove the double-% above and below it). I'm still exploring ways to render the top version more elegantly, but am running into some weirness with dataviewjs and tables.

%%
```dataviewjs
var temp='\n> |Effort|Rank|Status|\n> |--|--|--|';
for (let group of dv.pages('"Efforts"').groupBy(p => p.area)) {
	for (let row of group.rows
		.sort(k => k.rank, 'desc')
		.map(k => ["[[" + k.file.name + "]]", k.rank, k.project_status])) {
			temp +=('\n> |' + row[0] + ' | ' + row[1] + ' | ' + row[2] + '|')
			}
	let mkdw = '> [!globe]+ ### ' + group.key + temp;
	dv.span(mkdw);
	temp='\n> |Effort|Rank|Status|\n> |--|--|--|';
 }
```
%%


```dataviewjs
function drawCallout(header, entries) {
    
		header = ">" + header + "\n><p style='height:0px; padding: 0px; margin: 0px;'>";
    	let id = (Math.random() + 1).toString(36).substring(14);
    	let target = `span.dataview.rbennett${id} span div.callout`;
    	dv.span(header, { cls: `dataview rbennett${id}` });
    	let div = document.querySelectorAll(target + " div.callout-content")[0];
    	//dv.api.taskList(tasks, false, div, dv.component);
		dv.api.table(["Effort","Rank","Status"], entries, div, dv.component);
}


for (let group of dv.pages('"Efforts"').groupBy(p => p.area)) {
	drawCallout("[!globe]+ " + group.key, group.rows.sort(k => k.rank, 'desc').map(k => [k.file.link, k.rank, k.project_status]));
}
```



Back to `= this.up`
