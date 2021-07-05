# Weble Connect (Windows Weble VPN Client UI)


### TIGHT VNC Viewer

It is possible to open [Tight VNC Viewer](https://www.tightvnc.com/download.php) automatically from the interface. To do so, you just have to add "WC_TIGHTVNCVIEWER_PATH=[path to tvnviewwer.exe] parameter to the configuration file and restart "Weble Connect".

Config file (./supervision/config.sup in your application directory):

```
TINC_ENABLE=1
TINC_APP=1
WC_NAME=Weble Connect
WC_TIGHTVNCVIEWER_PATH=C:\Program Files\TightVNC\tvnviewer.exe
```
Restart your application

![restartwc](https://user-images.githubusercontent.com/6083644/124436748-97f18780-dd76-11eb-8f0c-56333bb79cc8.png)


Now you're able to directly open Tight VNC Viewer:

![tightvnc](https://user-images.githubusercontent.com/6083644/124434412-257fa800-dd74-11eb-84cd-9fcd8ec02d29.png)

