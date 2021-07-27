# Windows 10

## Keyboard shortcuts
#### General
Key | Description 
-- | --
Win + D | Minimize all open windows (Works as toggle button)
Win + Down Arrow | Minimize active window
Win + S | Open Cortana in text mode, so you can type in the search bar
Win + Q | Open Cortana in text mode, so you can type in the search bar
Ctrl + W | Close window
Ctrl + Shift + W | Close window
Win + V | Open clipboard manager
#### Browser
Key | Description
-- | --
Ctrl + Left Click | Open link in a new tab
Ctrl + Enter | Open link in a new tab
#### Multiple desktops
Key | Description
-- | --
Win + Tab | Open task view / desktop view
Win + Ctrl + D | Add new desktop
Win + Ctrl + Left Arrow | Switch Desktop
Win + Ctrl + Right Arrow  | Switch Desktop
Win + Ctrl + F4 | Close the desktop, you're currently on

## Useful commands
### Network diagnostic commands
```ping```

```netstat```
Checks network configuration and activity
\
__Example:__
1. Find out which application is using the port.
    ```netstat -ao | findstr <port_number_to_search_for>```

```telnet```
Check ports whether they are open or not

```tracert```
Displays routes or paths taken to reach destination

### PowerShell
#### Execution policy

```Get-ExecutionPolicy```\
```Get-ExecutionPolicy -list```

```Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser```

#### Open File Explorer from cmd from current directory
```start .```

#### Open PowerShell from right click context menu
1. Shift + Right Click the folder / Shift + Menu Key
2. Then select _Open PowerShell window here_ menu

#### Execute multiple PS commands on one line
Use semicolon between commands. \
For example: \
```git add .; git commit -m "files updated"; git push origin develop```

## Add or remove user from group
1. Select __Run__ from the __Start__ menu or alternatively, Press Win + R to bring up the __Run__ command.
2. Type _lusrmgr.msc_ and press __Enter__.
The Local User and Group Management tool appears.

## Open certificate manager
1. Select __Run__ from the __Start__ menu, and then enter _certmgr.msc_.
The Certificate Manager tool for the current user appears.
