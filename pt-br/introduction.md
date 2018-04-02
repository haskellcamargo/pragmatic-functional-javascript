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

Pragmatismo, substantivo, uma abordagem **prática** para problemas e assuntos. Não há nenhuma palavra que possa descrever este livro melhor. Vamos nos concentrar em aplicações práticas da bela e encantadora teoria construída em torno da programação funcional. Este livro é feito para pessoas com conhecimentos básicos sobre programação de JavaScript; você definitivamente não deveria ter habilidades excepcionais para entender as coisas aqui escritas: é feito para ser prático, simples, conciso e depois disso, exceto você, para poder escrever aplicativos do mundo real usando o paradigma funcional e, finalmente, dizer "Eu **faço** o trabalho com programação funcional! ". Este livro pode ser complexo para iniciantes e triviais para programadores avançados. Ele é projetado pensando no programador usual que usa o JavaScript diariamente para construir qualquer tipo de aplicativo, mas que já **tem** familiaridade com o JavaScript e está aberto à mentalidade funcional. Se você está começando a codificar agora, existem melhores alternativas para isso, como *Structure and Interpretation of Computer Programs* e *How to Design Programs*.

Quando possível, forneceremos o problema que estamos tentando resolver com implementações e técnicas alternativas em outros paradigmas. A programação é feita para resolver problemas, mas às vezes resolver um problema pode gerar vários outros pequenos problemas, e é aqui que tocaremos; É isso que tentaremos evitar. Antes de continuar, precisamos estabelecer algumas premissas:

* **As linguagens de programação não são perfeitas**: sério. Elas são construídas e projetadas por humanos, e os humanos não são perfeitos \(longe disso!\). Eles podem conter falhas e recursos arbitrariamente definidos, no entanto, na maioria das vezes, há uma explicação razoável sobre a "gambiarra".

* **A resolução de problemas pode gerar outros problemas**: Se você está preocupado apenas com "fazer as coisas", isso pode ser um pouco controverso para você. Quando você resolve um problema, tenha em mente que sua solução não é livre de apresentar problemas que outras pessoas terão que resolver mais tarde. Estar aberto a críticas é bom aqui; É assim que a tecnologia evolui.

* **A ferramenta certa para o trabalho certo**: isso é pragmatismo. Escolhemos a ferramenta que resolve o problema e introduz o menor número de efeitos colaterais. Os bons programadores analisam os trade-offs. Há muitas linguagens de programação publicadas e dezenas de paradigmas, e eles não são criados/descobertos apenas porque "alguém gosta de escrever dessa maneira" ou "alguém quer ter seu nome em uma linguagem de programação" \(pelo menos na maioria das vezes\) , mas porque surgem novos problemas. É sensível, por exemplo, usar Erlang em sistemas telefônicos, Agda em provas matemáticas e Go em sistemas concorrentes, mas é definitivamente insano usar Brainfuck no desenvolvimento web e PHP no desenvolvimento de compiladores!


### O autor

