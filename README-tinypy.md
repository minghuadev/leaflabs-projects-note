
#TinyPy 1.0

http://www.philhassey.com/blog/2008/02/28/tinypy-10-mit-license-and-swell-opengl-demo/

$ python build.py
$ ./tinypy-sdl julia.py *
$ ./tinypy your-program-goes-here.py


#SDL Etc

Ido Yehieli Says:
February 28th, 2008 at 1:05 pm

Phil – how can i run sdl programs directly on the vm? i tried:

$ ./vm py2bc.tpc julia.py julia.tpc
$ ./vm julia.tpc
320 240

File “julia.py”, line 26, in ?
set_mode(SW,SH)

Exception:
tp_get: KeyError: set_mode

----

philhassey Says:
February 28th, 2008 at 1:10 pm

Ido – you’d have to build a vm with the SDL functions built in. Take tinypy-sdl.c and tweak the main function to be more like the main function from vmmain.c. Doing it that way would be useful for distributing a game where you don’t want to support any in-game scripting, or in a case where you really don’t want all that bytecode in memory for some reason.

----

Ido Yehieli Says:
February 28th, 2008 at 1:20 pm

Thanks.

Does that mean that if I use ‘eval’ in my python program i have to provide the tinypy compiler as well as the vm?

----

shaurz Says:
February 28th, 2008 at 1:21 pm

Nice, a nod to “Top Down Operator Precedence” in your parser :-)

----

philhassey Says:
February 28th, 2008 at 1:24 pm

Ido: Yeah, to use eval or similar stuff the compiler must be included so it can dynamically compile the code.

shaurz: Indeed – http://javascript.crockford.com/tdop/tdop.html – was what got me through :) I tried some other approaches, but TDOP really suited me.

----

philhassey Says:
February 28th, 2008 at 1:31 pm

Ido: just to clarify, tinypy includes the VM, so you don’t have to have both “vm.exe” and “tinypy.exe” available for things to work.

----

Harry Roberts Says:
March 1st, 2008 at 11:22 am

Wow, that’s pretty cool. I can get the VM executable down to about 17k (-Os + strip + upx).

I’m thinking of a few things I can add to this, the first thing that comes it mind is transparent .zip file access via zziplib (http://zziplib.sourceforge.net/zzip-file.html) so a project can be distributed as vm + (compiled) code.zip

I’m also pondering an implementation of tasklets/channels/io ala Stackless Python, abusing libevent as a kernel.

Also – where can I send patches in?

----



