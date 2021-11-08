# Por que Julia? {#sec:why_julia}

O mundo da ciência de dados é repleto de diferentes linguagens open source.

A Indústria tem, em grande parte, adotado as linguagens Python e R.
**Por que aprender uma outra linguagem?**
Para responder a essa questão, abordaremos duas situações bastante comuns:

1. **Nunca programou antes** -- see @sec:non-programmers.

2. **Já programou** -- see @sec:programmers.

## Para os que nunca programaram {#sec:non-programmers}

Para a primeira situação, acreditamos que o ponto em comum seja:

A ciência de dados te atrai, você tem vontade de aprender sobre e entender como ela pode ajudar sua carreira seja na academia, seja no mercado.
Então, você tenta encontrar formas de aprender essa nova habilidade e cai em um mundo acrônimos complexos:
`pandas`, `dplyr`, `data.table`, `numpy`, `matplotlib`, `ggplot2`, `bokeh`, e a lista continua.

E, do nada, você ouve: "Julia".
O que é isso?
Como seria diferente de qualquer outra ferramenta usada para ciência de dados?

Por que você deveria usar seu tempo para aprender uma linguagem que programação que quase nunca é mencionada em processos seletivos, posições em laboratórios, pós-doutorados ou qualquer outro trabalho acadêmico?
A respota para a questão é que **Julia é uma nova abordagem** tanto para programação, quanto para ciência de dados.
Tudo que você faz em Python ou R, você pode fazer em Julia com a vantagem de poder escrever um código legível [^readable], rápido e poderoso.
Assim, Julia tem ganhado força e por uma série de motivos.

Então, **se você não tem nenhum conhecimento prévio de programação, recomendamos que aprenda Julia** como uma primeira linguagem de programação e ferramenta para ciência de dados.

## Para programadores {#sec:programmers}

Na segunda situação, a história por trás muda um pouco.
Você é uma pessoa que não só sabe programar, como também, provavelmente, vive disso.
Você tem familiaridade com uma ou mais linguagens de programação e deve transitar bem entre elas.
Você ouviu falar sobre "ciência de dados" e quer surfar essa onda.
Você começou a aprender a fazer coisas em `numpy`, a manipular `DataFrames` em `pandas` e como plotar em `matplotlib`.
Ou talvez você tenha aprendido tudo isso em R usando tidyverse e `tibbles`, `data.frames`, `%>%` (pipes) e `geom_*`...

Então, por alguém ou por algum lugar, você ouviu falar dessa nova linguagem chamada "Julia".
Por que se importar?
Você já domina Python ou R e consegue fazer tudo que precisa.
Bom, vamos analisar alguns possíveis cenários.

**Alguma vez você já fez em Python ou R:**

1. Algo que não tenha conseguido alcançar a performance necessária?
Então, **em Julia, minutos no Python ou R se transformam em segundos**^[e até em milésimos de segundo.].
Nós separamos o @sec:julia_wild para exemplificar casos de sucesso em Julia tanto na academia quanto no mercado.

2. Tentou algo diferente das convenções `numpy`/`dplyr` e descobriu que o código estava lento e provavelmente precisaria de magia ^[`numba`, or even `Rcpp` or `cython`?] para torná-lo mais rápido?
**Em Julia, você pode persinalizar uma série de coisas sem perder desempenho**.

3. Precisou executar um debug em um código e caiu num código Fortran ou C/C++, sem ter ideia alguma do que fazer?
**Em Julia, você lê apenas códigos de Julia, não é preciso programar em outra linguagem para tornar a original mais rápida**.
Isso é chamado o "problema das duas linguagens" (see @sec:two_language).
É também o caso quando "você tem uma ideia interessante e tenta contribuir com um pacote open source, mas desiste porque quase tudo não está nem em Python, nem em R, mas em C/C++ ou Fortran"^[dê uma olhada em algumas bibliotecas de aprendizado profundo no GitHub e você descobrirá que Python é apenas 25% -33% da base de código.].

4. Quis usar uma estrutura de dados definida em outro pacote e descobriu que não ia funcionar, e que você precisaria construir uma interface^[esse é um problema do ecossistema Python e, ainda que o R não sofra tanto com isso, também não é tão eficaz.].
**Julia permite que usuários compartilhem e reusem códigos de diferentes pacotes.**
A maior parte dos tipos e funções definidos pelos usuários de Julia, work right out of the box^[ou com pouquíssimo esforço.] e alguns usuários ficaram maravilhados ao descobrir como seus pacotes estão sendo usados por outras bibliotecas, das mais diversas formas, algo que nunca poderiam ter imaginado.
Temos alguns exempllos em @sec:multiple_dispatch.

