<%*  
let projectName = "";

if (tp.file.selection() === '') {
	projectName = await tp.system.prompt("Project name:", null, false, false);
} else {
	projectName = tp.file.selection();
}

projectName = projectName.replaceAll('/', '-');
const templatePath = tp.file.find_tfile("project");
const folderPath = "Efforts/" +  projectName;
let folder = app.vault.getAbstractFileByPath(folderPath);
console.log(templatePath);
if (folder === null) {  
	await app.vault.createFolder(folderPath);  
	// get the folder again after creation  
	folder = app.vault.getAbstractFileByPath(folderPath);  
}

tp.file.create_new(templatePath, projectName, false, folder);
%>[[<% projectName %>]]