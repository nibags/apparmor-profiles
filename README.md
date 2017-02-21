
# AppArmor Security Profiles for some applications
	Author: Nibaldo González Salgado

	Last Change: February 20, 2017

## Description:

Some AppArmor security profiles. 
These are designed to work on KDE Plasma 5, 
so these have not been tested in other desktop environments. 

The profiles have been tested in Ubuntu 16.04 & KDE Plasma 5.9. 

If you use Ubuntu, please install the packages 
`apparmor-profiles` & `apparmor-profiles-extra`.

## Installation:

1. Copy the files in: `/etc/apparmor.d/`

	Please do so with great caution!

2. Profile in enforcing mode: 

	`sudo aa-enforce /etc/apparmor.d/usr.bin.profile`
	
	For all profiles:
	
	`sudo aa-enforce /etc/apparmor.d/*`

3. View profiles status: 

	`sudo apparmor_status`
