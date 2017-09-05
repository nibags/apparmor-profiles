
# AppArmor Security Profiles for some applications

Author: Nibaldo González (<nibgonz@gmail.com>) (Valparaíso, Chile)

Last Change: September 04, 2017

## Description:

AppArmor security profiles for:
* Baka-MPlayer
* bomi
* Chromium
* Firefox
* Gwenview
* KGet
* Konversation
* KTorrent
* mpv
* Okular
* Opera
* qBittorrent
* Telegram
* Thunderbird
* Vivaldi
* VLC
* youtube-dl


These are designed to work on KDE Plasma 5. 
All profiles have been tested on Ubuntu 16.04 & KDE Plasma 5. 
The VLC, Telegram, Thunderbird & mpv profiles were also tested in GNOME 3.

If you use Ubuntu, please install the packages 
`apparmor-utils` & `apparmor-profiles`.

## Important:

* Some profiles require you to review the location of the downloads and desktop directories. By default it is used:
		Downloads Directory: `@{HOME}/Descargas/`	, Desktop Directory: `@{HOME}/Escritorio/`
	
* The profiles of KTorrent and qBittorrent use the directory `@{HOME}/Descargas/Torrents/` to save the downloads. You must modify this according to your configuration.

* Check the location of the Telegram executable. The profile uses: `/home/*/.TelegramDesktop/bin/{Telegram,Updater}`.

* For the profiles to work correctly, add the line: `#include <tunables/confidential>`, in the file: `/etc/apparmor.d/tunables/global`.


## Installation:

1. Copy the files in: `/etc/apparmor.d/`

	Please do so with great caution!

2. Enable profile in enforcing mode: 

	`sudo aa-enforce /etc/apparmor.d/usr.bin.profile`
	
	- For all profiles: `sudo aa-enforce /etc/apparmor.d/*`
	
	- If you need to reload a profile: `sudo apparmor_parser -r /etc/apparmor.d/usr.bin.profile`
	
	- For profile in compliant mode: `sudo aa-complain /etc/apparmor.d/usr.bin.profile`
	
	- NOTE: In Ubuntu, you need to install the `apparmor-utils` package to use the `aa-enforce` and `aa-complain` commands.

3. View profiles status: 

	`sudo apparmor_status`


