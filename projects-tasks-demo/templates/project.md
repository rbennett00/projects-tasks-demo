<%* 
const folders = tp.file.folder(true).split('/');
const project = folders[folders.length - 1]; 

const areas = (await app.plugins.getPlugin("dataview").api.tryQuery(`
TABLE WITHOUT ID
area
FROM "Efforts"
WHERE area 
GROUP BY area 
SORT length(rows.file.link) DESC
`)).values;
areas.push("! new area");
let selectedArea = await tp.system.suggester(item => item, areas.sort(), true, "Select an area or create a new area for this project...");

if (selectedArea === "! new area") {
	selectedArea = await tp.system.prompt("Please enter new area:", null, false, false);
}
-%>
<%"---"%>
up: "[[Efforts]]"
project: <% project %>
created: <% tp.date.now("YYYY-MM-DD") %>
start_date: <% tp.date.now("YYYY-MM-DD") %>
project_status: on
area: <% selectedArea %>
dependencies: 
product: 
stakeholders:
project_team:
tags: 
rank:
type: project
template_version: "1.1"
<%"---"%>
# Project Goals
- x
- y
- z
# Notes

---

> [!multi-column]
>> [!todo]+ Tasks
>> ``` tasks
>> not done
>> description includes 📋[[<% project %>]]
>> sort by due
>> group by priority
>> short mode
>>```
>
>>[!hint]+ Meetings
>>  ``` dataview
>>  list
>>  from "Calendar/Meetings"
>>  where contains(project, this.file.link)
>>  sort meeting_date desc
>>  ```
>
>> [!summary]+ Documents
>>  -
>>  -

---
Back to `= this.up`