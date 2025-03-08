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

5. notices
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
**IMPORTANT**
My Bluepill's cpu is **NOT** STM32, but GD32(RISC-V: cpuid is 410).
Page alignment is critical for Risc-V(GD32) and 6502 either.
If we wrote to flash(emulated EEPROM), then if not changed behavior or memory image, you should erase flash several times.
No need for care of flash image size, but if wrote code is not reveal run, that is perhaps erase needed.
And if you anoyed with page align, you could start with Searle's ZIP again. That works!!!
I could not get properly explain Page alignment would affect on 6502 on bluepill yet.
Only I found today that Zephyr project made some warning on page alignment of GD32.
https://docs.zephyrproject.org/latest/build/dts/api/bindings/mtd/gd%2Cgd32-nv-flash-v2.html
>erase-block-size
>int
>address alignment required by flash erase operations write-block-size
>int
>address alignment required by flash write operations

6. still has several problems
6.1 zeropage
ewoz's variables are still in problem, in ewoz you could test write ex: D8: FF or A8:FF.
if wrote FF, it is normal, if not wrote FF, that is problem.
6.2 basic sudden hangs
i do not know how to mitigate this.
garbage collection, or some kind of bug bites.

But this works:-)</PRE>
<img src="https://github.com/cobwebkanamachi/ewozmon4pill6502gen2/blob/main/works.png">
<PRE>Sorry, no warranty.  
Enjoy!</PRE>
