## Manage Client-Side Libraries opens libman.json, not UI Dialog
__Issue__ 
When 
https://github.com/aspnet/LibraryManager/issues/411
Manage Client-Side Libraries opens libman.json not UI Dialog
The dialog is accessed by right-clicking on a folder and choosing Add->Client Side Library...

The "Manage Client-Side Libraries" command opens libman.json to allow you to remove or change versions. When you save the file, LibMan will automatically update the downloaded files.

We understand that this is a little confusing, so we'll keep this item open to review the UX for the feature.

## Unable to connect to web server 'IIS Express'
1. Stop IIS Express
2. Close Visual Studio
3. Delete hidden folder __.vs__ under Visual Studio project solution folder
4. Delete __config__ folder under __%DOCUMENTS%\IISExpress__
5. Restart your PC
5. Run Visual Studio as Administrator

## Convert XML to Classes in Visual Studio 2019
1. Copy XML data
2. On the menu, select __Edit > Paste Special > Paste XML As Classes__ menu

## the application url cannot contain a query string or fragment