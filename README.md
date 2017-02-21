# apparmor-profiles
AppArmor Security Profiles for some applications
-----------------------------------------------------------------------
Author: Nibaldo González Salgado
Last Change: February 20, 2017

DESCRIPTION:
Some AppArmor security profiles.
These are designed to work on KDE Plasma 5,
so these have not been tested in other desktop environments.

The profiles have been tested in Ubuntu 16.04 & KDE Plasma 5.9.

If you use Ubuntu, please install the packages 
"apparmor-profiles" & "apparmor-profiles-extra".

INSTALLATION:
	Copy the files in:
		/etc/apparmor.d/
	Please do so with great caution!
	
	Profile in enforcing mode:
		sudo aa-enforce /etc/apparmor.d/le.profile
	
	View profiles status:
		sudo apparmor_status
