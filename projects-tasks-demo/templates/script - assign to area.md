<%*
const areas = (await app.plugins.getPlugin("dataview").api.tryQuery(`
TABLE WITHOUT ID
area
FROM "projects"
WHERE area 
GROUP BY area 
SORT length(rows.file.link) DESC
`)).values;
areas.push("! new area");
let selectedArea = await tp.system.suggester(item => item, areas.sort(), true, "Placeholder...");

if (selectedArea === "! new area") {
	selectedArea = await tp.system.prompt("Please enter new area:", null, false, false);
}
%>