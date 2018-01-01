# Types

JavaScript by default doesn't provide support for static type or even runtime type checking. By having type coercion, all the syntactic valid programs are accepted and type errors will only be caught in runtime. For the sake of sanity, there are good tools we can use to make JavaScript code safer and identify most of the runtime errors of a program before they happen, I mean at compile time, like Flow or even TypeScript, the JavaScript superset.

## Why types matter

Do we really need types? At first, this should be an obligation of the compiler; it should be its responsability to ensure that your program is correct and let you worry only about the logic, but this is not what happens on the most popular programming languages. You might not need static type checking, but, for sure, having it will help you writing programs that are more correct and safer, avoiding a lot of possible errors that would only happen in specific situations when executing your program.

