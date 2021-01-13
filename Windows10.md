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

```telnet```
Check ports whether they are open or not

```tracert```
Displays routes or paths taken to reach destination

### PowerShell
#### Execution policy

```Get-ExecutionPolicy```\
```Get-ExecutionPolicy -list```

```Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser```

#### Open explorer from cmd from current directory
```start .```

#### Execute multiple PS commands on one line
Use semicolon between commands. For example:

```git add .; git commit -m "files updated"; git push origin develop```

## Add or remove user from group
Steps
1. Win + R
2. lusrmgr.msc
3. Local Users and Groups app