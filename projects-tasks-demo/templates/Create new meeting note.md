<%*  
let now = new Date();  
let year = now.getFullYear();  
let month = String(now.getMonth() + 1).padStart(2, '0');  
let day = String(now.getDate()).padStart(2, '0');  

let topicName = '';
if (tp.file.selection() === '') {
	topicName = await tp.system.prompt("Meeting name:", null, false, false);
} else {
	topicName = tp.file.selection();
}
topicName = topicName.replaceAll('/', '-');  

const templatePath = tp.file.find_tfile("meeting")  ;
const folderPath = "Calendar/Meetings";
let folder = app.vault.getAbstractFileByPath(folderPath);  
  
if (folder === null) {  
await app.vault.createFolder(folderPath);  
// get the folder again after creation  
folder = app.vault.getAbstractFileByPath(folderPath);  
} 

tp.file.create_new(templatePath, `${year}-${month}-${day} ` + topicName, false, folder)  
%>[[<% `${year}-${month}-${day} ` + topicName  %>]]