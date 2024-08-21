
<%* 
let content=`--cssclass: kanban gridlist noyaml
tag: moc
obsidianUIMode: preview
--- `;
content +=   "`button-homewp`  `button-browsevault`  `button-browsenext` `button-browserefresh` \n"
content +=   "%% moc %%"
const folders = this.app.vault.getAllLoadedFiles().filter(i => i.children).map(folder => folder.path);
const selfolder=folders.map((item)=>{
    item='📁 '+item;
    return item;
});
const folderChoicePath = await tp.system.suggester(selfolder, folders,false,"Select the folder to generate the MOC");
if (folderChoicePath != null) {
	new Notice(`Folder selected: ${folderChoicePath}`, 5000);
		folders.map(async function (folder) {
		if(folder.includes(folderChoicePath))  //只对当前选择的目录以及子目录生成moc
			{
			let foldername =folder.replace(/(.*\/)*([^.]+)/i,"$2");
			let overwrite =''
			const Path = (folder== '/' ? '' : folder + '/') + foldername ;  
			if(tp.file.exists(Path))
			{overwrite = await tp.system.suggester(['yes','no'], ['yes','no'],false,"Does it overwrite files ''"+ Path +"''?");
				if(overwrite==="yes"){ await app.vault.delete(tp.file.find_tfile(Path)) 
					 await tp.file.create_new(content,Path) }}
			else await tp.file.create_new(content,Path)}})}else {
	new Notice (`No folder selected`, 5000[);}%>](<%3C%* 
let content=`---
cssclass: kanban gridlist noyaml
tag: moc
obsidianUIMode: preview
--- `;
content +=   "`button-homewp`  `button-browsevault`  `button-browsenext` `button-browserefresh` \n"
content +=   "%% moc %%"
const folders = this.app.vault.getAllLoadedFiles().filter(i =%3E i.children).map(folder => folder.path);
const selfolder=folders.map((item)=>{
    item='📁 '+item;
    return item;
});
const folderChoicePath = await tp.system.suggester(selfolder, folders,false,"Select the folder to generate the MOC");
if (folderChoicePath != null) {
	new Notice(`Folder selected: ${folderChoicePath}`, 5000);
		folders.map(async function (folder) {
		if(folder.includes(folderChoicePath))  //只对当前选择的目录以及子目录生成moc
			{
			let foldername =folder.replace(/(.*\/)*([^.]+)/i,"$2");
			let overwrite =''
			const Path = (folder== '/' ? '' : folder + '/') + foldername ;  
			if(tp.file.exists(Path))
			{overwrite = await tp.system.suggester(['yes','no'], ['yes','no'],false,"Does it overwrite files ''"+ Path +"''?");
				if(overwrite==="yes"){ await app.vault.delete(tp.file.find_tfile(Path)) 
					 await tp.file.create_new(content,Path) }}
			else await tp.file.create_new(content,Path)}})}else {
	new Notice(`No folder selected`, 5000);}%>>)