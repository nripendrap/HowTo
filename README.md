# How to
Keyboard shortcuts for Windows 10 

Win + D             Minimize all open windows (Works as toggle button)
Win + Down Arrow    Minimize active window
Win + S / Win + Q   Open Cortana in text mode, so you can type in the search bar
Ctrl + W            Close window
Ctrl + Shift + W    Close window

Ctrl + Left Click   Open link in a new tab
Ctrl + Enter        Open link in a new tab


Add or remove user from group in Windows 10

Win + R
lusrmgr.msc
Local Users and Groups app

Tools
1. Notepad++/VS Code
2. Ditto clipboard manager


Server=localhost\SQLEXPRESS;Database=master;Trusted_Connection=True;

https://github.com/aspnet/LibraryManager/issues/411
Manage Client-Side Libraries opens libman.json not UI Dialog
The dialog is accessed by right-clicking on a folder and choosing Add->Client Side Library...

The "Manage Client-Side Libraries" command opens libman.json to allow you to remove or change versions. When you save the file, LibMan will automatically update the downloaded files.

We understand that this is a little confusing, so we'll keep this item open to review the UX for the feature.




Installed 

--Terminal
Node.js
Git

Get-ExecutionPolicy
Get-ExecutionPolicy -list
 -- default: Restricted

Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser

Building for android
---------------------
Run following commands:

1. ionic integrations enable capacitor
2. ionic capacitor add android
```
      Issue:
      PS C:\Users\PradNrip\source\repos\acromaniac.client.ionic> ionic capacitor add android
      > capacitor.cmd add android
      [error] Capacitor could not find the web assets directory "C:\Users\PradNrip\source\repos\acromaniac.client.ionic\www".
          Please create it and make sure it has an index.html file. You can change
          the path of this directory in capacitor.config.json (webDir option).
          You may need to compile the web assets for your app (typically 'npm run build').
          More info: https://capacitorjs.com/docs/basics/building-your-app
      [ERROR] An error occurred while running subprocess capacitor.

        capacitor.cmd add android exited with exit code 1.

        Re-running this command with the --verbose flag may provide more information.
ionic build
```

3. ionic capacitor run android

push www directory to respective platform
4. npx cap copy
