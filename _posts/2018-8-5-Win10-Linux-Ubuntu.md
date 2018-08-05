---
layout: post
title: Windows and Linux Ubuntu - Dual Boot
---

![Logos]({{ site.baseurl }}/images/header-Linux.png)



## Complete Development environment with Windows 10 and Linux - Part 1

This guide is for installing Linux Ubuntu 18.04 LTS alongside Windows 10, a.k.a. a dual boot PC.
The base of this project came from a personal lack of comfort with the dominant coding machine, the one sporting a bitten common fruit. I personally don’t own any interest, share or sponsorship from any of the corporations mentioned in this article. This article is the first of two intending to install a viable, useful and professional development environment on a PC desktop or laptop. The main components are:
* Ubuntu 18.04LTS
* Chrome or Chromium
* Git
* Visual Studio Code
  * EsLint
  * Prettier
* Node JS
  * NVM, NPM
  * Nodemon, Testem
* PostgreSQL
* DBeaver
* Postman

### IMPORTANT DISCLAIMER
> **Please note that some of the modifications could potentially brick your machine or necessitate a new install of Windows if done without precautions. Proceed at your own risk. The information in this post is true and complete to the best of my knowledge. All recommendations are made without any guarantee, implied or express, on the part of the author. The author disclaim any liability in connection with the use of this information.**

The seminal consideration came from a deep discomfort with an MacBook Pro mid-2015 15” used for the Junior phase at Fullstack Academy where I’m happy to be a student. It means a lot of time on a screen, a lot of coding and typing and a even longer time debugging, staring at a screen trying to figure out what the hell is going on... The two main aspects of my MacBook Pro, keyboard and screen, felt really lacking in comfort at the end of each day. On the other hand, the SurfaceBook2 felt much more comfortable for typing and spending long hours on code. This is my personal taste and opinion, and I don’t pretend to speak for any one else's taste or preferences. In other terms, feel free to stop reading if your inclination, heart and soul is toward Cuppertino instead of Redmond. I am sure you are a great person nevertheless… Just jokin’!

### Why Ubuntu?
Linux is more or less just the OS kernel. Several organisations, communities or companies use this kernel to put together a full OS. Some different flavors, called distributions, are: Debian, Red Hat, Mint, Linux Lite and a lot of others. Ubuntu 18.04 LTS codenamed Bionic Beaver is the latest stable and Long Term Support release. Linux is extensively used by deloppers and tech companies. It is the OS of reference for supercomputers and servers. A lot of cell phones and IoT devices run on Linux.

Ubuntu is distributed and maintained by  Canonical. It is arguably one of the two or three most popular distributions  of Linux. This means that bugs are fixed promptly, updates are regular and frequent and, more importantly, most of the applications found on a Mac running OSX or a PC/Win  will exist on Ubuntu/Linux. Sometimes it is an equivalent.

### Windows Sub-System for Linux
In short: WSL.
It allows the installation and use of Ubuntu 18.04 within Win10. It is essentially a dedicated local VM. It makes it possible to run Visual Studio Code, NodeJS and Github Desktop, ESlint (not global) and Testem (not global either). It may encounter some difficulties running global packages. Incidentally, it will be the theme of Part 2, also known as the sequel (not the SQL…)

### First steps
Before any modification, it is best to prepare a Windows 10 system image with a 32GB USB drive.
As well, backup your files and documents, so you have them in case something goes wrong. Use some DVDs or other USB drives.
Determine the HD where Ubuntu will reside and free some space on it if needed. Note that it is possible to run Ubuntu from a USB drive or in a virtual machine on Windows, see Part 2 for instance. It will limit the apps which can be installed or used, more so if running Ubuntu from a USB drive.
What you need:
- 1 USB Drive 8GB
- 1 USB drive 32GB
- Writable DVDs or some more USB drives
- 60 GB minimum of free space on the Hard Drive or SSD where Ubuntu will reside

