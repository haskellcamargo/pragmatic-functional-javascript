# Welcome to Fantasy Land

## Unicorns and rainbows

Isn't that cute and wonderful? Fantasy Land is a specification for algebraic JavaScript, that is, the specification of how algebraic structures should be interoperable in the JavaScript environment. This means most part of JavaScript libraries and tools with focus in functional programming will follow these laws and specification, making them easily interoperable. This is the theory that will lead to a pragmatic and standardized practic.

But first, how can we define an algebra?

* **A set of values**: like primitive numbers, strings or even other data structures.
* **A set of operators**: that can be applied to values.
* **A set of laws**: the operations applied to these values must obey.

Each Fantasy Land algebra is a separate specification. Some algebras may depend on other algebras. The JavaScript primitives also have equivalents to some of these algebras, as we will see in some occasions. The specification warrants that values that satisfy to specific algebras can be safely replaced by other values that also respect them. For example, we can have:

* One list can be replaced by another if they have the same length.
* Two objects have the same keys and their values have the same or compatible types.
* Two functions have equivalent output types for equivalent input types.

### Understanding type signatures

We'll be using a notation similar to Haskell type signatures to express the types that the algebras must satisfy, where:

* `::` means "is a member of".
  * `e :: t` is the same as "the expression `e` is member of type `t`".
  * `true :: Boolean` means that "`true` is a member of type `Boolean`".
  * `42 :: Integer, Number` means that "`42` is a member of type `Integer` and type `Number`".
* New types can be created via type constructors.
  * Where type constructors can take zero or more parameters.
  * In Haskell, `True` is a type constructor that yields a `Bool` and takes no parameters.
  * `Array` is a type constructor that takes one parameter.
  * `Array Number` is the type of any array that holds only numbers, like `[1, 2]`.
  * Types can be nested. `Array (Array Boolean))` is the type of all arrays that have arrays of booleans, like `[[true], [false, true], []]`, where `[]` can be seen as an array compatible to any type parameter.



