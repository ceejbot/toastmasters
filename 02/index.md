5-7 well-organized minutes about why you should do hardware programming in high-level languages.

# Why, Robot?

The Tessell project appeared on a well-known programmers' forum the other day.



I want to turn that question around. Why should we do it in C? Because we've historically done it that way! And tradition is good, right? Tradition, tradition!

Why do embedded programmers use C anyway?

- They have real-time performance requirements.
- They're operating in heavily resource-constrained environments, where they're counting bytes to keep their memory use down.
- Until recently, it was *the only feasible approach.* Hardware was tiny and slow, and if it wasn't tiny it was expensive.

Suddenly today, in the era of the ARM processor, this isn't true any more. These things may be physically tiny, but they're not slow. And they're not expensive. Two breakthrough boards are responsible for kicking off this new era, and they're amazingly cheap. 

First came the Arduino. The Arduino Uno is $30, which is pretty cheap. Then you realize that you can get a Digispark Arduino for $9! A Raspberry Pi-- an entire Linux machine, capable of serving your hobby web page-- is $40. This is *affordable.* And this means that hardware tinkering has suddenly come within the reach of a lot of people who might never have tried it before. Those people are software developers, not hardware people. And they're solving problems that hardware people have simply lived with for ages, like an aging and terrible toolset. (Want a nice scare this Halloween? Teach yourself some Verilog.)

Want to hear something crazy? The Tessell is the moral equivalent of an Arduino-- a tiny ARM board with lots of great access to I/O pins. You can run your javascript on it directly. You write a node program, and the Tessell runs it. Okay, it JITs it to Lua bytecode on the board, but the crazy reality is that you're not running C on this tiny thing.

So great, you *can* do hardware programming in Javascript. Should you? Maybe you should eat your vegetables and learn C. Kale is good for you, I hear, just like malloc.

- when you're targeting platforms like the Pi or the Beaglebone, there's no constrained client reason to use C. It's an entire Linux platform, with easy access to the hardware and the I/O.
- you already know the language -- your startup time is zero
- you can concentrate on solving the robotics problem, not on using a language you're unfamiliar with

The interesting thing is getting your quadcopter to follow the line on the floor, not in figuring out why you can't link against the version of the computer vision library you want to use.



## intro
### inciting incident
## development
### pinch
### reversal
### pinch
### climax
## conclusion
### re-statement of points
