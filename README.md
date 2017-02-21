
# AppArmor Security Profiles for some applications

Author: Nibaldo González Salgado

Last Change: February 20, 2017

## Description:

AppArmor security profiles for:
* Bomi
* Chromium
* Firefox
* Gwenview
* KTorrent
* Okular
* Opera
* qBittorrent
* Telegram
* Thunderbird
* VLC

These are designed to work on KDE Plasma 5, 
so these have not been tested in other desktop environments. 

The profiles have been tested in Ubuntu 16.04 & KDE Plasma 5.9. 

If you use Ubuntu, please install the packages 
`apparmor-profiles` & `apparmor-profiles-extra`.

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

## To Do:

Correct failed security profiles (Not included in the repository):
* Clementine: I consider a profile unnecessary for this application. The profile generates some errors.
* Dropbox: Check.
* KGet: Check.
* KWalletd: Failed to upgrade from Plasma 5.8 to 5.9. Correct profile thoroughly.

