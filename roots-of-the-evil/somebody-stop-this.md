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

