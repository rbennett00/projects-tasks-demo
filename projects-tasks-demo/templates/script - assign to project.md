<%*
const projects = (await app.plugins.getPlugin("dataview").api.tryQuery(`
TABLE WITHOUT ID
project
FROM "Efforts"
WHERE project 
GROUP BY project 
SORT length(rows.file.link) DESC
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
%> 📋[[<% selectedProject %>]]