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

