# How to install Kali Linux GUI Desktop in Android using Termux:

This Guide will help you install Kali Linux in Android, that too with a GUI Desktop Environment within Android. It uses [Termux](https://f-droid.org/en/packages/com.termux/) to run Kali Linux in Android with XFCE4 Desktop Environment and a Tight VNC Server, which we connect to using a [VNC Viewer app](https://play.google.com/store/apps/details?id=com.realvnc.viewer.android) in Android.

## Just Follow these steps to install Kali Linux with XFCE4 Desktop GUI in Android using Termux:

* Download and install [Termux](https://f-droid.org/en/packages/com.termux/) in Android. ([Play Store release](https://play.google.com/store/apps/details?id=com.termux) is no more updated, so is not recommended.)
* Open Termux and run the following commands (will download around 100MB of files):
  ```
  apt update && apt install proot-distro -y
  proot-distro install nethunter
  proot-distro login nethuter
  ```
* After completion of the above steps, you will be in Kali Linux Shell. Run any of the following commands in the Kali Shell:

  * For a Minimal Desktop with no Default Apps:
    ```
    apt update && apt install kali-desktop-core --no-install-recommends -y
    ```
      * To Install the Default Apps, run (Optional, can be done later):
        ```
        apt update && apt install xfce4-goodies
        ```
  ***
  * For a Minimal Desktop with Default Apps:
    ```
    apt install kali-desktop-core -y
    ```
  ***
  * For Full Kali Linux Desktop:
    ```
    apt install kali-desktop-xfce -y
    ```
* Then Run the following commands:
  ```
  apt install xfce4-terminal -y
  apt install dbus-x11 -y
  apt install tightvncserver -y
  vncserver
  ```
* When it asks, Create and confirm a new password and remember it. You will need it to login in later steps.
* After setting the password, run the following command:
  ```
  vncserver -kill :1
  rm -f ~/.vnc/xstartup
  echo -e '#!/bin/bash\nxrdb \$HOME/.Xresources\nstartxfce4 &' > ~/.vnc/xstartup
  sudo chmod +x ~/.vnc/xstartup
  vncserver
  ```
* Let Termux run in background by pressing HOME button in Android.
* Install [VNC Viewer](https://play.google.com/store/apps/details?id=com.realvnc.viewer.android) in Android and open it.
* In VNC Viewer, press the + button in the lower right corner.
  * Under Address type `localhost:5901`.
  * Under Name type any name that you want to show in the app.
  * Press Create. An Entry by the name you entered will appear.
* Press the entry you just created in VNC Viewer.
* Type in the password that you created in a previous step (Turn on the Remember password slider if preffered) and press continue in the upper right corner.
* You will soon be in your Kali Linux XFCE4 Desktop Environment.
## How to stop the session:
Once you have done working(hacking) using Kali-Linux, follow these steps to stop the session:
* Swipe down from the top of the VNC Viewer app and tap the cross (`X`) icon.
* Tap `Disconnect` when it asks you about being sure to disconect.
* Now close the VNC Viewer app.
* Then open Termux that was running in background.
* To kill the VNC Server in Kali and exit from Kali, run the following commands:
  ```
  vncserver -kill:1
  exit
  ```
* To exit from Termux, type `exit` and press Enter.
## How to start a new session:
To start a new session if the installation part is already done, follow the following steps:
* Open Termux and run the command, `vncviewer`.
* Let Termux run in background by pressing HOME button in Android.
* Open VNC Viewer and press the entry that you created during installation(https://github.com/HiDe-Techno-Tips/install-kali-Linux-GUI-Desktop-in-Android-using-Termux/blob/main/README.md#how-to-stop-the-session).
* Type in the password created during (Turn on the Remember password slider if preffered) installation and press continue in the upper right corner.
* You will soon be in your Kali Linux XFCE4 Desktop Environment.
* [Click here](https://github.com/HiDe-Techno-Tips/install-kali-Linux-GUI-Desktop-in-Android-using-Termux/blob/main/README.md#how-to-stop-the-session) to see how to close the session.
