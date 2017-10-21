Getting Started with BeagleLogic Standalone
===========================================

Using PulseView
---------------

PulseView is the GUI client for the `sigrok <https://sigrok.org>`_ set of tools
for logic analysis and is a powerful Logic Analyzer client that supports a
variety of logic analyzers. It is currently the preferred way to use
BeagleLogic Standalone after the addition of the TCP Server to BeagleLogic.

Download PulseView for Windows and Linux from
`this folder <https://goo.gl/7z1w7h/>`_ (choose your folder accordingly)

At this point, BeagleLogic Standalone should be plugged in to your PC and
booted. You should know the IP address of the BeagleLogic Standalone board which
would usually be **192.168.7.2** if it is connected via USB or if it is connected
to your local network via LAN, then please find the IP address using ifconfig.

Linux
#########

On Linux, PulseView is a 64-bit AppImage. It must be marked executable after a
successful download. To do so, either do this on a command line::

    chmod +x <path-to-download-folder>/PulseView.AppImage

Or right click the AppImage file, select "Properties", click on "Permissions"
tab and select "Allow Executing File as program"

To launch PulseView, double-click on the AppImage file. You might want to create
a desktop launcher for it.

Windows
#########

On Windows, PulseView is installable. Click on the setup file, follow the
instructions and install PulseView. Launch PulseView.

After install
#############

Please watch the following set of videos which cover how to set up PulseView,
add triggers to a capture and access protocol decoding.

You can also refer to this `setup guide <https://goo.gl/L9QUrt>`_ document that
covers the bootstrapping of BeagleLogic Standalone board.

.. raw:: html

   <div><iframe width="560" height="315" src="https://www.youtube.com/embed/videoseries?list=PLB51hk_14f3J-1lEdxEh9aeD_5S1x3CJ7" frameborder="0" allowfullscreen></iframe></div>

The Web Interface
-----------------

The web Interface of BeagleLogic is currently very basic. It does not support
zoom or save functionality but is a quick way of visualizing some samples if
that's what you want to do. It is the quickest way of getting started with
BeagleLogic Standalone.

To access the web interface, open http://<ip-address-to-BeagleLogic-board>:4000
in a browser.

On the left hand corner, select the channels you want to capture by ticking the
corresponding check boxes. You can also label the inputs with custom text.

Click on "Begin Capture". Samples should be captured and then rendered on the
screen.

The Command line
----------------

The command line interface of BeagleLogic Standalone is the most advanced in
terms of functionality as it allows you to capture and decode samples on the
BeagleLogic Standalone board itself.

To access the command line interface you need to SSH into the board. On Linux this
is simple, but on Windows, one needs to install
`PuTTY <https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html>`_ for this

The username is "debian" and the password by default is "temppwd".

Once you open a SSH session, you can use the sigrok-cli command line tool to
capture and analyze data. The basic command to do a capture and save it to a file
is as follows::

    sigrok-cli -d beaglelogic -c samplerate=10M --samples 1M --channels 0,1,2,3,4,5 -o file.sr

The switches are “-d” (driver name: beaglelogic in this case), “-c” (configure),
“samplerate=<samplerate>”, “samples” (limit capture of samples up to the set
limit), “channels” (select which channels to sample, omit this to select all
channels from 0 to 15), “-o” (output file name).
