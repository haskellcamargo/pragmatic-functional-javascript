# Introdução

Este livro está separado em 15 capítulos com sub-seções específicas:

1. **Introdução**: Este capítulo lhe dá uma breve introdução sobre o desenvolvimento de software pragmático, abordando a história e razão da programação funcional e como é aplica-la ao desenvolvimento de software moderno.
2. **Origem do mal**: apresenta características de linguagem que são mais prejudiciais do que benéficas e depois se concentra em alternativas para resolver os problemas que elas apresentaram.
3. **Conheça o ESLint**: mostra como encorajar a escrita do código funcional e restringir os recursos prejudiciais da linguagem usando uma ferramenta específica para isso.
4. **Modules**: focuses on how to organize modular code and functions according to their domain and structuring the file system of your program. There is a special focus on modular code, code that is not specific for the program, but that can be easily reused and help you writing less.
4. **Módulos**: focado em como organizar o código modular e as funções de acordo com seu domínio e estruturar a arquitetura de diretórios do seu programa. Existe um foco especial no código modular, código que não é específico para o programa, mas que pode ser facilmente reutilizado e ajudá-lo a escrever menos.
5. **O poder da composição**: aborda o que realmente é a programação funcional e mostra como criar coisas mais complexas, compondo muito simples. É definitivamente como jogar LEGO!
6. **Types**: provides an overview about how a type system behaves and tools for static type checking on JavaScript in order to reduce the number of bugs. It also provides a different overview about static type system, different from what is presented in most courses and tutorials.
6. **Tipos**: fornece uma visão geral sobre como um sistema de tipo se comporta e ferramentas para verificação de tipo estático em JavaScript para reduzir a quantidade de erros. Ele também fornece uma visão geral diferente sobre o sistema de tipo estático, diferente do que é apresentado na maioria dos cursos e tutoriais.
7. **Transforming values**: talks about common data structures transformations and functions that help us modeling transformations and working with immutable data structures. We'll be using a library called Ramda to present it in practice.
7. **Transformando valores**: fala sobre transformações de dados e funções que nos ajudam a modelar transformações e trabalhar com estruturas de dados imutáveis. Estaremos usando uma biblioteca chamada Ramda para apresentá-la na prática.
8. **Monads, monoids e functors**: pode parecer um pouco teórico, mas irá apresentar, juntamente com os conceitos dos termos, o uso prático deles e a importância deles no design de um programa funcional e como eles nos ajudam a lidar com erros e lidar com o perigo que exite mundo a fora.
9. **Programação assíncrona**: é uma visão geral sobre como lidar com ações dependentes do tempo e computações assíncronas. Falaremos sobre promises, futures, generators e a task monad.
10. **Bem-vindo à Terra da Fantasia**: mostra o que é a Terra da Fantasia e como ajuda bibliotecas funcionais diferentes a interagir facilmente e trabalhar em conjunto e mostra algumas bibliotecas que são compatíveis com esta especificação.
11. **Hackeando o compilador**: fornece uma visão geral sobre o Babel e as ferramentas préprocessadoras para JavaScript que nos permitem extender a linguagem para reduzir o tamanho e facilitar o modelamento de nossos problemas. Apresentaremos como escrever plugins no compilador e usar já existentes para escrever um código melhor.
12. **Um pouco de teoria**: é definitivamente a parte mais teórica do livro. Apresentamos as raízes da programação funcional e possivelmente conceitos avançados.
13. **Linguagens Funcionais que visam o JavaScript**: apresenta quatro linguagens que compilam para JavaScript e têm uma boa interoperabilidade com ele, mas com foco no paradigma funcional. Alguns são mais restritivos do que outros, no entanto, com a restrição vem a segurança e a precicabilidade.
14. **Resolvendo problemas do mundo real**: presents common daily problems and functional approaches, step by step, to solve them. It is not only about solving problems, but solving problems in such way that they will generate less problems later.
14. **Resolvendo problemas do mundo real**: apresenta problemas comuns diários e abordagens funcionais, passo a passo,para resolvê-los. Não se trata apenas de resolver problemas, mas resolver problemas de tal forma que eles gerarão menos problemas mais tarde.
15. **Considerações Finais**: é o nosso "adeus". Não é a conclusão, porque as abordagens de desenvolvimento de software estão evoluindo muito rápido, e assumindo que uma maneira específica de fazer o trabalho é o melhor para todos os tempos é definitivamente tolo.

