# Conference "The state of Mikrotik security, an overview"

KirisSolovjovs, at Possible Security

Mikrotik RouterOS :
	Based on Linux (really old Linux though)
	With startup scripts
	with Nova binaries
	Use configuration files
	Closed source and closed ecosystem
	Not popular on France (3500 routeurs utilisés)
	
	Like Cisco IOS to use
	
	Complex ecosystem, multiples entry points
	Some entry points discovered via CIA leaks
	
	Known vulnerabilites in products
		CVE-2018-7445 samba
		283i4jfkai3389 : used for key generation by concatening user with the string before hashing, used for the password
		chimay_red : Stack clashing with large Content-Length, able to write code with it
			automated exploit available
		differents CVE availables (samba, winbox, etc...)
		winbox:
			DLL downloading without checking
		CVE-2018-1156
			Authenticated RCE by using network check
		package/option based jailbreak
			use squashfs file to simulate a package to execute code with breaking /rw/DEFCONF

		New method of exploit starting 6.41 and works for current version
			require write access to a precise folder
			use script magic_usb.sh (use of dd) to create usb flash or storage device with write access
			Exploit then jailbreak with storage mounted on device
			once jailbreaked, shell is available 

	Which versions are in use
		Major version 6 in majority
		vulnerables devices still greatly in use (used by russians actually to eavesdrop on network traffic or inject coin miner on computers)
		vulnerable versions on shodan	

	Hardening
		starting to harden devices to prevent exploitation
		Still not enough

	github.com/Oki/mikrotik-tools
	http://kirils.org
	
