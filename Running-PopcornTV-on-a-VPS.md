## Introduction

This guide will explain how to install and run PopcornTV on a Raspberry Pi. These instructions have been tested on a Raspberry Pi B+ with default Raspbian OS installed via NOOBS.

For help installing an operating system like NOOBS on your Pi, check the [official Raspberry Pi documentation](https://www.raspberrypi.org/help/noobs-setup/).

## Finding your Pi

After you install the operation system and plug your Pi into your network (and into power), you'll need to locate it so you can `ssh` into it and run some commands.

The default "Raspbian" OS will automatically broadcast its present on your network under the mDNS name "Pi". If you are using Mac or Linux, you can reach your Pi easily:

```sh
ssh pi.local
```

The default username for Raspberry Pi is usually `pi` and the default password is `raspberry`.

If you have a different OS installed on your Pi or you can't find it via `pi.local` then you can try connecting to your home router by pointing your web browser at somewhere like [http://192.168.0.1](), [http://192.168.1.1](), [http://10.1.1.1]() etc. (this depends on the router you're using and your network setup). Once you are logged in, you can usually find a list of devices connected to your network under "DHCP".

On Windows, you can't type `ssh` but you can use a free tool like [Putty](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html) to connect to your Pi.

## Basic setup

Once you're logged into your Pi, you should begin by updating the default system packages (note that these commands may be different if you are not running Raspbian OS).

```sh
sudo apt-get update
sudo apt-get upgrade
```

## Install Node

The easiest way to install Node is by using the prebuilt arm64 version hosted by a 3rd party:

```sh
echo "deb http://node-arm.herokuapp.com/ /" | sudo tee --append /etc/apt/sources.list
sudo apt-get update
sudo apt-get install node
node -v
```

*Note: This particular guide is using debian "wheezy" and node v.12.2 which was compiled using [this method](http://conoroneill.net/node-v0122-for-arm-v6v7-including-raspberry-pi-raspberry-pi-2-and-odroid-c1). I haven't tested PopcornTV with debian "jessie" or node v4.0.0.*


## Proceed as Usual

Now you can simply follow the instructions in the [README](/OsterlDev/PopcornTV) to install PopcornTV and start it up.

## Running PopcornTV on Bootup

If you would like your Pi to start up PopcornTV automatically on reboot, you will need to install an "init script". This free [init script template](https://github.com/fhd/init-script-template) is a great place to start.

For example, first go to the [raw template file](https://raw.githubusercontent.com/fhd/init-script-template/master/template) and select the whole page and copy it to your clipboard. Then connect to your pi:

```sh
ssh pi.local
sudo nano /etc/init.d/popcorntv
[paste clipboard contents]
```

Now you'll need to modify the top of the file. Here's an example:

```sh
#!/bin/sh
### BEGIN INIT INFO
# Provides: popcorntv
# Required-Start:    $network $remote_fs $syslog
# Required-Stop:     $remote_fs $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start daemon at boot time
# Description:       Enable service provided by daemon.
### END INIT INFO

dir="/home/pi/PopcornTV"
cmd="DEBUG=* node atv.js"
user="root"
```

This assumes you have installed PopcornTV to `/home/pi/PopcornTV`. Note the defining of "popcorntv" for "Provides" in the header (that's important).

Now type CTRL+o to save, then enter, then CTRL+x to exit. Now change the file permissions and "install" the script:

```sh
sudo chmod 755 /etc/init.d/popcorntv
sudo update-rc.d popcorntv defaults
```

It should now run when your Pi reboots. You can also start it up manually like this:

```sh
sudo /etc/init.d/popcorntv start
```

To view the running logs, you can `tail` the output log or error log:

```sh
tail -f /var/log/popcorntv.log
tail -f /var/log/popcorntv.err
```