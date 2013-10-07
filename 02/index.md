5-7 well-organized minutes about why you should do hardware programming in high-level languages.

# Why, Robot?

This week I watched the most amazing video on youtube. Boston Dynamic released some footage of its Wildcat robot running around in circles. Now this thing is the side of a Shetland pony. It runs on a two-stroke engine, like a chainsaw. The video starts with the operators firing up the engine in a cloud of blue smoke then booking on out of there.

Robots are obviously serious business. They obviously require serious programming languages.

This is obviously the belief of a lot of programmers. The Tessell project appeared on a well-known programmers' forum the other day. The Tessell is the moral equivalent of an Arduino-- a tiny ARM board with lots of great access to I/O pins. You can run your javascript on it directly. You write a node program, and the Tessell runs it. Okay, it JITs it to Lua bytecode on the board, but the crazy reality is that you're not running C on this tiny thing.

This might seem to you & me to be awesome, but the hackers on that news site were there to tell us all otherwise. You can't do hardware programming in javascript or lua! You need to do it in a real language, like C! Or ARM assembly! Obviously while walking uphill both ways in the snow barefoot, like a real programmer does.

Yeah, I don't buy that.

I think we need to turn this question around. Why should we do it in C? Because we've historically done it that way! And tradition is good, right? Tradition, tradition!

Why do embedded programmers use C anyway?

- They have real-time performance requirements.
- They're operating in heavily resource-constrained environments, where they're counting bytes to keep their memory use down.
- Until recently, it was *the only feasible approach.* Hardware was tiny and slow, and if it wasn't tiny it was expensive. C is the high-level language that gives you the control you need over memory in those tiny environments. That's what it's good at.

But guess what. Environments aren't tiny any more, in this era of the ARM processor. These things may be physically tiny, but they're not slow. And they're not expensive. Two breakthrough boards are responsible for kicking off this new era, and they're amazingly cheap. 

First came the Arduino. The Arduino is a board about the size of a credit card. It's got a tiny ancient ARM on it, a USB plug, and 32K of flash. It's $30. Conferences give them away in the swag bags.  Kickstarter is littered with Arduino-compatible boards. You can get a Digispark Arduino for $9! It's the size of a nickel.

You write software for the Arduino in a variant of C. You compile, download the bits to flash, reboot, and boom. You can control your Arduino with javascript, though. There's a standard protocol for interacting with microcontrollers from a host computer, called Firmata. Node has a great implementation of Firmata, and a truly great API for interacting with hardware implemented on top of that. That's called Johnny Five, and you will use it to make an LED blink very soon.

That's great, but you're running javascript on your laptop, same as you always were. The Arduino isn't running javascript itself. So the crusty old programmers are still right, right?

This is where our second breakthrough board comes in. It's the Raspberry Pi. This is a credit-card-sized ARM processor board, like the Arduino. Only unlike the Arduino, it's got a modern beefy ARM, 512MB of memory, HDMI out, ethernet in, audio out, USB up the wazoo, a GPU with H264 support in hardware, and an SD card slot. It's got 8 GPIO pins and can do practically anything the Arduino can, at the cost of slightly more power. It runs *Linux*. It can run your hobby web site, your home automation systems, your home AV system, a DVR system so you can watch TV, anything you want.

And guess what language you're using to program it. That's right: ANYTHING YOU WANT. This is beefier than whatever it was you had on your desktop ten years ago. Want to drive your home lights with javascript? You can. Want to get wireless moisture data from sensors in your garden & turn on the sprinklers with Python? You can.

It costs $40.

This is *affordable.* And this means that hardware tinkering has suddenly come within the reach of a lot of people who might never have tried it before. Those people are software developers, not hardware people. And they're solving problems that hardware people have simply lived with for ages, like an aging and terrible toolset. (Want a nice scare this Halloween? Teach yourself some Verilog.)

[more]

So great, you *can* do hardware programming in Javascript. Should you? Maybe you should eat your vegetables and learn C. Kale is good for you, I hear, just like malloc.

- when you're targeting platforms like the Pi or the Beaglebone, there's no constrained client reason to use C. It's an entire Linux platform, with easy access to the hardware and the I/O.
- you already know the language -- your startup time is zero
- you can concentrate on solving the robotics problem, not on using a language you're unfamiliar with

The interesting thing is getting your quadcopter to follow the line on the floor, not in figuring out why you can't link against the version of the computer vision library you want to use.

[more]


## intro
### inciting incident
## development
### pinch
### reversal
### pinch
### climax
## conclusion
### re-statement of points
