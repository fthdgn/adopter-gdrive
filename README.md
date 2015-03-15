# Orphan File Finder for Google Drive
This is a Google Apps Script which finds orphan files and folders on one's Google Drive.

### What is an orphaned file?
If an item in Google Drive loses all of its parent folders, it becomes an orphan. The item still exists, but it may be a little harder to find.
For more detailed information: https://support.google.com/a/answer/6008339?hl=en

### What is Google Apps Script
Google Apps Script is a cloud based scripting language for light-weight application development in the Google Apps platform.
For more information: https://developers.google.com/apps-script/

## What does this?
 * Creates a starred Folder names "Lost+Found".
 * Iterates all files and folders which belongs you, or shared to you.
 * If this file or folder is not in your "My Drive" or "Lost+Found", adds it to "Lost+Found"

### How can I develope this script
 * Go to [this link](https://script.google.com/) and create a blank App Script file.
 * Paste this source code on your App Script file.
 * Click Resources menu, the click Advanced Google Services.
 * Turn on Drive API
 * Follow "These services must also be enabled in the Google Developers Console." link
 * Turn on Drive API from here also.
 * Now you can run your code.

### I just want to use it
The script does not have a interface yet.
 * You can go to [my own release script](https://drive.google.com/open?id=1mtd2qRER9befN1AzokqjOMHZMFC5uSpViuD83FVpdG4m50WhxsL8f7Wf&authuser=0)
 * Select funtion main.
 * Click the run button. 
 * It will run. You can close your page. 
 * If you want to run this script periodically
 * Go to Resources menu
 * Click "Current Project's triggers"
 * Add a time-driven trigger.

P.S. This link is my own script file which is I will release bug fixes and enchantments. I will not add any code to delete file or send them somewhere else.
