# Introduction

This book is separated in 15 chapters with specific subsections:

1. **Introduction**: gives you a brief introduction about pragmatic software development, functional programming history and reason and how it is applicable to modern software development.
2. **Roots of the evil**: presents language features that are more harmful than beneficial and later focuses on alternatives to solve the problems introduced by them.
3. **Meet ESLint**: shows how to encourage writing functional code and restricting harmful language features by using a specific tool for that job.
4. **Modules**: focuses on how to organize modular code and functions according to their domain and structuring the file system of your program. There is a special focus on modular code, code that is not specific for the program, but that can be easily reused and help you writing less.
5. **The power of composition**: touches on what really functional programming is about and shows you how to create more complexes things by composing very simple ones. It is definitely like playing LEGO!
6. **Types**: provides an overview about how a type system behaves and tools for static type checking on JavaScript in order to reduce the number of bugs. It also provides a different overview about static type system, different from what is presented in most courses and tutorials.
7. **Transforming values**: talks about common data structures transformations and functions that help us modeling transformations and working with immutable data structures. We'll be using a library called Ramda to present it in practice.
8. **Monads, monoids and functors**: may look a bit theoretical, but will present, together with the concepts of the terms, the practical usage of them and how important they are on the design of a functional program and how they help us to handle errors and deal with the dangerous world that exist outside.
9. **Async programming**: is an overview about how to deal with time-dependent actions and asynchronous computations. We'll talk about promises, futures, generators and the task monad.
10. **Welcome to Fantasy Land**: shows what is Fantasy Land and how it helps different functional libraries to easily interact and work together and shows some libraries that are compliant to this specification.
11. **Hacking the compiler**: gives an overview about Babel and preprocessor tools for JavaScript that allow us to extend the language to reduce boilerplate and make it easier to model our problems. We'll present how to write plugins to the compiler and use already existing to write better code.
12. **A bit of theory**: is definitely the most theoretical part of the book. We present the roots of functional programming and possibly advanced concepts.
13. **Functional languages targeting JavaScript**: introduces four languages that compile to JavaScript and have a good interoperability with it, but with focus on the functional paradigm. Some are more restrictive than others, however, with restriction comes security and precictability.
14. **Solving real world problems**: presents common daily problems and functional approaches, step by step, to solve them. It is not only about solving problems, but solving problems in such way that they will generate less problems later.
15. **Final considerations**: is our "goodbye". It is not the conclusion, because software development approaches are evolving really fast, and assuming that a specific way to get the job done is the best for all the times is definitely foolish.


## What does "pragmatism" mean?

Pragmatism, noun, a **practical **aproach to problems and affairs. There is no word that can describe this book better. We are going to focus on practical applications of the beautiful and enchanting theory built around functional programming. This book is made for people with basic knowledges on JavaScript programming; you definitely shouldn't have exceptional abilities to understand the things here written: it is made to be practical, simple, concise and after that we except you to be able to write real world applications using the functional paradigm and finally say "I **do **work with functional programming!".

When possible, we'll provide the problem that we are trying to solve with alternative implementations and techniques in other paradigms. Programming is made to solve problems, but sometimes solving a problem may generate several other small problems. Before continuing, we need to set some premises:

* **Programming languages are not perfect**: seriously. They are built and designed by humans, and humans are not perfect \(far from that!\). They may contain failures and arbitrarily defined features, however, most times there is a reasonable explanation about the "workaround".

* **Problem solving may generate other problems**: if you are worried only about "getting shit done", this might be a bit controversial for you. When you solve a problem, have in mind that your solution is not free from introducing problems that other people will have to solve later. Being open to criticism is a good thing here; this is how technology evolves.

* **The right tool for the right job**: this is pragmatism. We pick the tool that solves the problem and introduces the lowest number of side-effects. Good programmers analyse trade-offs. There are a lot of programming languages published and dozens of paradigms, and they are not made/discovered only because "somebody likes writing that way" or "somebody wants to have their name in a programming language" \(at least most times\), but because new problems arise. It is sensible, for example, to use Erlang on telephone systems, Agda on mathematical proofs and Go on concurrent systems, but it is definitely insane to use Brainfuck on web development and PHP on compiler development!



