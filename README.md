
# AppArmor Security Profiles for some applications

**Author:** Nibaldo González (<nibgonz@gmail.com>) (Valparaíso, Chile)

## Description:

AppArmor profiles for:
* Baka-MPlayer
* Baloo (extra)
* Bluetooth Daemon
* Brave (extra)
* Chromium
* Firefox
* Gwenview
* KTorrent
* mpv
* Okular
* Opera
* qBittorrent
* Telegram (extra)
* Thunderbird
* Vivaldi (extra)
* VLC 2.2 (extra)
* youtube-dl

**NOTE:** The profiles in the *extra* folder are not tested frequently!

These are designed to work on KDE Plasma 5. 
All profiles have been tested on Ubuntu 16.04 & KDE Plasma 5 (in Xorg and Wayland).

If you use Ubuntu, please install the packages 
`apparmor-utils` & `apparmor-profiles`.

## Important:

* Some profiles require you to review the location of the downloads and desktop directories. By default it is used:
	* Downloads Directory: `@{HOME}/Descargas/`
	* Desktop Directory: `@{HOME}/Escritorio/`
	
* The profiles of KTorrent and qBittorrent use the directory `@{HOME}/Descargas/Torrents/` to save the downloads. You must modify this according to your configuration.

* Check the location of the Telegram executable. The profile uses: `/home/*/.app/Telegram/{Telegram,Updater}`.

* For the profiles to work correctly, in the file `/etc/apparmor.d/tunables/global`, add the line:
```c
#include <tunables/confidential>`
```

## Installation:

1. Copy the files in: `/etc/apparmor.d/`
	
	Please do so with great caution!
	
2. To enable a profile, in enforcing mode, use the following command:
```bash
sudo aa-enforce /etc/apparmor.d/usr.bin.profile
```

* For example, you can use:
```bash
sudo aa-enforce /etc/apparmor.d/usr.bin.*
sudo aa-enforce /etc/apparmor.d/home.*
sudo aa-enforce /etc/apparmor.d/usr.lib.bluetooth.bluetoothd
```

* If you need to reload a profile:
```bash
sudo apparmor_parser -r /etc/apparmor.d/usr.bin.profile
```

* For profile in compliant mode:
```bash
sudo aa-complain /etc/apparmor.d/usr.bin.profile
```
	
* **NOTE:**
	* In Ubuntu, you need to install the `apparmor-utils` package to use the `aa-enforce` and `aa-complain` commands.
	
	* It is also enough to restart the computer to enable the profiles.
	
3. View profiles status: 
```bash
sudo apparmor_status
```
