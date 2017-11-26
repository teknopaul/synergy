# Synergy FOSS 1.6 before paywalls went up

This fork of synergy is created to build on Linux Ubuntu only.  

refs:

https://www.reddit.com/r/linux/comments/2fydpm/synergy_gpl_input_sharing_software_gone_paid/

Hats off to **lavacano** for forking before the github repo was deleted.

https://github.com/lavacano/synergy/

The idea is to compile an old version that does not have nag-ware or incompatabilities built into the protocol to "encourage" you to upgrade.

Synergy compiles with **cmake**, the compilation instructions are behind a paywall so this project has updated the _./configure_ and _COMPILE_ files to try to make it possible to build synergy on Linux again without much fuss.

[configure](configure)
[COMPILE.md](COMPILE.md)


Ideally to compile we would just run 

	configure && make && sudo ./install

## Running synergy

To ruyn synergy you need tow computers, obviously, one with a keyboard and mouse called the server, nad the other (or others) which will share the keyb and mouse.

_/etc/synergy.conf_ is self explanatory,  use the hostnames of each PC and make sure that each PC has the same notion of hostname. (DNS, /etc/hsots)

	section: screens
	    myserver1:
	    myotherpc:
	end

	section: links
	    myotherpc:
	        right = myserver1
	    myotherpc:
	        left = myotherpc
	end

The default port in _24800_ make sure thats opein in your firewall

	sudo iptables -A INPUT -p tcp --dport 24800 -j ACCEPT

On the server run 

	synergys

If you have multiple network cards (or lxc or docker running) specify the IP to listen on

	synergys -a 192.168.1.23

On the clinet setup the same _/etc/synergy.conf_ and run

	synergyc

