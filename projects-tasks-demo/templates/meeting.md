<%* 
const projects = (await app.plugins.getPlugin("dataview").api.tryQuery(`
TABLE WITHOUT ID
project
FROM "Efforts"
WHERE type = "project" AND project_status != "💤 Sleeping"
SORT project ASC
`)).values;
projects.push("! new project");
let selectedProject = await tp.system.suggester(item => item, projects.sort(), true, "Select a project or create a new one...");

if (selectedProject === "! new project") {
	selectedProject = await tp.system.prompt("Please enter new project:", null, false, false);
	let projectName = selectedProject.replaceAll('/', '-');
	const templatePath = tp.file.find_tfile("project");
	const folderPath = "Efforts/" +  projectName;
	let folder = app.vault.getAbstractFileByPath(folderPath);
	
	if (folder === null) {  
		await app.vault.createFolder(folderPath);  
		// get the folder again after creation  
		folder = app.vault.getAbstractFileByPath(folderPath);  
		tp.file.create_new(templatePath, projectName, false, folder)  ;
	}
}	
-%>
<%"---"%>
meeting_date: <% tp.file.creation_date("YYYY-MM-DD") %>
meeting_topic: <% tp.file.title %>
attendees: 
project:  "[[<% selectedProject %>]]"
tags: 
type: meeting
in: "[[Meetings]]"
created: <% tp.file.creation_date("YYYY-MM-DD") %>
template_version: "1.0"
<%"---"%>

# Meeting Goal


# Notes


# Actions

