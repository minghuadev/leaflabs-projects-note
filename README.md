leaflabs-projects-note
======================

#FORK

leaflabs-projects forked from 

  https://github.com/leaflabs/projects


#BLOG

See blog at http://leaflabs.com/2011/09/pymite/:

We've got our blink on... Python style!

If you haven't had a chance to check out the specs on Maple Native:

    72MHz
    1MB external SRAM
    DACs
    I2Cs
    SPIs
    UARTs
    ADCs
    FSMC

To summarize, its got some junk in the trunk.

Last week we had a meeting to figure out a good way to demonstrate why EVERYBODY will not be able to live without it, and AJ chimes in with: "Has anybody played around with PyMite?"

PYTHON!... on a microcontroller! That you can interact with!  At runtime! Tooo good to be true.

Took me a week of randomly banging on a keyboard but yesterday we typed blinky into interactive pymite (IPM) and... let's just say I'm giddy.


* Roughly, under "projects/pmvm/platform/maple", type "make IPM", you'll be connected to the interactive PyMite. Then you can run the demo code. 


Anyway, we think it might be ready for some users to play around with. It's still rough around the edges, but if you've got a Maple Native or a Maple RET6 Edition and want to partake in some luscious Python goodness, then grab the latest release from our projects repo on GitHub (sorry, but this little slice of heaven is currently only usable from the command line toolchain):

$ git clone git://github.com/leaflabs/projects.git

Then follow the hastily written up instructions on the wiki.

Dave


#WIKI

The instruction is on the wiki from http://wiki.leaflabs.com/index.php?title=PyMite .

Python-on-a-Chip (P14P) is software for running Python (via the PyMite virtual machine) on microcontrollers without an OS.
Contents

    1 PyMite port for Maple
    2 Maple Native Support
    3 How to Build
    4 How to set up Interactive PyMite (IPM)
    5 Working with Interactive PyMite (IPM)

### PyMite port for Maple

PyMite takes up a relatively large amount of room: roughly 73kB in Flash and 40kB in RAM. Although the size in RAM can be adjusted, the large resource footprint restricts PyMite to either Maple RET6 or Maple Native.

### Maple Native Support

What good is Python if all you can do is print "Hi" and set variables? PyMite is capable of controlling all the peripherals of Maple. The libraries are a work in progress, but blinking the LED is fully supported at this time.

### How to Build

* The command-line toolchain must be installed and the environmental variable $LIB_MAPLE_HOME must be exported for the Makefile to find it 

* unfortunately PyMite is extremely sensitive to the version of Python being used on the host and as of now the only version that has successfully been tested is Python 2.6.5. One easy way to get this done (on Ubuntu) is by obtaining the source, making and install it then changing the symbolic link within /usr/bin/python2.6 to point to python2.6.5. If you don't want to change your symbolic link for python2.6 you can change scripts within pmvm/tools to point to your local version of 2.6.5 

* PySerial is required to communicate with the MCU and if downgrading/upgrading to Python 2.6.5 is required, then so is installing PySerial for Python 2.6.5. Ugh. Download the source from pyserial and after setting up Python 2.6.5 go into that directory and type 


    $ python2.6 ./setup.py

* get our source from GitHub: 


    $ git clone git://github.com/leaflabs/projects.git

* change to the pmvm/platform/maple directory 

* run 


    $ make clean
    $ make
    $ make install

The compiled program should upload to the Maple Native.

### How to set up Interactive PyMite (IPM)

Interactive Pymite IPM requires a Python script on the host to communicate with the MCU interpreter. You'll also need a USB-to-serial adapter to connect to the Maple Native. Connect the adapter to Serial3 TX and RX (pins 0 and 1). (Don't forget to ground the adapter as appropriate).

Here's how to start it up: 

In the pmvm/platform/maple directory,

    $ ../../tools/ipm.py -f pmfeatures.py --serial=/dev/<Serial Device> --baud=<Baudrate>

As an example, my TTL USB serial device is found at /dev/ttyUSB0 and has a baudrate of 115200, so I type:

    $ ../../tools/ipm.py -f pmfeatures.py --serial=/dev/ttyUSB0 --baud=115200

It's possible to use the built in USB Serial port, but both main.cpp and plat.cpp must be modified.

### Working with Interactive PyMite (IPM)

Just type Python at the prompt:

    this .. that .. 

#OTHEER

http://embeddedpython.org/index.php?title=The_Owl_Embedded_Python_System

The release combines work from:

    Dean Hall's Python-on-a-Chip
    libffi
    Python 2.7
    libopencm3
    Texas Instruments Stellaris Driverlib 


title1
======

title2
------

line

-----

line
