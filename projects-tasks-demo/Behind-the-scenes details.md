Here's a little more detail of what's happening to connect everything together.

## Creating a new effort / project
When you select some text on a note anywhere in your vault and press `Ctrl-Alt-P`, the Templater script [[Create new project]] gets called and does the following:
- Checks to see if there is text selected in the note you pressed the hotkey on
	- If there's no text highlighted, prompt you to enter a project name, otherwise just use the selected text
- Creates a new folder under `Efforts` with the text from above as the folder name
- Creates a file in the newly created folder with the same file name as the folder, using the [[project]] template. By default this will automatically set the new file as the folder note for your project folder.
- When the new file is created, the Templater script in the project template takes over and prompts you to select an Area for your project. It lists all of the values you've already used in the `area` property of existing project notes, and you can create a new Area from here as well.
- Finally, the rest of the project template sets up the YAML properties and the Tasks and Meetings queries so that everything will connect across your vault.
-  Note that if you also add people using the `stakeholders`  or `project_team` property, this project will show up automatically on each person's People page under Related Projects.

## Creating a new meeting note
When you select some text on a note anywhere in your vault and press `Ctrl-Alt-M`, the Templater script [[Create new meeting note]] gets called and does the following:
- Checks to see if there is text selected in the note you pressed the hotkey on
	- If there's no text highlighted, prompt you to enter a meeting name, otherwise just use the selected text
- Creates a file in `Calendar\Meetings` with the current date and the text from above as the file name (e.g., '2024-02-09 Fun Meeting'), using the [[meeting]] template. 
- When the new file is created, the Templater script in the meeting template takes over and prompts you to select an project your meeting is associated with. It lists all of the projects in the Efforts folder, and you can create a new Project from here as well (which does the same thing as the `Ctrl-Alt-P` hotkey).
- Finally, the rest of the project template sets up the YAML properties so that this meeting will automatically show up on the associated Project page.
- Note that if you also add people using the `attendees` property, this meeting will show up automatically on each attendee's People page under Meeting log.

## Associating a task with a project
There is currently no built-in way with the Obsidian Tasks plugin to associate a task with a project. To accomplish this, we have to overload the task description with the project name (or any other unique identifier, like a nested tag) so we can find it using dataview queries. There are many different ways to do this - for me, I found it easiest to create a hotkey that brings up a list of all the Projects and then inserts `📋Projectname` into the description field wherever the cursor is. This is admittedly inelegant, but it worked for me  😊. 

To do this simply create a new task (either using the Tasks popup window or directly in markdown. Then click into the text at the end of your task description (and before any other date fields). Then press `Ctrl-Alt-M` and the [[script - assign to project]] Templater script will run and basically run through the same project selection process as when you create a new meeting note. The script will then insert `📋Projectname` into the text description where your cursor is.

As I said, you could tweak this to use a different identifier, and you don't need to use the hotkey to associate a task with a project - you could just type (or paste) `📋Projectname` in the task description and it will show up on the project page. Note that if you want to use a different identifier (like tags) then you'll have to update the task query in the [[project]] template to search for the right string.