A maioria das partes deste livro são independentes, para que você possa ler capítulos na ordem que você preferir, e a ordem que definimos aqui é apenas uma sugestão (exceto para as considerações finais, é claro).

## O que significa "pragmatismo"?

Pragmatism, noun, a **practical** aproach to problems and affairs. There is no word that can describe this book better. We are going to focus on practical applications of the beautiful and enchanting theory built around functional programming. This book is made for people with basic knowledges on JavaScript programming; you definitely shouldn't have exceptional abilities to understand the things here written: it is made to be practical, simple, concise and after that we except you to be able to write real world applications using the functional paradigm and finally say "I **do** work with functional programming!". This book may be complex for beginners and trivial for advanced programmers. It is designed thinking in the usual programmer that uses JavaScript daily to build any kind of application, but that already **do** have familiarity with JavaScript and is open to the functional mindset. If you are starting to code now, there are better alternatives to this, such as *Structure and Interpretation of Computer Programs* and *How to Design Programs*.

Pragmatismo, substantivo, uma abordagem **prática** para problemas e assuntos. Não há nenhuma palavra que possa descrever este livro melhor. Vamos nos concentrar em aplicações práticas da bela e encantadora teoria construída em torno da programação funcional. Este livro é feito para pessoas com conhecimentos básicos sobre programação de JavaScript; você definitivamente não deveria ter habilidades excepcionais para entender as coisas aqui escritas: é feito para ser prático, simples, conciso e depois disso, exceto você, para poder escrever aplicativos do mundo real usando o paradigma funcional e, finalmente, dizer "Eu **faço** o trabalho com programação funcional! ". Este livro pode ser complexo para iniciantes e triviais para programadores avançados. Ele é projetado pensando no programador usual que usa o JavaScript diariamente para construir qualquer tipo de aplicativo, mas que já **tem** familiaridade com o JavaScript e está aberto à mentalidade funcional. Se você está começando a codificar agora, existem melhores alternativas para isso, como *Structure and Interpretation of Computer Programs* e *How to Design Programs*.

When possible, we'll provide the problem that we are trying to solve with alternative implementations and techniques in other paradigms. Programming is made to solve problems, but sometimes solving a problem may generate several other small problems, and this is where we will touch; this is what we will try to avoid. Before continuing, we need to set some premises:

* **Programming languages are not perfect**: seriously. They are built and designed by humans, and humans are not perfect \(far from that!\). They may contain failures and arbitrarily defined features, however, most times there is a reasonable explanation about the "workaround".

* **Problem solving may generate other problems**: if you are worried only about "getting shit done", this might be a bit controversial for you. When you solve a problem, have in mind that your solution is not free from introducing problems that other people will have to solve later. Being open to criticism is a good thing here; this is how technology evolves.

* **The right tool for the right job**: this is pragmatism. We pick the tool that solves the problem and introduces the lowest number of side-effects. Good programmers analyse trade-offs. There are a lot of programming languages published and dozens of paradigms, and they are not made/discovered only because "somebody likes writing that way" or "somebody wants to have their name in a programming language" \(at least most times\), but because new problems arise. It is sensible, for example, to use Erlang on telephone systems, Agda on mathematical proofs and Go on concurrent systems, but it is definitely insane to use Brainfuck on web development and PHP on compiler development!



### The author

Marcelo Camargo is a cute brazilian programmer and one of the main evangelists of the paradigm in Brazil. He is the designer of the Quack programming language and colaborator or maintainer of dozens of open-source projects, such as the first unnoficial version of Skype for Linux and improvements on the PHP language. He loves type theory, capybaras and has a cute black cat that is almost always with him while writing. You can find him on GitHub under [`/haskellcamargo`](https://github.com/haskellcamargo) or write him a letter on [marcelocamargo@linuxmail.org](marcelocamargo@linuxmail.org).



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





