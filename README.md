
# AppArmor Security Profiles for some applications

Author: Nibaldo González (<nibgonz@gmail.com>)

Last Change: March 17, 2017

## Description:

AppArmor security profiles for:
* Bomi
* Chromium
* Firefox
* KTorrent
* Opera
* qBittorrent
* Telegram
* Thunderbird
* VLC

Note: The following profiles had problems updating to KDE Applications 16.12.3:
* Gwenview
* Okular
Use in compliant mode to wait to correct the error.

These are designed to work on KDE Plasma 5, 
so these have not been tested in other desktop environments. 

The profiles have been tested in Ubuntu 16.04 & KDE Plasma 5.9. 

If you use Ubuntu, please install the packages 
`apparmor-profiles` & `apparmor-profiles-extra`.

## Important:

* Some profiles require you to review the location of the downloads and desktop directories. By default it is used:
	Downloads Directory: `@{HOME}/Descargas/`	
	Desktop Directory: `@{HOME}/Escritorio/`
	
* The profiles of KTorrent and qBittorrent use the directory `@{HOME}/Descargas/Torrents/` to save the downloads. You must modify this according to your configuration.

* Check the location of the Telegram executable. The profile uses: `/home/*/.TelegramDesktop/bin/{Telegram,Updater}`.

* In the Opera profile, the executable path is `/usr/lib/x86_64-linux-gnu/opera/opera`. Modify if your architecture is not x86_64. Could be: `/usr/lib/*-linux-gnu/opera/opera`

## Installation:

1. Copy the files in: `/etc/apparmor.d/`

	Please do so with great caution!

2. Enable profile in enforcing mode: 

	`sudo aa-enforce /etc/apparmor.d/usr.bin.profile`
	
	- For all profiles: `sudo aa-enforce /etc/apparmor.d/*`
	
	- If you need to reload a profile: `sudo apparmor_parser -r /etc/apparmor.d/usr.bin.profile`
	
	- For profile in compliant mode: `sudo aa-complain /etc/apparmor.d/usr.bin.profile`

3. View profiles status: 

	`sudo apparmor_status`