### The author

Marcelo Camargo is a developer and translator known in Brazil for advocating in favor of functional programming. He is the creator of the Quack programming language, Skype unofficial version for Linux and contributor on dozens of open-source projects. If you want to talk about compilers and type theory, you can easily find him on GitHub under [/haskellcamargo](https://github.com/haskellcamargo).



## The second chance

> And God said, "let there be functions", and there were functions.

In the beginning, computers were very slow, way slower than running Android Studio on your 2GB RAM machine! When the first physical computers appeared and programming languages started to be designed and implemented, there were mainly 2 mindsets:

1. Start from the Von Neumann architecture and **add abstraction**;
2. Start from mathematics and **remove abstraction**.

When it all started, dealing with high levels of abstraction was very hard and costly, memory and storage were really small in power, so imperative programming languages got a lot more visibility than functional ones because imperative languages had a lower level of abstraction that was way easier to implement and map directly to the hardware. It could not be the best way to design programs and express ideas, but at least it was the faster one to run.

But computers improved a lot, and functional programming finally got its deserved chance! Functional programming is not a new concept. I'm serious, it is really old and came directly from mathematics! The core concepts and the functional computational model came even before physical computers existed. It had its origins on lambda calculus, and it was initally only a formal system developed in the 1930s to investigate computability.

A lot of modern programming languages support well functional programming. Even Java surrended to this and implemented lambda expressions and streams. Most of you program in languages that were created; I want to show you the one which was discovered.

### Why functional programming?

If imperative programming and other paradigms, like object orientation, were good enough, why do we need to learn a new way to code? The answer is: survival. Object orientation cannot save us from the cloud monster anymore. More complex problems have arisen and functional programming fits them very well. Functional programming is not "another syntax", as some people think; it is another mindset and a declarative way to solve problems. While in imperative programming you specify steps and how things happen, in declarative \(functional and logic\) programming you specify what has to be done, and the computer should decide the best way to do that. We've evolved a lot to do the job that a computer can do hundreds of times better than us.

#### Testability and maintainability

Modular and functional code bases are way easier to test and get a high coverage on unit tests. Things are very well isolated and independent, and by following all the main principles you get composable programs that work well together and have less bugs.

#### Parallelism

This is really variant with the implementation, but in languages that can track all sort of effects, you get parallelism and the possibility of clustering your program for free.

#### Optimization

Functional languages tend to be a lot easier to optimize and are more predictable for compilers. Knowing all sort of things that can haven in a program gives the possibility to the compiler to know the semantics of your code before even running it. Haskell can be even faster than C if you write idiomatic code! The main JavaScript engine, V8, has invested extensivily in otimizations for the functional paradigm.

## Less is more

Having a lot of ways to do a job and to solve a problem in the same context is always good, right? Well, not always. If you pluck most programming languages that are largely used by the market, then you have a functional language ─ and this is valid also to JavaScript. JavaScript has strong ties with Scheme and has the perfect potential to be a very good functional language. Remove loops, mutability, references, conditional statements, exceptions, labels, blocks and you virtually have a dynamically typed OCaml dialect. I'm serious, you can even define functions in JavaScript without giving importance to the order they occur, just like OCaml em Haskell do ─ this is what we can call hoisting and we'll be seing how to take advantage of this in the next chapters.

Don't be miser. Do you really need all that different unaddressed language constructs? In the chapters of this book we'll discard a large part of JavaScript and we'll focus only in an expressive subset: functions and bindings, it is everything we'll need for now! Before learning functional programming with JavaScript, you first will have to think about unlearning some things. This is necessary to avoid language vices and to estimulate your brain to solve problems in a declarative way. For now, you'll have to trust, but in the course of this book you'll see how everything makes sense and fits into the purpose.

## Tooling

We'll focus more on program semantics and correctness than execution, but if you really want to learn, only reading this book will not be enough.





