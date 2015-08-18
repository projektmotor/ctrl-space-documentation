# Ctrl-Space Installation #

Before installing Ctrl-Space you have to download the latest version of Ctrl-Space from [the Download-Page](http://ctrl-space.projektmotor.de).
Ctrl-Space is available for Linux, Mac and Windows.

## Pre-Installation Requirements ##

### Install Java JDK 8 or later ###

Depending on the OS (and Version) there are different ways to install Java JDK 8 or later.

#### On Linux ####

For most of the Linux distributions it is possible to install java via your package manager (e.g. apt on Debian). If not, follow the steps of 
[On Linux, MacOS and Windows][].

#### On Linux, MacOS and Windows ####

* [Download](http://www.oracle.com/technetwork/java/javase/downloads/index.html) the JDK 8 for your Operating System from Oracle
* Install the JDK 8 (see [Oracle Documentation](https://docs.oracle.com/javase/8/docs/technotes/guides/install/install_overview.html))
* test the JDK installation by entering the following into a Terminal:

```
    java -version
```

If the resulting output is a JAVA version number greater than 1.8 you are fine. Otherwise try our FAQs first, then a 
google search on java installation issues or consult our forums and mailing lists.

## Install Ctrl-Space ##

Now that we have installed Java JDK, we can continue installing Ctrl-Space. The process of installation differs, depending
on the type of OS you have.

### Linux ###

* open a terminal
* navigate to the archive directory
* untar the archive
```
$ tar -xvf ctrl-space-[OS].tar.gz
```
* make install script executable
```
$ chmod +x controlspace-linux.sh
```
* execute the installer
```
$ ./controlspace-linux.sh
```
* follow the installation instructions

![Linux Installer](/images/installer-linux.png)

* after installation you can run ctrl-space by executing
```
$ ./CTR-INSTALL-PATH/bin/controlspace
```

### MacOS X ###

On MacOS X the installation is a bit easier than on linux systems.

* open the Finder
* untar the archive
* open the installer
* follow the installation instructions
* after installation you can run ctr-space, as any other application, by double click the app icon

### Windows ###

coming soon!

## Install Ctrl-Space JS Bridge

The JS Bridge is a set of JavaScript files. In those files an API is defined to fit the needs of web developers who are used to code JavaScript.
Since the Java API is more complicated to read and write we decided to wrap it up.

The bridge is not loaded automatically. You have to download it from our outlet or clone it from our git repository.


Download directly from the [Software outlet:](http://outlet.controlspace.intranet.projektmotor.de/Blueprints.zip)

OR

Clone from git:

* go to `USERDIR/controlspace.data/`
* remove the folder `js-bridge`
* clone repository
```Bash
$ git clone https://github.com/projektmotor/ctrl-space-bridge.git js-bridge
```

After adding the newly cloned folder as "js-bridge" in the "Manage Libraries" dialog, all libraries will be reloaded automatically and can be used immediately.

To Update the JavaScript bridge, you can call `git pull` from the `USERDIR/controlspace.data/js-bridge` directory. 

## Install Ctrl-Space Standard Blueprint Library

To get a default set of Blueprints and make use of Ctrl-Space's image data extraction features, you need to load the Standard Blueprint
Library (SBL). As with the JS Bridge, you can download the [SBL directly] (http://outlet.controlspace.intranet.projektmotor.de/Blueprints.zip)

OR

* go to `USERDIR/controlspace.data`
* remove the folder `blueprints`
* clone repository
```Bash
$ git clone https://github.com/projektmotor/ctrl-space-sbl.git blueprints
```

After adding the newly cloned folder in the "Manage Libraries" dialog, all libraries will be reloaded automatically and can be used immediately.

To Update the Ctrl-Space Standard Blueprint Library, you can call `git pull` from the `USERDIR/controlspace.data/blueprints` directory.

## Install PSDConverter

To make Ctrl-Space work with Photoshop files (PSD), the PSD Converter is used.
It converts PSD files to our own special image format, the CSImage (*slim, *.csi).
Basically a CSi file is a zip containing png files and an xml meta file.

During conversion all layers inside a PSD file will be rasterized (including effects, masks, etc) and stored as single PNG files.
Meta information about the layers (position, size, text, text styling, ...) will be stored in the XML meta file of the archive.

To make your life easier we built a small Java application to communicate between a Ctrl-Space instance an a Windwos PC running Photoshop.
When opening a PSD file in Ctrl-Space, the converter server will be called, PSD file will be uploaded and after converting it to CSImage it's send beck to your Ctrl-Space instance and automatically opened.

This way you can remotely convert PSD files on one Windows machine for all Ctrl-Space clients of your company.

The PSDConverter Server works on Windows 7+. OS X support will be added on request.


### On PSDConverter Host

Before installing PSDConverter make sure you have Photoshop CC and .NET Framework 4.6.1+ installed correctly.

* download `PSD2Slim.Export.zip` from `http://outlet.controlspace.intranet.projektmotor.de/PSD2Slim.Export.zip`
* unzip the archive
* go to unzip location and open `server.cmd`
* enter the IP of the Windows system
    * if you run the PSDConverter on the same host as Ctrl-Space, enter `127.0.0.1`
    * if you run on another host, enter a IP which is reachable from the Ctrl-Space host

To start the Java server, execute the `server.md` command.

### On Ctrl-Space Host

Now it is time to tell Ctrl-Space where to find the server which
is wrapping the PSDConverter. 

* open Ctrl-Space and go to `Tools` > `Options` > `Slim Converter`
* enter IP/Port of the host running the PSDConverter (default port: 40000)
* click `Apply` and close the options window
