# ewozmon4pill6502gen2
<PRE>
This repo is clone of https://gist.github.com/b529a24f39bcbd53f1e21775e24d0b9e.git.
And also an implement for pill6502gen2 branch bellow.
https://github.com/cobwebkanamachi/pill_6502/tree/pio-and-uartbased-mod/new-src
And osi_bas is Grant Searle's bellow.
http://searle.x10host.com/6502/osi_bas.zip on http://searle.x10host.com/6502/Simple6502.html .

1. concept
I think it is available to implement the wozmon on ROM.HEX of Grant Searle's osi_bas and handler.
So experimented.

2. problem
Wozmon 's placement between Basic and Handler.
Page alignment issue.
Several times I fail to implement.

3. design
3.1 Place of wozmon
Not made a segment (in Basic's code segment, after the Basic code, wozmon placed).
3.2 cfg of ld65
After the Basic, wozmon placed, so not changed osi_bas.cfg.
3.3 ACIA
Compatible with Searle's osi_bas's design, tweak ACIA two addresses of ewoz.

4. implementation of mine
Dirty Kludge. So change as you like freely.
There's no explain for my code:-).
Only the codes tell about it.
osi_bas.s includes all(ewoz and msbasic and handler and vectors(6bytes)) for pill6502gen2(for uart).

Notice:
Running environment is bellow.
Bluepill
Stlink(clone) to programming Bluepill.
FT232RL(red) to communicate uart of bluepill.
teraterm
ca65, ld65 are on Searle's zip( run on cmd.exe )
bin2hex is problematic. if you assemble osi_bas.s, you would get .bin, but bin2hex needed.
I got this https://github.com/krupski/bin2hex.git
git clone it, then make and use it.
You should do copy osi_bas.hex to ROM.HEX of pill6502gen2 then make clean and make to run osi_bas.hex. 
  
Sorry, no warranty.  
Enjoy!
