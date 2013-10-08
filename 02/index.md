5-7 well-organized minutes about why you should do hardware programming in high-level languages.

# Why, Robot?

Hello, CascadiaJS friends. It's a pleasure to be here talking to you all about javascript hardware hacking. 

Some people think it's an oxymoron. You can't program robots with javascript!

The Tessel project appeared on Hacker News the other day. The Tessel is the moral equivalent of an Arduino-- a tiny microcontroller board with lots of great access to I/O pins. You write node-style javascript, and the Tessel runs it. Okay, it JITs it to Lua bytecode on the board, but the crazy reality is that you're not running C on this tiny thing. You're programming it Javascript.

This might seem to you & me to be awesome, but the Hacker News people were there to tell us all otherwise. The Tessel is an abomination. You can't do hardware programming in javascript or lua! It's not reliable! It's slow! It'll garbage-collect on you! You need to do embedded hardware programming in a real language, like C! Or ARM assembly! While walking uphill both ways in the snow barefoot, like a real programmer.

The other day I watched the most amazing video on youtube. Boston Dynamics released some footage of its Wildcat robot. Now this thing is the size of a Shetland pony. It runs on a two-stroke engine, like a chainsaw. The video starts with the operators firing up the engine in a cloud of blue smoke then booking on out of there. And then the Wildcat walks, bounds, and then gallops in circles around a parking lot. State of the art in robotics! All this is funded by DARPA. Probably they're going to strap rockets to it next.

Robots are obviously serious business. They obviously require serious programming languages. 

Yeah, I don't buy that.

Let's turn this question around. Why do we do it in C? Because we've historically done it that way! And tradition is good, right? Tradition, tradition!

Why do embedded programmers use C anyway?

Until recently, it was *the only feasible approach.* Hardware was tiny and slow, and if it wasn't tiny it was expensive. C is the high-level language that gives you the control you need over memory in those tiny environments. It's unparalleled at this. If you've got real-time performance requirements-- say you're running a bone saw doing hip surgery-- C is what you'll choose. And if you're operating in heavily resource-constrained environments, where you're counting bytes to keep memory use down, C is what you'll choose.

But guess what. Moore's Law is a thing. Environments aren't tiny any more, in this era of the ARM processor. These things may be physically tiny, but they're not slow. And they're not expensive. Not any more. Two breakthrough boards are responsible for kicking off this new era, and they're amazingly cheap. 

First came the Arduino. The Arduino Uno is a board about the size of a credit card. It's got a tiny ancient 8-bit microcontroller on it, a USB plug, 14 digital pins, 6 analog pins, and 32K of flash. It's $30.Conferences give them away in the swag bags. That's two t-shirts! Kickstarter is littered with Arduino-compatible boards. Here's a good one-- it's the Digispark Arduino. It costs $9! It's the size of a nickel.

You don't program an Arduino with javascript.

You write software for the Arduino in a variant of C. You compile, download the bits to flash, reboot, and boom. You can control your Arduino with javascript, though. There's a standard protocol for interacting with microcontrollers from a host computer, called Firmata. Node has a great implementation of Firmata, and a truly great API for interacting with hardware implemented on top of that. That's called Johnny Five, and you will use it to make an LED blink very soon.

That's great, but you're running javascript on your laptop, not on the Arduino. The Arduino isn't running javascript itself. It's running compiled C, same as it ever was.  We're cheating. So the crusty old programmers are still right.

This is where our second breakthrough board comes in. It's the Raspberry Pi. This is a credit-card-sized board, like the Arduino. Only unlike the Arduino, it's got a modern beefy ARM, 512MB of memory, HDMI out, ethernet in, audio out, USB up the wazoo, a GPU with H264 support in hardware, and an SD card slot. It's got 8 GPIO pins and can do practically anything the Arduino can, at the cost of slightly more power. It runs *Linux*. It can run your hobby web site, your home automation systems, your home AV system, a DVR system so you can watch TV, anything you want.

And guess what language you're using to program it. That's right: ANYTHING YOU WANT. This is beefier than whatever it was you had on your desktop in the year 2000. Want to write javascript to turn on your lights when you walk in the room? You can. Want to write Python to get moisture data from wireless sensors in your garden & turn on the sprinklers ? You can.

The Raspberry Pi costs $40.

This is *affordable.* And this means that hardware tinkering has suddenly come within the reach of a lot of people who might never have tried it before. The Raspberry Pi was developed to get a hackable computer back into schoolrooms in the UK, so today's kids could have programming experiences more like the ones my generation had, with computers like the Apple II and the BBC Acorn. Guess what! It's working. Hardware hacking is accessible to kids again.

So great, you *can* do hardware programming in Javascript. Should you? Maybe you should eat your vegetables and learn C. Kale is good for you, I hear, just like malloc.

Yeah, I don't buy that.

The history of programming languages says not to buy it. We invented assembler because we were sick of programming using DIP switches. We invented FORTRAN because we were sick of assembler. And we invented modern dynamic languages for the same reason. Because the increasing levels of abstraction let us do ever-more complicated things with these ever-more-powerful machines.

The Raspberry Pi is a modern computer. It's got CPU cycles coming out its ears. Run your favorite language on it. You already know the language; your startup time is zero. You can concentrate on solving the robotics problem, not on struggling with your tools. And if you're just learning to program in the first place, you get to have all the fun of blinking an LED or moving a robot arm with a programming language that doesn't slice your fingers off.

The Internet of Things? It's happening right now, as people connect all kinds of tiny devices together using Javascript, or Python, or Ruby, or whatever language they like best.

Hardware hacking is accessible now. It's accessible to everybody. To kids in classrooms with Raspberry Pis, to me, and to you, too.

And next I'm going to show you how.

Thank you.
