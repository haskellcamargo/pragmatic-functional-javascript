# Roots of the evil

## Null considered harmful

And by `null`, we also mean `undefined`. It is hard to see a programmer who never had any sort of problems with null references, null pointers or anything that can represent the absence of a value. For JavaScript programmers, `undefined is not a function`,   for the C\# young men in suits, `NullReferenceException`, and for unlucky one who use need to use Java, the classic `java.lang.NullPointerException`. Do you think we really need `null` as a special language construct? In this point, there is also a consensus between functional programmers and object-oriented programmers: `null` was a secular mistake.

### A brief history

Null references were introduced in ALGOL-W programming language decades ago; 1964 to be specific. They hadn't any special purpose except they were considered "easy to implement" by the language designers, and a lot of modern languages implemented it for the same reason ─ and it gone viral. At that time, most of the softwares, including the compiler, were written in machine code with little or no abstraction. But what is wrong with `null`?

### It increases complexity

When you have to compare for null to avoid runtime errors, your code logic forks and creates a new path of possibilities. If you use lots of `null` values, the chance of having spaghetti code that becomes hard to maintain is really big. Object-oriented languages recommend the _null object pattern_, while functional languages use monads for that. Luckily, there are lots of libraries and monadic implementations for JavaScript to abstract and avoid this problem. We'll see monads in details and how to properly handle `null` later ─ for now we'll be presenting the problems and seeking the solution will be a task for the next chapters.

### Unpredictable types

Why would you return `null` in a function that retrieves the list of users of the database when I can just return the **empty representation** of the expected type? ─ an empty array in this situation. The fact is that `null` can inhabit **any** type, and this makes the task of debugging a lot harder. Which one is more pragmatic?

```js
const showUsers = () => {
    const users = getUsers()
    if (users !== null) {
        users.forEach(console.log)
    }
}
```

```js
const showUsers = () => getUsers().forEach(console.log)
```

Don't make it complex when you can make it simple.

### True, false ...and null!?

Unless you have a **very** good excuse, don't return `null` when all you need to do is giving a simple boolean answer. First thing: `null` is not `false`, `null` is the absence of value, and in this case we don't have a boolean representation, but a three-state model. Booleans should never be nullable \(or they aren't booleans at all\) ─ and `null` is not the same as `false` and not even supposed to be.

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

## Type coercion is a bad boy

While static typing helps avoiding mistakes and unexpected behaviors, type coercion helps losing the control about your data values and types. Type coercion means that when the operands of an operator have different types, then they are converted to an equivalent and acceptable value by that operator. For instance, when you do:

```js
1 == true
```

This is `true` only because, as longer as there is no comparison for different types, `true` on the right side is converted to a number \(based on `1` in the left side\), in this case, `true` becomes `1`. The operator `===` prevents this conversion from happening, and it is what we will be using from this point.

The type system of a programming language defines what types of data can exist in the language and how operations can be applied to them, and this sort of thing exist to prevent the programmer from shooting theirself on the foot. Type coercion is about  **implicitly** converting incompatible values when there is no valid operation for that type of value.

In languages like Python, even with dynamic typing, operations like `"foo" + 1` will emit a runtime error:

```python
>>> "foo" + 1
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: cannot concatenate 'str' and 'int' objects
```

And this helps preventing a lot of bugs that would be caught only in distant point of the program. Type coercion is a misnomer, as long as values have no types in the sense of static typed languages, but it is a definition of how different values interact. The ECMAScript specification about type coercion is really big; there are lots of rules and exceptions and trusting on these conversions is a fatal error.

## Somebody stop this!

There are a lot of articles about the `this` keyword in JavaScript, and **this** was one of the worst design issues of the language. Some people argue that there would be names that express better the concept of `this`, like `potatoes`. Even JavaScript programmers with years of experience get confused about it and it is a common source of mistakes among them. There are several different ways to set the value of `this` inside a function, such as calling a method from an object, calling a function alone, using `call`, `apply` or even using `new` to create an instance. It's really a handyman keyword. Telling the behavior of a program piece only looking at it when it has `this` is not as easy as it is with pure functions because you need to worry and care about the **context** of call of that function. It also has different behaviors when using `function` keyword and `() =>`, the fat-arrow, which captures the top context instead of creating another, making the use of the two forms of declarations of anonymous functions not interchangeable.

### Behaviors of this

#### Method call

```js
const person = {
    fullName: 'Mr. Pickles',
    sayName: function () {
        console.log(`Hello, my name is ${this.fullName}!`)
    }
}

person.sayName() // Hello, my name is Mr. Pickles!
```

Note that using `() =>` instead of `function` would capture the top `this`, making `this.fullName` be `undefined` in this situation.