5. Precisou de uma melhor gestão de projeto, with dependencies and version control tightly controlled, manageable, and replicable?
**Julia tem soluções incríveis para a gestão de projetos e um ótimo gerenciador de pacotes**.
Diferentemente dos gerenciadores de pacotes tradicionais, que instalam e gerenciam um único conjunto global de pacotes, o gerenciador de pacotes de Julia é projetado em torno de "ambientes":
conjuntos independentes de pacotes que podem ser locais para um projeto individual ou compartilhados entre projetos.
Cada projeto mantém, independentemente, seu próprio conjunto de versões de pacotes.

Se nós chamamos a sua ateção expondo situações familiares ou mesmo plausíveis, talvez você se interesse em aprender um pouco mais sobre Julia.

Vamos ccomeçar!

## O que Julia pretende alcançar? {#sec:julia_accomplish}

> **_NOTE:_**
> Nessa seção explicaremos com detalhe o que faz de Julia uma linguagem de programação brilhante.
> Se essa explicação for muito técnica para você, vá direto para @sec:dataframes to learn about tabular data with `DataFrames.jl`.

A linguagem de programação Julia [@bezanson2017julia] é relativamente nova, foi lançada em 2012, e procura ser **fácil e rápida**.
Ela "roda como C^[às vezes até mais rápido], mas lê como Python" [@perkelJuliaComeSyntax2019].
Foi feita para computação científica, capz de lidar com **uma grande quatidade de dados e a computação dos mesmos** sendo, ao mesmo tempo, **fácil de manipular, criar and prototipar códigos**.

Os criadores de Julia explicaram porque desenvolveram a linguagem [2012 blogpost](https://julialang.org/blog/2012/02/why-we-created-julia/).
Eles afirmam:

> Somos ambiciosos: queremos mais.
> Queremos uma linguagem open source, com uma licença liberal.
> Queremos a velocidade do C com o dinamismo do Ruby.
> Queremos uma linguagem que seja homoicônica, com verdadeiros macros como Lisp, mas com uma noção matemética óbvia e familiar como Matlab.
> Queremos algo que seja útil para programação em geral como Python, fácil para estatística como R, tão natural para processamento de string quanto Perl, tão poderoso para álgebra linear quanto Matlab, tão bom para colar programas juntos quanto shell.
> Algo que seja simples de aprender, mas que deixe os hackers mais sérios felizes.
> Queremos que seja interativo e compilado.

Most users are attracted to Julia because of the **superior speed**.
After all, Julia is a member of a prestigious and exclusive club.
The [**petaflop club**](https://www.hpcwire.com/off-the-wire/julia-joins-petaflop-club/) is comprised of languages who can exceed speeds of **one petaflop^[a petaflop is one thousand trillion, or one quadrillion, operations per second.] per second at peak performance**.
Currently only C, C++, Fortran, and Julia belong to the [petaflop club](https://www.nextplatform.com/2017/11/28/julia-language-delivers-petascale-hpc-performance/).

But, speed is not all that Julia can deliver.
The **ease of use**, **Unicode support**, and a language that makes **code sharing effortless** are some of Julia's features.
We'll address all those features in this section, but we want to focus on the Julia code sharing feature for now.

The Julia ecosystem of packages is something unique.
It enables not only code sharing but also allows sharing of user-created types.
For example, Python's `pandas` uses its own `Datetime` type to handle dates.
The same with R tidyverse's `lubridate` package, which also defines its own `datetime` type to handle dates.
Julia doesn't need any of this, it has all the date stuff already baked into its standard library.
This means that other packages don't have to worry about dates.
They just have to extend Julia's `DateTime` type to new functionalities by defining new functions and do not need to define new types.
Julia's `Dates` module can do amazing stuff, but we are getting ahead of ourselves now.
Let's talk about some other features of Julia.

### Julia Versus Other Programming Languages

In [@fig:language_comparison], a highly opinionated representation is shown that divides the main open source and scientific computing languages in a 2x2 diagram with two axes:
**Slow-Fast** and **Easy-Hard**.
We've omitted closed source languages because there are many benefits to allowing other people to run your code for free as well as being able to inspect the source code in case of issues.

We've put C++ and FORTRAN in the hard and fast quadrant.
Being static languages that need compilation, type checking, and other professional care and attention, they are really hard to learn and slow to prototype.
The advantage is that they are **really fast** languages.

R and Python go into the easy and slow quadrant.
They are dynamic languages that are not compiled and they execute in runtime.
Because of this, they are really easy to learn and fast to prototype.
Of course, this comes with a disadvantage:
they are **really slow** languages.

Julia is the only language in the easy and fast quadrant.
We don't know any other serious language that would want to be hard and slow, so this quadrant is left empty.

![Scientific Computing Language Comparisons: logos for FORTRAN, C++, Python, R and Julia.](images/language_comparisons.png){#fig:language_comparison}

**Julia is fast!
Very fast!**
It was designed for speed from the beginning.
It accomplishes this by multiple dispatch.
Basically, the idea is to generate very efficient LLVM[^LLVM] code.
LLVM code, also known as LLVM instructions, are very low-level, that is, very close to the actual operations that your computer is executing.
So, in essence, Julia converts your hand written and easy to read code to LLVM machine code which is very hard for humans to read, but easy for computers to read.
For example, if you define a function taking one argument and pass an integer into the function, then Julia will create a _specialized_ `MethodInstance`.
The next time that you pass an integer to the function, Julia will look up the `MethodInstance` that was created earlier and refer execution to that.
Now, the **great** trick is that you can also do this inside a function that calls a function.
For example, if some data type is passed into function `f` and `f` calls function `g` and the data types passed to `g` are known and always the same, then the generated function `g` can be hardcoded into function `f`!
This means that Julia doesn't even have to lookup `MethodInstances` any more, and the code can run very efficiently.
The trade-off, here, is that there are cases where earlier assumptions about the hardcoded `MethodInstances` are invalidated.
Then, the `MethodInstance` has to be recreated which takes time.
Also, the trade-off is that it takes time to infer what can be hardcoded and what not.
This explains why it can often take very long before Julia does the first thing:
in the background, it is optimizing your code.

The compiler in turns does what it does best: it optimizes machine code^[if you like to learn more about how Julia is designed you should definitely check @bezanson2017julia.].
You can find [benchmarks](https://julialang.org/benchmarks/) for Julia and several other languages here.
@fig:benchmarks was taken from [Julia's website benchmarks section^[please note that the Julia results depicted above do not include compile time.]](https://julialang.org/benchmarks/).
As you can see Julia is **indeed** fast.

![Julia versus other programming languages.](images/benchmarks.png){#fig:benchmarks}

We really believe in Julia.
Otherwise, we wouldn't be writing this book.
We think that Julia is the **future of scientific computing and scientific data analysis**.
It enables the user to develop rapid and powerful code with a simple syntax.
Usually, researchers develop code by prototyping using a very easy, but slow, language.
Once the code is assured to run correctly and fulfill its goal, then begins the process of converting the code to a fast, but hard, language.
This is known as the "Two-Language Problem" and we discuss next.

### The Two-Language Problem {#sec:two_language}

The "Two-Language Problem" is a very typical situation in scientific computing where a researcher devises an algorithm or a solution to tackle a desired problem or analysis at hand.
Then, the solution is prototyped in an easy to code language (like Python or R).
If the prototype works, the researcher would code in a fast language that would not be easy to prototype (C++ or FORTRAN).
Thus, we have two languages involved in the process of developing a new solution.
One which is easy to prototype but is not suited for implementation (mostly due to being slow).
And another which is not so easy to code, and consequently not easy to prototype, but suited for implementation because it is fast.
Julia avoids such situations by being the **same language that you prototype (ease of use) and implement the solution (speed)**.

Also, Julia lets you use **Unicode characters as variables or parameters**.
This means no more using `sigma` or `sigma_i`, and instead just use $σ$ or $σᵢ$ as you would in mathematical notation.
When you see code for an algorithm or for a mathematical equation, you see almost the same notation and idioms.
We call this feature **"One-To-One Code and Math Relation"** which is a powerful feature.

We think that the "Two-Language problem" and the "One-To-One Code and Math Relation" are best described by one of the creators of Julia, Alan Edelman, in a [TEDx Talk](https://youtu.be/qGW0GT1rCvs) [@tedxtalksProgrammingLanguageHeal2020].

<style>.embed-container { position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden; max-width: 100%; } .embed-container iframe, .embed-container object, .embed-container embed { position: absolute; top: 0; left: 0; width: 100%; height: 100%; }</style><div class='embed-container'><iframe src='https://www.youtube.com/embed/qGW0GT1rCvs' frameborder='0' allowfullscreen></iframe></div>

### Multiple Dispatch {#sec:multiple_dispatch}

Multiple dispatch is a powerful feature that allows us to extend existing functions or to define custom and complex behavior for new types.
Suppose that you want to define two new `struct`s to denote two different animals:

```jl
s = """
    abstract type Animal end
    struct Fox <: Animal
        weight::Float64
    end
    struct Chicken <: Animal
        weight::Float64
    end
    """
sc(s)
```

Basically, this says "define a fox which is an animal" and "define a chicken which is an animal".
Next, we might have one fox called Fiona and a chicken called Big Bird.

```jl
s = """
    fiona = Fox(4.2)
    big_bird = Chicken(2.9)
    """
sc(s)
```

Next, we want to know how much they weight together, for which we can write a function:

```jl
sco("combined_weight(A1::Animal, A2::Animal) = A1.weight + A2.weight")
```

And we want to know whether they go well together.
One way to implement that is to use conditionals:

```jl
s = """
    function naive_trouble(A::Animal, B::Animal)
        if A isa Fox && B isa Chicken
            return true
        elseif A isa Chicken && B isa Fox
            return true
        elseif A isa Chicken && B isa Chicken
            return false
        end
    end
    """
sco(s)
```

Now, let's see whether leaving Fiona and Big Bird together would give trouble:

```jl
scob("naive_trouble(fiona, big_bird)")
```

Okay, so this sounds right.
Writing the `naive_trouble` function seems to be easy enough. However, using despacho múltiplo to create a new function `trouble` can have their benefits. Let's create our new function as follows:

```jl
s = """
    trouble(F::Fox, C::Chicken) = true
    trouble(C::Chicken, F::Fox) = true
    trouble(C1::Chicken, C2::Chicken) = false
    """
sco(s)
```

After defining these methods, `trouble` gives the same result as `naive_trouble`.
For example:

```jl
scob("trouble(fiona, big_bird)")
```

And leaving Big Bird alone with another chicken called Dora is also fine

```jl
s = """
    dora = Chicken(2.2)
    trouble(dora, big_bird)
    """
scob(s)
```

So, in this case, the benefit of multiple dispatch is that you can just declare types and Julia will find the correct method for your types.
Even more so, for many cases when multiple dispatch is used inside code, the Julia compiler will actually optimize the function calls away.
For example, we could write:

```
function trouble(A::Fox, B::Chicken, C::Chicken)
    return trouble(A, B) || trouble(B, C) || trouble(C, A)
end
```

Depending on the context, Julia can optimize this to:

```
function trouble(A::Fox, B::Chicken, C::Chicken)
    return true || false || true
end
```

because the compiler **knows** that `A` is a Fox, `B` is a chicken and so this can be replaced by the contents of the method `trouble(F::Fox, C::Chicken)`.
The same holds for `trouble(C1::Chicken, C2::Chicken)`.
Next, the compiler can optimize this to:

```
function trouble(A::Fox, B::Chicken, C::Chicken)
    return true
end
```

Another benefit of multiple dispatch is that when someone else now comes by and wants to compare the existing animals to their animal, a Zebra, then that's possible.
In their package, they can define a Zebra:

```jl
s = """
    struct Zebra <: Animal
        weight::Float64
    end
    """
sc(s)
```

and also how the interactions with the existing animals would go:

```jl
s = """
    trouble(F::Fox, Z::Zebra) = false
    trouble(Z::Zebra, F::Fox) = false
    trouble(C::Chicken, Z::Zebra) = false
    trouble(Z::Zebra, F::Fox) = false
    """
sco(s)
```

Now, we can see whether Marty (our zebra) is safe with Big Bird:

```jl
s = """
    marty = Zebra(412)
    trouble(big_bird, marty)
    """
scob(s)
```

Even better, we can also calculate **the combined weight of zebra's and other animals without defining any extra function at our side**:

```jl
scob("combined_weight(big_bird, marty)")
```

So, in summary, the code that was written with only Fox and Chicken in mind works even for types that it **has never seen before**!
In practise, this means that Julia makes it often easy to re-use code from other projects.

If you are excited as much as we are by multiple dispatch, here are two more in-depth examples.
The first is a [fast and elegant implementation of a one-hot vector](https://storopoli.io/Bayesian-Julia/pages/1_why_Julia/#example_one-hot_vector) by @storopoli2021bayesianjulia.
The second is an interview with [Christopher Rackauckas](https://www.chrisrackauckas.com/) at [Tanmay Bakshi YouTube's Channel](https://youtu.be/moyPIhvw4Nk?t=2107) (see from time 35:07 onwards) [@tanmaybakshiBakingKnowledgeMachine2021].
Chris mentions that, while using [`DifferentialEquations.jl`](https://diffeq.sciml.ai/dev/), a package that he developed and currently maintains, a user filed an issue that his GPU-based quaternion ODE solver didn't work.
Chris was quite surprised by this request since he would never have expected that someone would combine GPU computations with quaternions and solving ODEs.
He was even more surprised to discover that the user made a small mistake and that it all worked.
Most of the merit is due to multiple dispatch and high user code/type sharing.

To conclude, we think that multiple dispatch is best explained by one of the creators of Julia:
[Stefan Karpinski at JuliaCon 2019](https://youtu.be/kc9HwsxE1OY).

<style>.embed-container { position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden; max-width: 100%; } .embed-container iframe, .embed-container object, .embed-container embed { position: absolute; top: 0; left: 0; width: 100%; height: 100%; }</style><div class='embed-container'><iframe src='https://www.youtube.com/embed/kc9HwsxE1OY' frameborder='0' allowfullscreen></iframe></div>


## Julia in the Wild {#sec:julia_wild}

In @sec:julia_accomplish, we explained why we think Julia is such a unique programming language.
We showed simple examples about the main features of Julia.
If you would like to have a deep dive on how Julia is being used, we have some **interesting use cases**:

1. NASA uses Julia in a supercomputer to analyze the ["Largest Batch of Earth-Sized Planets Ever Found"](https://exoplanets.nasa.gov/news/1669/seven-rocky-trappist-1-planets-may-be-made-of-similar-stuff/) and achieve a whopping **1,000x speedup** to catalog 188 million astronomical objects in 15 minutes.
2. [The Climate Modeling Alliance (CliMa)](https://clima.caltech.edu/) is using mostly Julia to **model climate in the GPU and CPU**.
Launched in 2018 in collaboration with researchers at Caltech, the NASA Jet Propulsion Laboratory, and the Naval Postgraduate School, CliMA is utilizing recent progress in computational science to develop an Earth system model that can predict droughts, heat waves, and rainfall with unprecedented precision and speed.
3. [US Federal Aviation Administration (FAA) is developing an **Airborne Collision Avoidance System (ACAS-X)** using Julia](https://youtu.be/19zm1Fn0S9M).
This is a nice example of the "Two-Language Problem" (see @sec:julia_accomplish).
Previous solutions used Matlab to develop the algorithms and C++ for a fast implementation.
Now, FAA is using one language to do all this: Julia.
4. [**175x speedup** for Pfizer's pharmacology models using GPUs in Julia](https://juliacomputing.com/case-studies/pfizer/).
It was presented as a [poster](https://chrisrackauckas.com/assets/Posters/ACoP11_Poster_Abstracts_2020.pdf) in the 11th American Conference of Pharmacometrics (ACoP11) and [won a quality award](https://web.archive.org/web/20210121164011/https://www.go-acop.org/abstract-awards).
5. [The Attitude and Orbit Control Subsystem (AOCS) of the Brazilian satellite Amazonia-1 is **written 100% in Julia**](https://discourse.julialang.org/t/julia-and-the-satellite-amazonia-1/57541) by Ronan Arraes Jardim Chagas (<https://ronanarraes.com/>).
6. [Brazil's national development bank (BNDES) ditched a paid solution and opted for open-source Julia modeling and gained a **10x speedup**.](https://youtu.be/NY0HcGqHj3g)

If this is not enough, there are more case studies in [Julia Computing website](https://juliacomputing.com/case-studies/).

[^readable]: no C++ or FORTRAN API calls.
[^LLVM]: LLVM stands for **L**ow **L**evel **V**irtual **M**achine, you can find more at the LLVM website (<http://llvm.org>).
