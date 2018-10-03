---
title: "How to uninstall LibreOffice and install WPS office in Ubuntu 18.04"
date: 2018-10-03T18:18:28+09:00
author: "Khamidulla Inoyatov"
---

* [Uninstall LibreOffice](#uninstall-libreoffice)
* [Install WPS office](#install-wps-office)

***

# <a name="uninstall-libreoffice"></a>Uninstall LibreOffice

Open terminal by using following shortcut <kbd>Ctrl+Alt+t</kbd>, if you do not knew how to do so. 
Then type following lines in terminal window which will remove all packages related to libreoffice.

{{< highlight >}}
sudo apt-get remove --purge libreoffice*
sudo apt-get clean
sudo apt-get autoremove
{{< /highlight >}}

# <a name="install-wps-office"></a>Install WPS office

Open your browser and navigate to following [downloads page](http://wps-community.org/downloads).
Choose proper debian package from "Addresses" section for your Ubuntu installation architecture and download it.

![Download options](images/Download Options.png)

> If you do not knew what is your Ubuntu installation architecture type following in your browser **uname -i**.
> You should see something like this in terminal output **x86_64**. It means your installation architecture
> is 64 bit. So you should select *wps-office_10.1.0.6757_amd64.deb*

In terminal window navigate to directory where you saved your file using `cd` command. In my case it is
**Downloads** directory under user's home directory. Then type following command:

{{< highlight >}}
cd ~/Downloads
sudo dpkg -i wps-office_10.1.0.6757_amd64.deb
{{< /highlight >}}

If you noticied in order to install WPS office you need super user permissions. After executing last command
wait until it will compleates and then you can start using WPS office.