### Image of Ubuntu
Links:
 - [Bootable USB drive Linux](http://www.everydaylinuxuser.com/2015/11/how-to-create-ubuntu-1510-usb-drive.html)
- [Guide Linux on PC](http://dailylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside.html)

Download Ubuntu 18.04LTS. LTS means Long Term Support, and identify a stable version. That’s what you want.
With the 8GB USB drive, create a bootable image of Ubuntu Linux. Some of the links refer to 16.04LTS, just transpose for 18.04LTS.
Check if your BIOS is UEFI or Legacy, as the install process is a bit different. The Guide Linux on PC describes the differences. You may have to disable BitLocker and/or SecureBoot in Windows 10.

### Linux partition
If you have more than 1 HD, it is preferable to install Linux on a different drive from the one supporting your Windows OS.
Start Disk Management from  the Search bar and shrink the main partition on the Linux  drive. A minimum of 60GB is advised for Linux Ubuntu, while leaving some space for your other files. A 500GB HD can accommodate a 150 to 200GB partition for Linux, and that is plenty (see notes at the end).
There is now a zone labelled “Unallocated Space”.

### Install
Turn off the machine, and insert the drive in an empty USB slot.
Turn the PC back on and press F11 or the keys necessary to get to the BIOS and force the boot to be from a USB drive. On a Surface device, it is PowerOn button and SoundUp button.
Choose to use Ubuntu or install. For the following directions, let’s assume the installation option has been chosen. Ubuntu will install in the Unallocated space precedently set up .

### Bionic Beaver is alive!
Link:
 - [PC clock adjustment](https://askubuntu.com/questions/800914/clock-shows-wrong-time-after-switching-from-ubuntu-to-windows-10/800965)

At that point, you are pretty much done. Congratulations!
Before any add-on, set up the boot sequence for your machine. If the sequence can be interrupted like on a desktop, it’s easy. On a laptop, it may be useful to get Ubuntu to boot first, then Windows loader can be chosen from the GRUB boot screen.
The clock may need to be adjusted between Ubuntu and Windows.

### Install on a Surface device
Link:
 - [For Surface series](https://www.reddit.com/r/SurfaceLinux/comments/7kb1ky/guide_installing_linux_on_surfaceseries_devices/)
- [JakeDay's repo on GitHub](https://github.com/jakeday/linux-surface)

Due to the touch functions and some Microsoft idiosyncrasies, the process is a bit more involved. See the link here.
To get the touch screen and pen to work, use the patches and modified Kernel from JakeDay’s repo on GitHub. It also lists what works or not for a Surface device.
Git will need to be installed first.
NB: The clock adjustment is now part of Jake’s installation script.

### Linux for Fullstack Academy
Links:
- [Linuxbrew](http://linuxbrew.sh/)
- [Updating Linux Kernel](https://itsfoss.com/upgrade-linux-kernel-ubuntu/)
- [Things to do after 18.04 install](https://linuxconfig.org/things-to-do-after-installing-ubuntu-18-04-bionic-beaver-linux)

You may want to get Linuxbrew first, though it is really optional . Next step would be to install an updated kernel, as 18.04 ships with Linux kernel 14.5.0, staying with the stable versions of course. Note that updating the kernel on a Surface device should happen before installing the custom kernel assembled by Jake Day. In addition, it is better to upgrade the kernel to the corresponding version of the custom kernel.

If the latest stable Surface kernel is 14.17.3, **do not upgrade to a higher version kernel**.

Then, there are a few things which can be installed. See _Things To Do After 18.04 Install_ for some bloatware clean-up. Most of the games can be removed for instance.

### Starting with the basic
Links:
- [Git](https://www.digitalocean.com/community/tutorials/how-to-install-git-on-ubuntu-18-04-quickstart)
- [NVM](https://github.com/creationix/nvm)
- [Curl](https://linuxhint.com/install-curl-on-ubuntu-18-04/)
- [NodeJS](https://linuxconfig.org/how-to-install-node-js-on-ubuntu-18-04-bionic-beaver-linux)

From experience, it is best to start with Git, Curl, NVM and NodeJS in this order.
Xcode tools and ITerm2 are nice to have but Mac only. The equivalent apps can be found pretty easily. On the other hand, the native Bash terminal is quite sufficient to start with.

There are a few ways to install NodeJS. For Ubuntu, the most reliable is through NVM (Node Version Manager).
Simply follow the  directions in the 2 links provided, starting with NVM then NodeJS. It seems to be best to stick with a LTS version of NodeJS at the start. Having NVM will allow to manage and switch between different NodeJS versions.
Do not try to install NPM (Node Package Manager), as it comes already with the NodeJS installation.

### Installing PostgreSQL - part 1
Links:
- [PostgreSQL installlation](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-postgresql-on-ubuntu-18-04)
- [PostgreSQL](https://help.ubuntu.com/community/PostgreSQL)

This is a necessary item and note that other DBMs can be installed. The particular process for eac one may be different, so it is better to consult their own documentation. Be cautious and take it slow, this part is pretty involved and can go sideways easily.

First, open a CLI window with `Alt + T` and update/upgrade the Ubuntu machine.
```js
User@Linux~$ sudo apt update

User@Linux~$ sudo apt upgrade
```
Follow the directions to install Postgres then create a super-user. The username should be the same one registered for Ubuntu. This will happen with the following commands still in the CLI terminal:
```js
User@Linux~$ sudo apt-get install postgresql postgresql-contrib

User@Linux~$ sudo -u postgres createuser --superuser <$YOUR_USERNAME>

User@Linux~$ createdb $USER
```
In doubt, try using `psql` by typing it in the CLI terminal. The error will show which username is needed. The password can be left blank. The last step is to put the trust in the `pg_hba.conf` file. Literally.

Nano will be used to edit this file. Start in your home prompt in the CLI terminal by typing the following. The latest version number as of August 2018 is 10.4. __The number to type is 10, not 10.4__
```js
User@Linux~$ sudo nano /etc/postgresql/VERSION_NUMBER_HERE/main/pg_hba.conf
```
Replace the `md5` values by `trust`, moving with the arrows and typing in the same exact spot. The file should look like this:

 ![pg_hba.config]({{ site.baseurl }}/images/pbhgaConf.png)

Confirm with `CTRL + O`, then `ENTER`, and exit with `CTRL + X`. Go back to home with `cd ~`.

At that stage, check with psql that the postgreSQL server can be accessed. This is pretty much it, and should allow all the labs, workshops and personal projects  to interact with postgreSQL through the scripts in place. Note that it may be necessary sometimes to create the database first then proceed to the npm set-up.
NB: restart postgreSQL by closing the CLI terminal and reopening then typing `psql`. Alternatively, type:

```js
User@Linux~$ sudo service postgresql start

```
### DBeaver : installation and configuration
Links:
- [DBeaver documentation](https://github.com/dbeaver/dbeaver/wiki/User-Guide)
- [DBeaver install](https://github.com/dbeaver/dbeaver/wiki/Installation)

DBeaver is a complete DB Admin tool which can handle all the needs one may have regarding database inspection and management. Postico is a simple tool on Mac OS, and DBeaver offers the same features and way more. Setting up the connection in DBeaver can be a tad tricky. First, the JDBC driver needs to be installed, via the tab Driver.

The connection parameters are mainly the user previously created, and the relevant password, if implemented. Nte that having set a password can add some complexity if a script in `package.json` accesses the database for a particular app. Check in the DB window if the `<your_user>` database can be accessed, even if it is presently empty.

### Which browser and IDE?
Firefox is a good option, but Chrome or its open source twin Chromium are probably better for development. Just the debugger, if it’s the only aspect considered, is so worth the install. On the other hand, Firefox Inspector is quite good too. Your choice, or load them both.

### Text Editor
Links:
- [Visual Studio Code](https://code.visualstudio.com/download)
- [VSC install](https://code.visualstudio.com/docs/setup/linux#_installation)

As editor, Visual Studio Code is a great choice. Atom is another one, as well as Sublime or Vim. Due to its real nice extensions and great interaction with GitHub, VSC is also my favorite. Your choice…
The missing tool here is GitHub Desktop which is a very useful piece of software. It helps a lot when managing complex projects, repos and Git. It is available on Win10 and MacOSX, though… If really needed, it is easy to switch to Win10 and apply the fix in the GitHub Desktop. Most of this section is based on Fullstack Academy Tool Box set-up, and can vary according to the desired environment and personal preferences.

ESLint and Prettier can be installed as local dependencies, or globally, as shown here. Again, start from a CLI terminal as home:

```js
User@Linux~$ sudo npm install -g eslint eslint-config-fullstack eslint-plugin-react babel-eslint
User@Linux~$ sudo npm install --global prettier
User@Linux~$ sudo npm install eslint-config-prettier --global
```
Once done, starting as home as always, create a `config.json` file for ESLint with nano:
```js
nano ~/.eslintrc.json
```
It should have the following code:
```js
{
  "extends": ["fullstack", "prettier", "prettier/react"],
  "parser": "babel-eslint",
  "rules": {
    "semi": [1, "always"],
    "react/prefer-stateless-function": [0]
  }
}
```
Confirm with `CTRL + O`, then `ENTER`, and exit with `CTRL + X`.

In Visual Studio Code, open the Settings (little gear in the bottom left corner), and add the following to the User Settings. This is again from Fullstack Academy and may vary depending on preferences and/or project.
```js
{
    "editor.renderIndentGuides": true,
    "editor.renderWhitespace": "boundary",
    "editor.renderControlCharacters": false,
    "editor.rulers": [80, 100],
    "editor.tabSize": 2,
    "editor.trimAutoWhitespace": false,
    "editor.wordWrap": "on",
    "files.trimTrailingWhitespace": true,
    "files.insertFinalNewline": true,
    "editor.formatOnSave": true,
    "files.associations": {
        ".gitignore": "shellscript"
    },
    "emmet.syntaxProfiles": { "javascript": "jsx" },
    "window.title": "${activeEditorMedium}${separator}${rootName}",
    "workbench.colorCustomizations": {
        "editorWarning.foreground": "#ec0"
    }
}
```
### So much to chose from...
The Ubuntu and Linux community is very much alive and kicking. With a little research and some keen eyes, a lot can be mined and installed to make coding easier. Up to you!
Nevertheless, some advice is needed. Frequently, apps and software are at the experimental stage or very new. Bugs and flaws can be frequent. As it is often the case, use your best judgement and it may be better to err on the side of caution, unless one may feel comfortable with experimenting.

### A few notes
__Storage__: Ubuntu does not need a huge amount of disk space. First it is a very compact OS, though other Linux distributions are even more lightweight. The trick is that the disk space under Windows management can be accessed from Ubuntu. Just mount and unmount the disk, and get some folders created to use that additional storage space.

__Power management__: This is a minus for Linux in general, it is not good at managing the power consumption. On a desktop, not such a big deal; on a laptop the battery will be eaten up 30 to 50% faster than with Windows. Just be aware of it. On top of that and depending on the machine, the battery level may also not be visible. This is even more true for Surface devices, which can get rather hot under heavy workload.


### Some useful stuff
Links:
- [Installing Postman](https://itrendbuzz.com/install-postman-native-app-on-ubuntu/)
- [Psql cheat sheet](http://www.postgresqltutorial.com/postgresql-cheat-sheet/)
- [Tweaks](https://linuxconfig.org/how-to-install-tweak-tool-on-ubuntu-18-04-bionic-beaver-linux)

At this point, the machine is pretty well stacked. Some of the following can be very useful:
1. Postman: highly recommended, great for testing routes and middleware / backend results.
2. Psql cheat sheet: The kind of handy link to have somewhere, just in case.
3. Tweaks: it adds some nice features, especially a battery indicator. Works on single battery laptops, not the Surface Book 2 :(
4. Nodemon: very useful package for reloading an app through NodeJS
5. Testem: another package for TDD. It works with Jasmine, Mocha-Chai, among others.

### Testing
All those modifications have been tested on:
Custom-built desktop PC i-5 4690K overclocked, 16GB RAM, 2TB storage (SSD/2HD), GTX 1070 NVidia 8GB,
Surface Pro tablet (2017) i-7, 8GB RAM, 256GB SSD,
Surface Book 2 i-7, 16GB RAM, 1TB SSD,  GTX 1060 NVidia 8GB.
All are running Windows 10 - April 2018.

_Microsoft, Windows, Windows 10 are trademarks of Microsoft Corp. MacBook Pro is a trademark of Apple Inc. Ubuntu is a trademark of Canonical Inc. UK._

_Thanks to Dakota Blair and the whole team at Fullstack Academy for their precious help._