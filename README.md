#!!!DEPRECATED!!!
Google has implemented a way to find orphaned files and directories. Search "is:unorganized" on Google Drive to find orphaned files and folders. You can narrow search by using "is:unorganized owner:me" or "type:folder is:unorganized".

# Orphan File Finder for Google Drive
This is a Google Apps Script which finds orphan files and folders on one's Google Drive.

### What is an orphaned file?
If an item in Google Drive loses all of its parent folders, it becomes orphan. The item still exists, but it may be a little hard to find.
For more detailed information: https://support.google.com/a/answer/6008339?hl=en

### What is Google Apps Script
Google Apps Script is a cloud based scripting language for light-weight application development in the Google Apps platform.
For more information: https://developers.google.com/apps-script/

## What does this do?
 * Creates a starred Folder names "Lost+Found".
 * Iterates all files and folders which belongs to you, or shared with you.
 * If this file or folder is not in your "My Drive" or "Lost+Found", adds it to "Lost+Found"

### How can you use it?
 * Go to [this link](https://script.google.com/macros/s/AKfycby7g--KZ2DsuCbxL3mOqChgi0Yg8KJLBM1_87C6N3juwJZMv1zF/exec) and authorize it.
 * The script will be run periodically on each 12 hours.
 * You can found your rescued files on "Lost+Found" folder on your [Starred](https://drive.google.com/drive/#starred) section on Google Drive.
 * If you want to de-authorize the script visit [this link](https://script.google.com/macros/d/M34QqyYeiUPsx34wIV8tjARf4lvhlP8BT/manage/uninstall)

### I want to run my own script. How can I do it?
 * Go to [this link](https://script.google.com/) and create a blank App Script file.
 * Paste this source code on your Apps Script file.
 * Now you can run your own code.