Marcelo Camargo é um simpático programador brasileiro e um dos principais evangelistas do paradigma no Brasil. Ele é o designer da linguagem de programação Quack e colaborador ou mantenedor de dezenas de projetos open-source, como a primeira versão não oficial do Skype para Linux e melhorias na linguagem PHP. Ele ama a teoria do tipo, as capivaras e tem um gatinho preto fofo que quase sempre está com ele enquanto escreve. Você pode encontrá-lo no GitHub como [`/haskellcamargo`](https://github.com/haskellcamargo) ou escreva-lhe uma carta em [marcelocamargo@linuxmail.org] (marcelocamargo@linuxmail.org).


## The second chance

## A segunda chance

> E Deus disse: "que haja funções", e havia funções.
> And God said, "let there be functions", and there were functions.

No começo, os computadores eram muito lentos, muito mais lentos do que o Android Studio em sua máquina com 2GB de RAM! Quando os primeiros computadores físicos apareceram e as linguagens de programação começaram a ser projetadas e implementadas, havia principalmente 2 mentalidades:

1. Comece pela arquitetura de Von Neumann e **adicione a abstração**;
2. Comece a partir da matemática e **remova a abstração**.

Quando tudo começou, lidar com altos níveis de abstração era muito difícil e dispendioso, a memória e o armazenamento eram muito pequenos, então as linguagens de programação imperativas obtiveram muito mais visibilidade do que as funcionais, pois as linguagens imperativas tinham um nível de abstração inferior que era uma maneira mais fácil de implementar e mapear diretamente para o hardware. Poderia não ser a melhor maneira de projetar programas e expressar idéias, mas pelo menos era mais rápido para executar.

Mas os computadores melhoraram muito, e a programação funcional finalmente conseguiu sua merecida chance! A programação funcional não é um conceito novo. Estou falando sério, é muito velho e veio diretamente da matemática! Os conceitos fundamentais e o modelo computacional funcional vieram mesmo antes que os computadores físicos existissem. Tinha suas origens no cálculo lambda, e era, inicialmente, apenas um sistema formal desenvolvido na década de 1930 para investigar computabilidade.

Muitas linguagens de programação modernas suportam programação funcional bem. Até Mesmo Java se rendeu a isso e implementou expressões lambda e streams. A maioria de vocês programa em linguagens que foram criadas; Quero mostrar-lhe o que foi descoberto.


### Por que a programação funcional?

Se a programação imperativa e outros paradigmas, como a orientação do objeto, eram bons o suficiente, por que precisamos aprender uma nova maneira de codificar? A resposta é: sobrevivência. A orientação a objeto não pode mais nos salvar do monstro da nuvem. Problemas mais complexos surgiram e a programação funcional se encaixa muito bem. A programação funcional não é "outra sintaxe", como algumas pessoas pensam; É uma outra mentalidade e uma maneira declarativa de resolver problemas. Embora na programação imperativa você especifique etapas e como as coisas acontecem, na programação declarativa \(funcional e lógica\) você especifica o que tem que ser feito e o computador deve decidir a melhor maneira de fazer isso. Nós evoluímos muito para fazer o trabalho que um computador pode fazer centenas de vezes melhor que nós.

#### Testabilidade e manutenção

As bases de código modulares e funcionais são muito mais fáceis de testar e obter uma cobertura elevada nos testes de unidades. As coisas são muito bem isoladas e independentes e, seguindo todos os princípios principais, você obtém programas compostos que funcionam bem juntos e têm menos erros.

#### Paralelismo

Isso é realmente variável com a implementação, mas em linguagens que podem acompanhar todos os tipos de efeitos, você obtém paralelismo e a possibilidade de agrupar seu programa sem nenhum custo.

#### Otimização

As linguagens funcionais tendem a ser muito mais fáceis de otimizar e são mais previsíveis para os compiladores. Conhecer todo o tipo de coisas que podem ser vistas em um programa dá a possibilidade ao compilador de conhecer a semântica do seu código antes mesmo de executá-lo. Haskell pode ser ainda mais rápido que C se você escrever código idiomático! O principal mecanismo de JavaScript, V8, investiu amplamente em otimizações para o paradigma funcional.

## Menos é mais

Ter muitas maneiras de fazer um trabalho e resolver um problema no mesmo contexto é sempre bom, certo? Bem, nem sempre. Se você pegar a maioria das linguagens de programação que são amplamente utilizadas pelo mercado, então você tem uma linguagem funcional - e isso é válido também para o JavaScript. O JavaScript tem fortes laços com o Esquema e tem o potencial perfeito para ser uma excelente linguagem funcional. Remova laços, mutabilidade, referências, declarações condicionais, exceções, etiquetas, blocos e você praticamente possui um dialeto OCaml digitado dinamicamente. Estou falando sério, você pode até definir funções em JavaScript sem dar importância à ordem em que ocorrem, assim como OCaml em Haskell faz - isso é o que podemos chamar de hoisting e nós veremos como aproveitar isso nos próximos capítulos.

Não seja avaro. Você realmente precisa de todas as diferentes construções de linguagem não endereçadas? Nos capítulos deste livro, descartaremos uma grande parte do JavaScript e nos concentraremos apenas em um subconjunto expressivo: funções e ligações, é tudo o que precisamos por enquanto! Antes de aprender a programação funcional com JavaScript, primeiro você terá que pensar em desaprender algumas coisas. Isso é necessário para evitar vícios de linguagem e estimular seu cérebro para resolver problemas de maneira declarativa. Por enquanto, você terá que confiar, mas no decorrer deste livro, você verá como tudo faz sentido e se encaixa no propósito.

## Ferramentas

Nós nos concentraremos mais na semântica do programa e na correção do que na execução, mas se você realmente quiser aprender, apenas a leitura deste livro não será suficiente.





