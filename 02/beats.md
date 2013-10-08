controlling hardware with js? 
oxymoron
surely JS is just for swapping out images on web pages
tessel on hacker news
c or assembly, uphill both ways in the snow barefoot
robots R serious bizness
so suppose they have a point, why *do* we do hardware in C?
tradition! tradition
tiny + slow == you need a language with byte-counting control
hard-real-time problems like bone saws need languages with fine control
BUT
moore's law is a thing
wait, should you? malloc == kale, horrible but good for you
NO
history of programming: dip switches -> assembly -> Fortran -> C -> modern dynamic languages
concentrate on the problem to solve, not the ceremony of a language
we're not writing bone saws.
here are two things pushing it forward
#1 arduino: 8bit cpu, 14 dig 6 analog, 32K flash
$30 two t-shirts, swag bags
gets even better: there are Arduino-compatible boards all over kickstarter
digispark is $9 
You don't program an Arduino with javascript.
C, ide.
can run tethered using firmata, which lets you use JohnnyFive to interact with the hardware
johnnyfive is popular because it has a *great* API, way better than the C one
tethering is cheating
#2 raspberry pi
modern beefy ARM, 512MB mem, HDMI out, ethernet in, audio out, USB ports, GPU with H264 video support in hardware, & an SD card slot
8 GPIO pins
almost as great at making hardware accessible as the Arduino
kicker: it runs Linux
official distro is a variant of Debian, but can run ArchLinux as well
guess what language you program it in? ANTHING YOU WANT
beefier than desktops in 2000
$40
affordability is half the point: designed to get hackable computers into classrooms in the UK
and now you're really doing it in javascript!
internet of things is happening now, in dynamic languages
hardware hacking is accessible now, to YOU
