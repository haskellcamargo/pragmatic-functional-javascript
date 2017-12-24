## Mutability can kill your hamster

One of the pillars of functional programming is immutability, and changing things is a very common thing in imperative and object-oriented programming languages, but how one can model computations and problems without even being allowed to have variables?

Mutability is about showing the computer **how** to solve your problem and not presenting out declaratively **what** is the problem that it should solve.

Before presenting how we can do it, let's first examine why mutability is evil and you should avoid it when possible and sensible if you care about the life and health of your hamster. This is definitely not a rant about mutability in general, but an overview of the problems that are undeniably common in real world projects. There are situations where mutability is necessary, but they are the exception, not the rule.

### Mutable data is inherently complex

And mutability without explicit control is what makes software development difficult. The control flow of your program takes more possible paths and more things to worry about. When maintaining code bases with lots of mutable or global variables and references,  there are not warranties that touching and changing a function will not present side-effects in other part of the program that may be completely unrelated. Functions with only input and output give you warranty that they will not affect other parts of the program and are predictable. Worrying about program safety should be a work of the compiler, not yours. The programmer should worry about problem modeling and the only errors with which they should worry about should be from business logic, but most mainstream languages transfer their work to the depressive programmer.

### Multithreading is hard

If you believe that imperative languagens and things which are closer to Assembly are better for distributed systems, you are wrong, and increasingly wrong. Immutable and predictable code is inherently easier to optimize to run in multiple cores and threads because the compiler knows that it can safely run different parts of the program independently knowning that there is no interdependence among them. A function that has some input and aways the same output and that doesn't touches parts of the program it shouldn't or emit side-effects is always thread-safe and optimizable.

### Loss of reversibility

Reversibility matters a lot. Since 2015, new tools for front-end development have emerged and a large part of them is about state control and reversibility, such as React and Vue. Reversibility is about having the control of your program and being able to replicate the point of a program based purely on it's current state. This also makes debugging and finding errors a lot easier because not reproducing errors can no longer be an excuse. When you have reversibility and state control, complexes things become trivial, such as restoring the program state on restarting it or implementing "undo" and "redo" operations.

### Debugging can be tiresome

And I'm not joking. Debugging becomes still harder when you are dealing with multiple processes and asynchronous programming. Did you ever wonder how in the world that variable suddenly had its value changed? When you combine mutability with nullity, you create a dangerous monster.

