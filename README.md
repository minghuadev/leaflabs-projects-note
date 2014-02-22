leaflabs-projects-note
======================


leaflabs-projects forked from 

  https://github.com/leaflabs/projects


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


Roughly, under "projects/pmvm/platform/maple", type "make IPM", you'll be connected to the interactive PyMite. Then you can run the demo code. 


Anyway, we think it might be ready for some users to play around with. It's still rough around the edges, but if you've got a Maple Native or a Maple RET6 Edition and want to partake in some luscious Python goodness, then grab the latest release from our projects repo on GitHub (sorry, but this little slice of heaven is currently only usable from the command line toolchain):

$ git clone git://github.com/leaflabs/projects.git

Then follow the hastily written up instructions on the wiki.

Dave




