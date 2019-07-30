---
title: 複製 Google 雲端的資料夾
thumbnail: /images/index.JPG
date: 2018-03-20 18:10:35
categories: 軟體
tags:
- Google Drive
---

## 前言

最近在 PTT 上看到有好心的大大分享了 Python 的教學資源。因為資料很多，不想全部下載下來，我就開始尋找有沒有直接把資料複製到自己雲端的方法

<!-- more -->

除了一個一個按右鍵建立副本外，我找到一個以 Google 試算表為介面，執行 Google App Script 後，就能把該 Folder ID 的資料夾複製到自己的雲端。

不過我實際使用後，資料夾內的檔案太多的話，會容易失敗的樣子

* [How To: Copy Folder Structure and Contents in Google Drive?](http://techawakening.org/copy-folder-structure-contents-in-google-drive/2846/)
* [CHG: google 雲端硬碟 對資料夾 做副本，複製一份到自己的帳戶](https://charlottehong.blogspot.tw/2017/12/google.html)
* [[教學] 如何在 Google Drive 裡面複製一份資料夾出來 @ 老電影下載 :: 痞客邦 ::](http://ak77now.pixnet.net/blog/post/44908675-%5B%E6%95%99%E5%AD%B8%5D-%E5%A6%82%E4%BD%95%E5%9C%A8google-drive%E8%A3%A1%E9%9D%A2%E8%A4%87%E8%A3%BD%E4%B8%80%E4%BB%BD%E8%B3%87%E6%96%99%E5%A4%BE%E5%87%BA)

附上原始碼

```js
/*
       ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~   
        Google Drive: Copy/Duplicate Folder Structure and Contents without using Desktop App
       ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
  
   
                      For instructions, go to http://techawakening.org/?p=2846
                      For queries, bugs reporting comment on the above article.
   
                  Written by Shunmugha Sundaram for Techawakening.org - April 27, 2014

            --.--        |                   |              o                          
              |,---.,---.|---.,---.. . .,---.|__/ ,---.,---..,---.,---. ,---.,---.,---.
              ||---'|    |   |,---|| | |,---||  \ |---'|   |||   ||   | |   ||    |   |
              ``---'`---'`   '`---^`-'-'`---^`   ``---'`   '``   '`---|o`---'`    `---|
                                                                  `---'           `---'
                                                                 
Credits:

Finding Subordinate Folders/Files: By David French via http://goo.gl/mhykXU

Change Log:

Jan-13-2015: V1.1: Update to Prevent Files from being Tagged to My Drive Root.

Apr-29-2015: V2: DocList deprecated, Script rewritten to use DriveApp.

To Donate: http://techawakening.org/go/donate
*/

var sheet = SpreadsheetApp.getActiveSheet();
var spreadsheet = SpreadsheetApp.getActiveSpreadsheet();
var scriptproperties = PropertiesService.getScriptProperties();

function authorize() {
    spreadsheet.toast("Enter Folder ID and  Select GDrive: Copy Folder->  Make a Copy", "", -1);

}


function onOpen() {
    var ss = SpreadsheetApp.getActiveSpreadsheet();
    var menuEntries = [{
            name: "1. Authorize",
            functionName: "authorize"
        }, {
            name: "2. Make a Copy",
            functionName: "findRootFolder"
        }

    ];
    ss.addMenu("GDrive: Copy Folder", menuEntries);
    spreadsheet.toast("Select GDrive: Copy Folder-> Authorize. This is an One Time Action.", "Get Started", -1);
}

function findRootFolder() {
    var folderId = sheet.getRange("B5").getValue();
    var folderId = folderId.toString().trim();
    var start = new Date();

    try {

        var topFolder = DriveApp.getFolderById(folderId);

        deletekeys();
        spreadsheet.toast("Copy Process Has Started. Please Wait...", "Started", -1);
        getFolders_(topFolder.getName(), topFolder);
        spreadsheet.toast("Folder Has Been Copied Successfully. Please Check Your Google Drive Now.", "Success", -1);
    } catch (e) {
        Browser.msgBox("Error", "Sorry, Error Occured: " + e.toString(), Browser.Buttons.OK);
        spreadsheet.toast("Error Occurred :( Please make sure you Entered Folder ID in B5 Cell.", "Oops!", -1);
    }

}

function getFolders_(path, container) {

    var folders = container.getFolders();

    var count = 0;
    while (folders.hasNext()) {
        count++;
        var folder = folders.next();
    }

    var folderCount = count;
    var fileslist = container.getFiles();
    var fileCountFind = 0;
    while (fileslist.hasNext()) {
        fileCountFind++;
        var file = fileslist.next();
        Logger.log(file.getName());
    }
    var fileCount = fileCountFind;
    var files = container.getFiles();

    Logger.log("container.getName() " + container.getName() + "| folder length " + folderCount + "| files length " + fileCount);

    if (folderCount <= 0) {

        if (fileCount > 0) {
            Logger.log("Just Files Found Loop");
            copyfiles_(container.getName(), files);
        }
    }

    if (folderCount) {
        Logger.log("If loop, Folders Found");
        var folders = container.getFolders();

        while (folders.hasNext()) {

            var folder = folders.next();
            copy_(container.getName(), folder.getName(), files);
            var thisFolder = folder.getName();
            var thisPath = path + "/" + thisFolder;
            Logger.log("Folder Name:" + folder.getName());
            getFolders_(thisPath, folder);

        }
        
    }
    return;
}

function copy_(containername, childname, files)

{

    if (scriptproperties.getProperty(containername + "copy")) {
        Logger.log("if");
        var parentcontainer = DriveApp.getFolderById(scriptproperties.getProperty(containername + "copy"));

        if (!scriptproperties.getProperty(containername + "processed")) {
            /*process, copy files*/

            while (files.hasNext()) {
                var file = files.next();
                var newFile = file.makeCopy(file.getName(), parentcontainer);
               //parentcontainer.addFile(newFile);
                DriveApp.getRootFolder().removeFile(newFile);
                Utilities.sleep(2000);
            }




        }

        scriptproperties.setProperty(containername + "processed", "true");
        var childfolder = parentcontainer.createFolder(childname + "_copy");
        var childfolderid = childfolder.getId();
        scriptproperties.setProperty(childname + "copy", childfolderid);

    } else {

        Logger.log("else");
        var parentfold = DriveApp.createFolder(containername + "_copy");
        var parentfoldid = parentfold.getId();
        scriptproperties.setProperty(containername + "copy", parentfoldid);



        if (!scriptproperties.getProperty(containername + "processed")) {
            /*process, copy files*/

            while (files.hasNext()) {
                var file = files.next();
                var newFile = file.makeCopy(file.getName(), parentfold);
            //  parentfold.addFile(newFile);
                DriveApp.getRootFolder().removeFile(newFile);
                Utilities.sleep(2000);
            }

        }

        scriptproperties.setProperty(containername + "processed", "true");
        var childfolder = parentfold.createFolder(childname + "_copy");
        var childfolderid = childfolder.getId();
        scriptproperties.setProperty(childname + "copy", childfolderid);

    }
    Logger.log("Container Name: " + containername + "||" + " Child Name: " + childname);
}

function copyfiles_(containername, files) {
    if (scriptproperties.getProperty(containername + "copy")) {
        Logger.log("If Loop, Just files found- down");
        var parentcontainer = DriveApp.getFolderById(scriptproperties.getProperty(containername + "copy"));

        if (!scriptproperties.getProperty(containername + "processed")) {

            while (files.hasNext()) {
                var file = files.next();
                var newFile = file.makeCopy(file.getName(), parentcontainer);
              //parentcontainer.addFile(newFile);
                DriveApp.getRootFolder().removeFile(newFile);
                Utilities.sleep(2000);
            }
        }
        scriptproperties.setProperty(containername + "processed", "true");

    } else {

        Logger.log("Else Loop, Just files found");
        var parentfold = DriveApp.createFolder(containername + "_copy");
        var parentfoldid = parentfold.getId();
        scriptproperties.setProperty(containername + "copy", parentfoldid);

        if (!scriptproperties.getProperty(containername + "processed")) {

            while (files.hasNext()) {
                var file = files.next();
                var newFile = file.makeCopy(file.getName(), parentfold);
              //parentfold.addFile(newFile);
                DriveApp.getRootFolder().removeFile(newFile);
                Utilities.sleep(2000);
            }



        }
        scriptproperties.setProperty(containername + "processed", "true");
    }

}

function deletekeys() {
    scriptproperties.deleteAllProperties();
}
```