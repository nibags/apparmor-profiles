
# AppArmor Security Profiles for some applications

**Author:** Nibaldo González (<nibgonz@gmail.com>)

## Description:

AppArmor profiles for:

* Bluetooth Daemon
* Brave
* Chromium
* Firefox
* Gwenview
* KTorrent (not tested in latest versions!)
* mpv
* Okular
* Opera (not tested in latest versions!)
* qBittorrent
* Thunderbird
* Vivaldi
* youtube-dl (extra)

**NOTE:** The profiles in the *extra* folder are not tested frequently!

These are designed to work on KDE Plasma 5. 
All profiles have been tested on Ubuntu 18.04 & 16.04 with KDE Plasma 5. 

If you use Ubuntu, please install the `apparmor-utils` package.

## Important:

* Some profiles require you to review the location of the downloads and desktop directories. By default it is used:
	* Downloads Directory: `@{HOME}/Descargas/`
	* Desktop Directory: `@{HOME}/Escritorio/`
	
* The profiles of KTorrent and qBittorrent use the directory `@{HOME}/Descargas/Torrents/` to save the downloads. You must modify this according to your configuration.

* Check the location of the Telegram executable. The profile uses: `/home/*/.app/Telegram/{Telegram,Updater}`. NOTE: The Telegram profile is unmaintained; for sandbox, use the Flatpak or Snap package.

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
