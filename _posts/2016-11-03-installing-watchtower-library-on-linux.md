---
title:  "Installing Watchtower Library in Linux"
date:   2016-11-05 15:04:23
categories: [linux]
tags: [linux]
---

![Watchtower Library Installation Setup](/images/watchtower-library-application.png)

Figure 1: Watchtower Library Application on Ubuntu Linux

> __NOTE__: The information presented here might change (or might not apply) over time. Jehovah's Witnesses and other Christians alike might particular find this tutorial useful for Bible studies.

Watchtower Library is a reference and research tool which contains publications by the Watchtower Society dated back from 1970, as well as, reference Bibles. The application is currently developed for the Windows operating system and this tutorial will guide you to install and run it on [Linux](https://aberba.github.io/2016/what-is-linux/). An application called [PlayOnLinux](https://en.wikipedia.org/wiki/PlayOnLinux) allows Linux users to run Windows programs in Linux. 

> __NOTE__: This tutorial is for installing the `Watchtower Library` and NOT the `JW Library` (which is currently developed for Android or iOS devices). JW Library (the phone and tablet version) can be installed from the Google Play Store or Apple Store on Android and iOS respectively.
> You will need an Internet connection to complete this tutorial since most of the stuff will be installed online. 

> "Why use PlayOnLinux?"

PlayOnLinux is built using another application called [Wine](https://en.wikipedia.org/wiki/Wine_(software) ) which provides a runtime (core technology) for running Windows applications on Linux. Using PlayOnLinux makes it more easy to use Wine to install Watchtower Library.

I will be using Ubuntu version 14.04 (a Linux distribution) for this tutorial but you can equally follow along with any other Linux operating system using same or similar procedure.

## Installing PlayOn Linux

PlayOnLinux is available in the software center so you can either search and install from there or you can use the Ubuntu command-line with the following command;

```sh
sudo apt install -y playonlinux
```

OR on a Fedora-based distribution, you can use the command;

```sh
sudo dnf install -y playonlinux
```

This will install the PlayOnLinux application online so make sure you have Internet connection on your computer.


## Installing Watchtower Library using PlayOnLinux

Now that we have PlayOnLinux installed, we can now use it to install Watchtower library. 

> You may contact your local Kingdom Hall for a copy of the Watchtower Library application if you do not have a copy already. Currently, each new version comes every year so you may have to reinstall again when there is a newer version. 

### Lauching PlayOnLinux
Once you have installed PlayOnLinux, you can launch it from your applications menu. When launched, it will look similar to the image (screenshot) below;

![The PlayOnLinux application](/images/play-on-linux-application.jpg)
Figure 2: The PlayOnLinux Application running on Ubuntu Linux

### Installing Watchtower Library
To begin with Watchtower Library installation, click on the `Install` button as indicated in the screenshot above. This will launch a dialog which will fetch all the list of applications supported officially in PlayOnLinux as show below;

![List of officially supported application in PlayOnLinux](/images/play-on-linux-database.jpg)
Figure 3: List of applications officially supported in PlayOnLinux

> __NOTE__ I will be using the 2015 edition of the Watchtower Library to demonstrate so I do not guarantee that any other version (newer or older) will work with this same process. However, this should also work for the 2014 edition. 

Look for Watchtower Library 2014 from the list of applications supported, either by scrolling down or using the search entry on-top of the list as shown below;

![Watchtower Library 2014 edition](/images/watchtower-library-2014-in-list.png)
Figure 4: Watchtower Library 2014 edition in the list

As you can see, the Watchtower Library 2014 edition is the only option, however the 2015 edition will also work. Select `Watchtower Library 2014` and click on the `Install` button beneath to proceed with the installation. This will launch a dialog (Wizard) which will assist you with the installation process as show below;

![Watchtower Library Installation Wizard](/images/watchtower-library-install-wizard.png)
Figure 5: Watchtower Library Installation Wizard

Click on the `Next` button to continue. The installer will present you with three options;

1. __Overwrite__ - Used this option when you want to reinstall Watchtower Library on PlayonLinux again, especially if you cannot launch an existing installation.
2. __Erase__ - Use this option if you want to completely remove (wipe out) an existing Watchtower Library installation from PlayOnLinux to install a fresh copy again. This option come in handy for first-time installation or when you are installing a newer Watchtower Library version.
3. __Abort Installation__ - This option will stop the installation process and return back to the main PlayOnLinux application window.

I will select Option 2 and click `Next` to proceed. You will now be presented with another dialog with two options as show below;

![Watchtower Library Installation Wizard](/images/watchtower-library-select-setup.png)
Figure 6: Watchtower Library Installation Wizard

1. __Use a setup file on my computer__ - Use this option if you have copied the Watchtower Library application files onto your computer.
2. __Use CD-ROMS(s)__ - Use this option to install from a DVD disk which contains the Watchtower Library (make sure you have inserted the disk into your computer before proceeding with this option).

I will select Option 1 and click `Next` after which I will be presented with and dialog with a button labelled `Browse`. Click on that button to select the Watchtower Library application executable labelled `Setup.exe` from your computer as shown below;

![Watchtower Library Installation Setup](/images/watchtower-library-select-setup-executable.png)
Figure 7: Watchtower Library Executable

> If you select option 2, browse to the CD ROM to select the executable. There may be other executables for Windows Phone (those old Windows Phones) but that is not covered in this tutorial. 

After selecting the executable, click `Next` to proceed. This will launch a dialog to configure and install the necessary files required to be able to run the Watchtower Library in PlayOnLinux online so make sure you have Internet connection. The process may take some few minutes (at least in my experience) to complete so be patient when it seem to be delaying - this may take a little longer especially when you have a slow Internet connection. When this process is finished, you will be presented with a `Finish` button, so click on it to finish the configuration part. 

After everything is successful, PlayOnLinux will immediately launch another window (an installation wizard) which will take your through the process of installing the _actual_ Watchtower Library application. Proceed by click next, next, next... (affirm the default options). Once the installation is complete, PlayOnLinux application should have Watchtower Library listed in the main window as shown below;

![Watchtower Library Installed in PlayOnLinix](/images/watchtower-library-installed-in-playonlinux.png)
Figure 8: Watchtower Library Installed in PlayOnLinix


### Managing Wine versions
We are _almost_ done except that the version of Wine installed by default in PlayOnlinux does not work for running the installed Watchtower Library application. Therefore, we will have to install an __OLDER__ version (version 1.7.38 at the time of this tutorial). Click on the `Tools` menu from  the PlayOnLinux main window and select `Manage Wine versions` as show below;

![Manage Wine Versions Menu](/images/play-on-linux-wine-versions-manager-menu.jpg)
Figure 9: Manage Wine Versions Menu

This will present you with a dialog which shows the available Wine version in the left pane (fetched from the Wine project database) and those installed on your computer in the right pane. On the left section, scroll to find version `1.7.38`, select it and click on the button labelled with the greater-than symbol (`>`) in the middle to install it. This process may also take some few minutes (again, depending on your internet connection speed :)  ) so be patient. After version `1.7.38` of Wine has been installed, it will show up in the right pane as show below;


![Wine version manager dialog](/images/play-on-linux-wine-versions-dialog.jpg) Figure 9: Wine version manager dialog

> NOTE: You may also install version 1.7.35 in addition to version 1.7.38 for safe keeping.

Once this is done, close the dialog to return to the main PlayOnLinux window to now launch (run) Watchtower Library.

### Launching Watchtower Library
Select it from the main window and click on the `Run` button at the top. This will launch the splash screen of the Watchtower Library application after which your will be presented with the main window of Watchtower Library.

![Watchtower Library Application](/images/watchtower-library-installed.png)
Figure 10: Watchtower Library Application 

Whew!! that was quiet a process, let me know in the comments section below if you encounter any problem with installation.