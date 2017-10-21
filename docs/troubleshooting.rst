Troubleshooting
================

Here are some common issues that you might encounter, and how to resolve them:

Not booting (lights not coming on)
------------------------------------
Remove and reconnect the USB cable. If that does not fix it, try pressing the
reset button (the button on the right) and wait for some time. If still no
response, the LEDs do not come on in sequence and start blinking in a pattern,
try connecting a USB-Serial cable on the serial console header
and seeing if you get any output there.

PulseView hangs on scanning for devices
---------------------------------------
First, terminate PulseView manually. Then SSH into the board and execute the
command, “sudo service beaglelogic-tcp restart” (use password “temppwd”).
The next time PulseView should be able to detect the board fine.

The board boots, the lights are blinking, but unable to connect to the board
-----------------------------------------------------------------------------
If on Linux, check using “ifconfig” that two new interfaces have appeared, and
that the IP addresses have been assigned. The PC should be assigned an IP of
192.168.7.1 and/or 192.168.6.1 on Linux.

On Windows, install the drivers first from the USB drive that appears. Then
check under “Device Manager” that there is a new network adapter. Under
“Network and sharing Center”, select the network connection corresponding to
the BeagleLogic standalone board and see the status that it has indeed been
assigned an IP address of 192.168.7.1
