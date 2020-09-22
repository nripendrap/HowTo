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

https://html.developreference.com/article/12038514/How+to+access+localhost+from+android+emulator%3F


Configure IIS to access website using IP address
Open port in windows firewall
https://manage.accuwebhosting.com/knowledgebase/2886/How-to-configure-IIS-to-access-website-using-IP-address.html

netstat -a -n