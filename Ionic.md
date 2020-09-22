Building for android
---------------------
Run following commands:

1. ionic integrations enable capacitor
2. ionic capacitor add android
3. ionic capacitor run android

push www directory to respective platform
4. npx cap copy


Debug
-----
chrome://inspect/#devices

Issues
------
Issue #1
      PS <filepath>\ionic> ionic capacitor add android
      > capacitor.cmd add android
      [error] Capacitor could not find the web assets directory "<filepath>\www".
          Please create it and make sure it has an index.html file. You can change
          the path of this directory in capacitor.config.json (webDir option).
          You may need to compile the web assets for your app (typically 'npm run build').
          More info: https://capacitorjs.com/docs/basics/building-your-app
      [ERROR] An error occurred while running subprocess capacitor.

        capacitor.cmd add android exited with exit code 1.

        Re-running this command with the --verbose flag may provide more information.

Soln:
ionic build

Issue #2
failed to load resource: net::err_cleartext_not_permitted in ionic app capacitor

Soln:
https://github.com/ionic-team/capacitor/issues/2118


Issue #3
WebApi hosted on iis and android emulator connection refused

Localhost refers to your local machine. It's a common mistake that people think that the Android emulator (or iOS for that matter) is also part of localhost since it is running on the same machine. But this isn't the case.
The emulators are running as a device in your device and mimic the working as if it was a physical device. It has it's own IP address and cannot reach your localhost loopback address. Your app runs as a application on another machine, namely te emulator. It gets a bit confusing when using UWP, since this does run as an application on your local machine.
That is why you would have to use the network address of your machine where the server application is hosted. This address typically starts with 192.168.x.x or 10.x.x.x and can be found in the network settings of your machine.
It seems that you already discovered this. When using the 10.0.2.2 address you receive a HTTP 400. Which means something in your request wasn't right, but you can conclude from this that the server application can actually be reached. But the content of the request causes a problem in your server app. Since you do not provide any code for the /Account/Register endpoint it is impossible to tell what is going on there. Put a breakpoint in your server code, retry the request and try to see why a HTTP 400 is triggered.

https://html.developreference.com/article/12038514/How+to+access+localhost+from+android+emulator%3F

Issue #4
Binding IIS to an IP address

Allow port listening

Issue #5
Binding IIS Express to an IP address
Go to <solution folder> ->.vs -><solution folder name>->config
Edit applicationhost.config file manually 
edit bindingInformation '<ip-address>:<port>:<host-name>'
as
<binding protocol="http" bindingInformation="*:8083:192.168.2.102" />

Run IIS Express as admin. To run IIS Express as admin, Open Visual studio as admin and run the project. 

Issue #6
Could not read script '<other path>\android\capacitor-cordova-android-plugins\cordova.variables.gradle' as it does not exist

Delete android folder
Rebuild

Get the current network status
================================
```
import { Plugins } from '@capacitor/core';

const { Network } = Plugins;

// Get the current network status
let status = await Network.getStatus();
```

