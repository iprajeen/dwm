# dwm - dynamic window manager
![dwm-logo](https://fedoramagazine.org/wp-content/uploads/2019/03/dwm-magazine-image-816x345.png)

dwm is an extremely fast, small, and dynamic window manager for X.

#### So why this fork any way?
This fork is mainly for personal usage. This is purely intended to support **Gentoo**'s patch system and includes all my 
favourite patches from [suckless.org](suckless.org/dwm/patches) tinkered to support the version found in Portage build system.

## Requirements
In order to build dwm you need the Xlib header files.


## Installation
#### Using ```emerge```
Edit ```config.def.h``` to match your usage and create a patch file for it using the command:

    git diff | tee patches/dwm-personal.patch

Clone this repo and copy all the ```.patch``` files in **patches** to ```/etc/portage/patches/x11-wm/dwm-6.2``` and run ```emerge dwm```.

#### or, using the great old method
Edit config.mk to match your local setup (dwm is installed into
the /usr/local namespace by default).

Afterwards enter the following command to build and install dwm (if
necessary as root):

    make clean install


## Running dwm
Add the following line to your .xinitrc to start dwm using startx:

    exec dwm

In order to connect dwm to a specific display, make sure that
the DISPLAY environment variable is set correctly, e.g.:

    DISPLAY=foo.bar:1 exec dwm

(This will start dwm on display :1 of the host foo.bar.)

In order to display status info in the bar, you can do something
like this in your .xinitrc:

    while xsetroot -name "`date` `uptime | sed 's/.*,//'`"
    do
    	sleep 1
    done &
    exec dwm


## Configuration
The configuration of dwm is done by creating a custom config.h
and (re)compiling the source code.


## Patches

- **Colorbar:** Allows to change color of each and every segment of dwm bar
- **Hardware volume control:** Allows to control volume through function keys (supports only pulseaudio)
- **Pertag:** Allows us to have different mode for each tag (modifies global mode policy)
- **Vanitygaps:** Purely for aesthetic reason, adds gaps around windows which can be varied through key bindings
