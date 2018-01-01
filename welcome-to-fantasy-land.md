# Welcome to Fantasy Land

## Unicorns and rainbows

Isn't that cute and wonderful? Fantasy Land is a specification for algebraic JavaScript, that is, the specification of how algebraic structures should be interoperable in the JavaScript environment. This means most part of JavaScript libraries and tools with focus in functional programming will follow these laws and specification, making them easily interoperable. This is the theory that will lead to a pragmatic and standardized practic.

But first, how can we define an algebra?

* **A set of values**: like primitive numbers, strings or even other data structures.
* **A set of operators**: that can be applied to values.
* **A set of laws**: the operations applied to these values must obey.

Each Fantasy Land algebra is a separate specification. Some algebras may depend on other algebras. The JavaScript primitives also have equivalents to some of these algebras, as we will see in some occasions. The specification warrants that values that satisfy to specific algebras can be safely replaced by other values that also respect them. For example, we can have:



