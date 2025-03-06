# ewozmon4pill6502gen2
<PRE>
This repo is clone of https://gist.github.com/b529a24f39bcbd53f1e21775e24d0b9e.git.
And also an implement for pill6502gen2 branch bellow.
https://github.com/cobwebkanamachi/pill_6502/tree/pio-and-uartbased-mod/new-src

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
  
Enjoy!
