VERSION

V.1.11.1

--------------------
DISCLAIMER

-This BASH script was created by Cooper Van Kampen
-This BASH script is licensed under the GPLv3
-This BASH script was created with the intent of providing a simple, immediate way 
to connect to IIT-Secure.
-The version numbers of this BASH script can be read as follows:
	- V.#.$.%
		-# is the major version; large important changes.
		-$ is the minor version; small changes.
			-Even means stable
			-Odd means unstable
		-% is the working version; tiny changes that occur during the coding
		process that help track changes.

--------------------
USAGE

TO START:
-You need these programs installed:
	-wpa_supplicant
	-A DHCP Client
		-Typically dhclient if you are, but possibly dhcpcd or another client
		Debian-based, but dhcpcd is also quite common.
			-Script will attempt to detect one of these two if you do
			not edit the configuration variables.
	-The sudo command and sudo privilege.
	-The ip or ifconfig network command suite

PREPARATION:
-To prepare this BASH script, you must have the ability to execute it. This can be 
done with the following command:

	$ sudo chmod +x connectiitsecure.sh

	-Please note a few things about this command:
		-You will need administrator privileges to run this command.
			-This can be done with the sudo command or by becoming the
			root user.
		-The $ (or # if you are the root user) is not entered into your
		terminal. It is just indicative of the fact that you enter
		what proceeds it into your terminal.
		-This gives anyone the ability to run the shell script.
			-If this is a problem, see further usage of chmod from
			its man page, or a desirable, example rich post on the
			internet.

CONFIGURE:
-This bash script offers several configurable features, mainly:
!	-Wireless interface name
		-The name of your wireless interface.
			-NEEDS to be changed!
			-Since this BASH script currently requires the ip command
			suite, you can find it with the following command:

	$ ip l

				-The name will be in the numbered line, starting
				with a w.
					-For example, wlan0, wlp3s0.
					-NOT enp9s0, en0.
						-Ethernet, not wifi.
			-If your interface was wlan0, simply put it in as follows:

	INTERFACE="wlan0"

	-MAC address
		-Referred to as the "physical address" of your computer, it is the
		way that your network determines which computer is which.
		-WARNING: Setting your MAC address to the same as someone elses is
		a quick way to get your network administrator at your throat. It 
		is dangerous, and you will be caught.
		-If you do not understand, leave the value as is.
	-DHCP client
		-Allows you to request an IP address from the network after you
		connect to it via this script or use of another tool.
		-If you do not understand, that is ok.
			-If the script throws an error message and quits, you
			need to search the internet to find out how to install
			one of these two DHCP clients.
	-DHCP client arguments
		-Allows you to have more granular control over the output that you
		see as the script runs.
	-WPA Supplicant configuration file location and name
		-Can be changed to the location you wish to save the file as long
		as you have the required permissions.
		-If you do not understand, leave the value as is.

START:
-To start this BASH script, enter the following command, assuming you are in the
same directory as the script:

	$ ./connectiitsecure

RUN:
-The script should run you through any remaining steps automatically, however,
here are some important things to remember:
	-You need to have sudo and the privileges to use it.
	-Errors on the DHCP section of the script usually are a result of one
	of the following:
		-Bad interface name
			-Action: Check it and change it if necessary.
		-Wrong DHCP client
			-Action: Adjust the configuration until it matches.
	-Errors on the ping section of the script usually are a result of one
	of the following:
		-Incorrect username and password.
			-Action: Check them. Your username should be your hawk
			email. Change them directly through the conf file you
			located during the configuration step.
		-Incorrect loading of wpa_supplicant or the DHCP request
			-Action: Run the script again. Usually, you are just
			unlucky in this case.

--------------------
FUTURE POSSIBLE FEATURES

-rfkill checking
	-Medium difficulty, medium work, medium impact
-Add checking for root account vs account that you need sudo
	-Low difficulty, low work, low impact
-Automatically encrypt password instead of storing plaintext in wpa conf
	-Medium difficulty, medium work, variable impact
-Create a management script or embed management features in this script which
allow you to change your username and/or password easily.
	-Medium difficulty, high work, high impact
	-May also include automated metamorphic settings changing feature that
	make manual configuration unnecessary.

Send your suggestions to my github (coopervk), my email (coopervk@gmail.com,
cvankampen@hawk.iit.edu), or my Telegram (gdynamics). 

--------------------
OFFICIAL PATCH NOTES

V.1.11.1

-Fixed several typo errors, including but not limited to:
	-Using ping to check connection.
		-" 0%" instead of "0%"
	-MSCHAP typo
		-"MSCHAPV2" instead of "MSCHAPv2"
-Fixed logical error with checking for DHCP Client
	-Remove bangs for negation
	-Not sure if this was always a problem? Didn't see issue on Debian
	-If this is wrong on your system, please, create a bug report
	-This is why version is unstable
