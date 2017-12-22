## Null considered harmful

And by `null`, we also mean `undefined`. It is hard to see a programmer we never had any sort of problems with null references, null pointers or anything that can represent that absence of a value. For JavaScript programmers, `undefined is not a function`,   for the C\# young men in suits, `NullReferenceException`, and for unlucky one who use need to use Java, the classic `java.lang.NullPointerException`. Do you think we really need `null` as a special language construct? In this point, there is also a consensus between functional programmers and object-oriented programmers: `null` was a secular mistake.

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

Unless you have a **very** good excuse, don't return `null` when all you need to do is giving a simple boolean answer. First thing: `null` is not `false`, `null` is the absence of value, and in this case we don't have a boolean representation, but a three-state model. Booleans should never be nullable.



