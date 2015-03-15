function main() { 
  
  var user = Session.getActiveUser().getEmail();
  var root = DriveApp.getRootFolder(); 
  var folderToken = PropertiesService.getUserProperties().getProperty("folderToken");
  var fileToken = PropertiesService.getUserProperties().getProperty("fileToken");
  var lostfoundid = PropertiesService.getUserProperties().getProperty("lostfoundid");
  var lostfound;
  
  try {
    lostfound = DriveApp.getFolderById(lostfoundid);
  }
  catch (e) {
    lostfound = DriveApp.createFolder("Lost+Found");
    lostfound.setStarred(true);
    Drive.Parents.remove(lostfound.getId(), root.getId());
    lostfoundid = lostfound.getId();
    PropertiesService.getUserProperties().setProperty("lostfoundid", lostfoundid);
  }
  
    lostfound.setStarred(true);
  
  
  
  
  var folderIterator;
  var fileIterator;
  
  try {
    folderIterator = DriveApp.continueFolderIterator(folderToken); 
  }
  catch (e) {
    folderIterator = DriveApp.getFolders(); 
    folderToken = folderIterator.getContinuationToken();
    PropertiesService.getUserProperties().setProperty("folderToken", folderToken);
  }
  
  try {
    fileIterator = DriveApp.continueFileIterator(fileToken); 
  }
  catch (e) {
    fileIterator = DriveApp.getFiles(); 
    fileToken = fileIterator.getContinuationToken();
    PropertiesService.getUserProperties().setProperty("fileToken", fileToken);
  }
  
  var count = 1;
  
  while (folderIterator.hasNext()){
    checkFolder(folderIterator.next().getId(), root, lostfound, user);
    folderToken = folderIterator.getContinuationToken();
    count++;
    if (count%100 == 0){
      count = 1;
      PropertiesService.getUserProperties().setProperty("folderToken", folderToken);
    }
  }
  

  
  while (fileIterator.hasNext()){
    checkFile(fileIterator.next().getId(), root, lostfound, user);
    fileToken = folderIterator.getContinuationToken();
    if (count%100 == 0){
      count = 1;
      PropertiesService.getUserProperties().setProperty("fileToken", fileToken);
    }
  }
  
  
  folderToken = "0";
  PropertiesService.getUserProperties().setProperty("folderToken", folderToken);
  fileToken = "0";
  PropertiesService.getUserProperties().setProperty("fileToken", fileToken);
  
}



function checkFolder(id, root, lostfound, user) {
  f = DriveApp.getFolderById(id);
  var isOnDrive = false;
  
  if(f.isTrashed() && f.getOwner().getEmail() != user){
    return false;
  }
  
  if(f.isTrashed() && f.getOwner().getEmail() == user){
    return true;
  }
  
    if (id == root.getId() || id == lostfound.getId())
  {
    return false;
  }
  
  var parents = f.getParents();
  
  
  while(parents.hasNext()) {
    var parent = parents.next();
    
    if (parent.getId() == root.getId())
    return true;
    if (parent.getId() == lostfound.getId())
    return true;
    
    isOnDrive = isOnDrive || checkFolder(parent.getId(), root, lostfound, user);
  }
  
  if(!isOnDrive) 
    Drive.Parents.insert( { "id": lostfound.getId() } , id);
  
  
  return true;
}

function checkFile(id, root, lostfound, user) {
  f = DriveApp.getFileById(id);
  
  
  
  if(f.isTrashed()){
    return false;
  }

  var parents = f.getParents();
  
  while(parents.hasNext()) {
    var parent = parents.next();
    
   
    if (parent.getOwner().getEmail() == user)
      return false;
    
    if (checkFolder(parent.getId(), root, lostfound,user))
      return false;
  }
  
  Drive.Parents.insert( { "id": lostfound.getId() } , id);
  
  return true;
}