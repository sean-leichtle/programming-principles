# Programming Principles

There are certain universal laws and principles in software development that guide architects, programmers, and anyone needing to design software. This page lists quite a few of those principles, although it's far from complete. This page is a fork of [programming-principles repository by Lars Kappert](https://github.com/webpro/programming-principles), who has done most of the work collecting the material.

## KISS

Most systems work best if they are kept simple rather than made complex.

Why

- Less code takes less time to write, has less bugs, and is easier to modify.
- Simplicity is the ultimate sophistication.
- It seems that perfection is reached not when there is nothing left to add, but
  when there is nothing left to take away.

Resources

- [KISS principle](https://en.wikipedia.org/wiki/KISS_principle)
- [Keep It Simple Stupid (KISS)](http://principles-wiki.net/principles:keep_it_simple_stupid)

## YAGNI

YAGNI stands for "you aren't gonna need it": don't implement something until it
is necessary.

Why

- Any work that's only used for a feature that's needed tomorrow, means losing
  effort from features that need to be done for the current iteration.
- It leads to code bloat; the software becomes larger and more complicated.

How

- Always implement things when you actually need them, never when you just
  foresee that you need them.

Resources

- [You Arent Gonna Need It](http://c2.com/xp/YouArentGonnaNeedIt.html)
- [You’re NOT gonna need it!](https://ronjeffries.com/xprog/articles/practices/pracnotneed/)
- [You aren't gonna need it](https://en.wikipedia.org/wiki/You_aren%27t_gonna_need_it)

## Do The Simplest Thing That Could Possibly Work

Why

- Real progress against the real problem is maximized if we just work on what
  the problem really is.

How

- Ask yourself: "What is the simplest thing that could possibly work?"

Resources

- [Do The Simplest Thing That Could Possibly Work](http://c2.com/xp/DoTheSimplestThingThatCouldPossiblyWork.html)

## Separation of Concerns

Separation of concerns is a design principle for separating a computer program
into distinct sections, such that each section addresses a separate concern. For
example the business logic of the application is a concern and the user
interface is another concern. Changing the user interface should not require
changes to business logic and vice versa.

Quoting [Edsger W. Dijkstra](https://en.wikipedia.org/wiki/Edsger_W._Dijkstra)
(1974):

> It is what I sometimes have called "the separation of concerns", which, even
> if not perfectly possible, is yet the only available technique for effective
> ordering of one's thoughts, that I know of. This is what I mean by "focusing
> one's attention upon some aspect": it does not mean ignoring the other
> aspects, it is just doing justice to the fact that from this aspect's point of
> view, the other is irrelevant.

Why

- Simplify development and maintenance of software applications.
- When concerns are well-separated, individual sections can be reused, as well
  as developed and updated independently.

How

- Break program functionality into separate modules that overlap as little as
  possible.

Resources

- [Separation of Concerns](https://en.wikipedia.org/wiki/Separation_of_concerns)

## Keep things DRY

Every piece of knowledge must have a single, unambiguous, authoritative
representation within a system.

Each significant piece of functionality in a program should be implemented in
just one place in the source code. Where similar functions are carried out by
distinct pieces of code, it is generally beneficial to combine them into one by
abstracting out the varying parts.

Why

- Duplication (inadvertent or purposeful duplication) can lead to maintenance
  nightmares, poor factoring, and logical contradictions.
- A modification of any single element of a system does not require a change in
  other logically unrelated elements.
- Additionally, elements that are logically related all change predictably and
  uniformly, and are thus kept in sync.

How

- Put business rules, long expressions, if statements, math formulas, metadata,
  etc. in only one place.
- Identify the single, definitive source of every piece of knowledge used in
  your system, and then use that source to generate applicable instances of that
  knowledge (code, documentation, tests, etc).
- Apply the
  [Rule of three](<https://en.wikipedia.org/wiki/Rule_of_three_(computer_programming)>).

Resources

- [Dont Repeat Yourself](http://wiki.c2.com/?DontRepeatYourself)
- [Don't repeat yourself](https://en.wikipedia.org/wiki/Don't_repeat_yourself)
- [DRY Principle: Its Benefit and Cost with Examples](https://thevaluable.dev/dry-principle-cost-benefit-example/)

Related

- [Abstraction principle](<https://en.wikipedia.org/wiki/Abstraction_principle_(computer_programming)>)
- [Once And Only Once](http://wiki.c2.com/?OnceAndOnlyOnce) is a subset of DRY
  (also referred to as the goal of refactoring).
- [Single Source of Truth](https://en.wikipedia.org/wiki/Single_Source_of_Truth)
- A violation of DRY is [WET](http://thedailywtf.com/articles/The-WET-Cart)
  (Write Everything Twice)
- [Be careful with the code metric "duplicated lines"](https://rachelcarmena.github.io/2018/02/27/duplication-you-are-welcome.html)

## Code For The Maintainer

Why

- Maintenance is by far the most expensive phase of any project.

How

- _Be_ the maintainer.
- Always code as if the person who ends up maintaining your code is a violent
  psychopath who knows where you live.
- Always code and comment in such a way that if someone a few notches junior
  picks up the code, they will take pleasure in reading and learning from it.
- [Don't make me think](http://www.sensible.com/dmmt.html).
- Use the
  [Principle of Least Astonishment](https://en.wikipedia.org/wiki/Principle_of_least_astonishment).

Resources

- [Code For The Maintainer](http://wiki.c2.com/?CodeForTheMaintainer)
- [The Noble Art of Maintenance Programming](https://blog.codinghorror.com/the-noble-art-of-maintenance-programming/)

## Avoid Premature Optimization

Quoting [Donald Knuth](https://en.wikiquote.org/wiki/Donald_Knuth):

> Programmers waste enormous amounts of time thinking about, or worrying about,
> the speed of noncritical parts of their programs, and these attempts at
> efficiency actually have a strong negative impact when debugging and
> maintenance are considered. We should forget about small efficiencies, say
> about 97% of the time: premature optimization is the root of all evil. Yet we
> should not pass up our opportunities in that critical 3%.

Understanding what is and isn’t "premature" is critical of course.

Why

- It is unknown upfront where the bottlenecks will be.
- After optimization, it might be harder to read and thus maintain.

How

- [Make It Work Make It Right Make It Fast](http://wiki.c2.com/?MakeItWorkMakeItRightMakeItFast)
- Don't optimize until you need to, and only after profiling you discover a
  bottleneck optimise that.

Resources

- [Program optimization](https://en.wikipedia.org/wiki/Program_optimization)
- [Premature Optimization](http://wiki.c2.com/?PrematureOptimization)

## Minimise Coupling

Coupling between modules/components is their degree of mutual interdependence;
lower coupling is better. In other words, coupling is the probability that code
unit "B" will "break" after an unknown change to code unit "A".

Why

- A change in one module usually forces a ripple effect of changes in other
  modules.
- Assembly of modules might require more effort and/or time due to the increased
  inter-module dependency.
- A particular module might be harder to reuse and/or test because dependent
  modules must be included.
- Developers might be afraid to change code because they aren't sure what might
  be affected.

How

- Eliminate, minimise, and reduce complexity of necessary relationships.
- By hiding implementation details, coupling is reduced.
- Apply the [Law of Demeter](#law-of-demeter).

Resources

- [Coupling](<https://en.wikipedia.org/wiki/Coupling_(computer_programming)>)
- [Coupling And Cohesion](http://wiki.c2.com/?CouplingAndCohesion)

## Law of Demeter

Don't talk to strangers.

Why

- It usually tightens coupling
- It might reveal too much implementation details

How

A method of an object may only call methods of:

1. The object itself.
2. An argument of the method.
3. Any object created within the method.
4. Any direct properties/fields of the object.

Resources

- [Law of Demeter](https://en.wikipedia.org/wiki/Law_of_Demeter)
- [The Law of Demeter Is Not A Dot Counting Exercise](https://haacked.com/archive/2009/07/14/law-of-demeter-dot-counting.aspx/)

## Composition Over Inheritance

Why

- Less coupling between classes.
- Using inheritance, subclasses easily make assumptions, and break LSP.

How

- Test for LSP (substitutability) to decide when to inherit.
- Compose when there is a "has a" (or "uses a") relationship, inherit when "is
  a".

Resources

- [Favor Composition Over Inheritance](https://blogs.msdn.microsoft.com/thalesc/2012/09/05/favor-composition-over-inheritance/)

## Orthogonality

> The basic idea of orthogonality is that things that are not related
> conceptually should not be related in the system.

Source: [Be Orthogonal](https://www.artima.com/intv/dry3.html)

> It is associated with simplicity; the more orthogonal the design, the fewer
> exceptions. This makes it easier to learn, read and write programs in a
> programming language. The meaning of an orthogonal feature is independent of
> context; the key parameters are symmetry and consistency.

Source:
[Orthogonality](<https://en.wikipedia.org/wiki/Orthogonality_(programming)>)

## Robustness Principle

> Be conservative in what you do, be liberal in what you accept from others

Collaborating services depend on each others interfaces. Often the interfaces
need to evolve causing the other end to receive unspecified data. A naive
implementation refuses to collaborate if the received data does not strictly
follow the specification. A more sophisticated implementation will still work
ignoring the data it does not recognize.

Why

- In order to be able to evolve services you need to ensure that a provider can
  make changes to support new demands while causing minimal breakage to their
  existing clients.

How

- Code that sends commands or data to other machines (or to other programs on
  the same machine) should conform completely to the specifications, but code
  that receives input should accept non-conformant input as long as the meaning
  is clear.

Resources

- [Robustness Principle in Wikipedia](https://en.wikipedia.org/wiki/Robustness_principle)
- [Tolerant Reader](https://martinfowler.com/bliki/TolerantReader.html)

## Inversion of Control

Inversion of Control is also known as the Hollywood Principle, "Don't call us,
we'll call you". It is a design principle in which custom-written portions of a
computer program receive the flow of control from a generic framework. Inversion
of control carries the strong connotation that the reusable code and the
problem-specific code are developed independently even though they operate
together in an application.

Why

- Inversion of control is used to increase modularity of the program and make it
  extensible.
- To decouple the execution of a task from implementation.
- To focus a module on the task it is designed for.
- To free modules from assumptions about how other systems do what they do and
  instead rely on contracts.
- To prevent side effects when replacing a module.

How

- Using Factory pattern
- Using Service Locator pattern
- Using Dependency Injection
- Using contextualized lookup
- Using Template Method pattern
- Using Strategy pattern

Resources

- [Inversion of Control in Wikipedia](https://en.wikipedia.org/wiki/Inversion_of_control)
- [Inversion of Control Containers and the Dependency Injection pattern](https://www.martinfowler.com/articles/injection.html)

## Maximise Cohesion

Cohesion of a single module/component is the degree to which its
responsibilities form a meaningful unit; higher cohesion is better.

Why

- Increased difficulty in understanding modules.
- Increased difficulty in maintaining a system, because logical changes in the
  domain affect multiple modules, and because changes in one module require
  changes in related modules.
- Increased difficulty in reusing a module because most applications won’t need
  the random set of operations provided by a module.

How

- Group related functionalities sharing a single responsibility (e.g. in a
  class).

Resources

- [Cohesion](<https://en.wikipedia.org/wiki/Cohesion_(computer_science)>)
- [Coupling And Cohesion](http://wiki.c2.com/?CouplingAndCohesion)

## Liskov Substitution Principle

The LSP is all about expected behavior of objects:

> Objects in a program should be replaceable with instances of their subtypes
> without altering the correctness of that program.

Resources

- [Liskov substitution principle](https://en.wikipedia.org/wiki/Liskov_substitution_principle)
- [Liskov Substitution Principle](http://www.blackwasp.co.uk/lsp.aspx)

## Open/Closed Principle

Software entities (e.g. classes) should be open for extension, but closed for
modification. I.e. such an entity can allow its behavior to be modified without
altering its source code.

Why

- Improve maintainability and stability by minimizing changes to existing code.

How

- Write classes that can be extended (as opposed to classes that can be
  modified).
- Expose only the moving parts that need to change, hide everything else.

Resources

- [Open Closed Principle](https://en.wikipedia.org/wiki/Open/closed_principle)
- [The Open Closed Principle](https://blog.cleancoder.com/uncle-bob/2014/05/12/TheOpenClosedPrinciple.html)

## Single Responsibility Principle

A class should never have more than one reason to change.

Long version: Every class should have a single responsibility, and that
responsibility should be entirely encapsulated by the class. Responsibility can
be defined as a reason to change, so a class or module should have one, and only
one, reason to change.

Why

- Maintainability: changes should be necessary only in one module or class.

How

- Apply [Curly's Law](#curlys-law).

Resources

- [Single responsibility principle](https://en.wikipedia.org/wiki/Single_responsibility_principle)

## Hide Implementation Details

A software module hides information (i.e. implementation details) by providing
an interface, and not leak any unnecessary information.

Why

- When the implementation changes, the interface clients are using does not have
  to change.

How

- Minimize accessibility of classes and members.
- Don’t expose member data in public.
- Avoid putting private implementation details into a class’s interface.
- Decrease coupling to hide more implementation details.

Resources

- [Information hiding](https://en.wikipedia.org/wiki/Information_hiding)

## Curly's Law

Curly's Law is about choosing a single, clearly defined goal for any particular
bit of code: Do One Thing.

- [Curly's Law: Do One Thing](https://blog.codinghorror.com/curlys-law-do-one-thing/)
- [The Rule of One or Curly’s Law](http://grsmentor.com/blog/the-rule-of-one-or-curlys-law/)

## Encapsulate What Changes

A good design identifies the hotspots that are most likely to change and
encapsulates them behind an API. When an anticipated change then occurs, the
modifications are kept local.

Why

- To minimize required modifications when a change occurs

How

- Encapsulate the concept that varies behind an API
- Possibly separate the varying concept into its own module

Resources

- [Encapsulate the Concept that Varies](http://principles-wiki.net/principles:encapsulate_the_concept_that_varies)
- [Encapsulate What Varies](https://blogs.msdn.microsoft.com/steverowe/2007/12/26/encapsulate-what-varies/)
- [Information hiding](https://en.wikipedia.org/wiki/Information_hiding)

## Interface Segregation Principle

Reduce fat interfaces into multiple smaller and more specific client specific
interfaces. An interface should be more dependent on the code that calls it than
the code that implements it.

Why

- If a class implements methods that are not needed the caller needs to know
  about the method implementation of that class. For example if a class
  implements a method but simply throws then the caller will need to know that
  this method shouldn't actually be called.

How

- Avoid fat interfaces. Classes should never have to implement methods that
  violate the
  [Single responsibility principle](#single-responsibility-principle).

Resources

- [Interface segregation principle](https://en.wikipedia.org/wiki/Interface_segregation_principle)

## Boy-Scout Rule

The Boy Scouts of America have a simple rule that we can apply to our
profession: "Leave the campground cleaner than you found it". The boy-scout rule
states that we should always leave the code cleaner than we found it.

Why

- When making changes to an existing codebase the code quality tends to degrade,
  accumulating technical debt. Following the boyscout rule, we should mind the
  quality with each commit. Technical debt is resisted by continuous
  refactoring, no matter how small.

How

- With each commit make sure it does not degrade the codebase quality.
- Any time someone sees some code that isn't as clear as it should be, they
  should take the opportunity to fix it right there and then.

Resources

- [Opportunistic Refactoring](https://martinfowler.com/bliki/OpportunisticRefactoring.html)

## Command Query Separation

The Command Query Separation principle states that each method should be either
a command that performs an action or a query that returns data to the caller but
not both. Asking a question should not modify the answer.

With this principle applied the programmer can code with much more confidence.
The query methods can be used anywhere and in any order since they do not mutate
the state. With commands one has to be more careful.

Why

- By clearly separating methods into queries and commands the programmer can
  code with additional confidence without knowing each method's implementation
  details.

How

- Implement each method as either a query or a command
- Apply naming convention to method names that implies whether the method is a
  query or a command

Resources

- [Command Query Separation in Wikipedia](https://en.wikipedia.org/wiki/Command%E2%80%93query_separation)
- [Command Query Separation by Martin Fowler](https://martinfowler.com/bliki/CommandQuerySeparation.html)

## Murphy's Law

> Anything that can go wrong will go wrong.

It seems to be a universal law that when there is even the smallest possibility of something going wrong, it eventually will go wrong. It makes total sense when we think about probabilities and an infinite amount of trials. The law also applies to software development.

Resources

- [Murphy's law in Wikipedia](https://en.wikipedia.org/wiki/Murphy%27s_law)

## Brooks's Law

> Adding manpower to a late software project makes it later.

The law is related to software project management and was introduced by Fred Brooks in his famous book 'The Mythical Man-Month'. The essence of the law is that adding new developers to a software project does not make them productive immediately but conversely takes time from the other team members due to communication overhead.

Resources

- [Brooks's law in Wikipedia](https://en.wikipedia.org/wiki/Brooks%27s_law)

## Linus's Law

> Given enough eyeballs, all bugs are shallow.

The law is originating from the book 'The Cathedral and the Bazaar' by Eric S. Raymond and was named in honor of the famous Finnish inventor of Linux operating system, Linus Torvalds. It's basically a praise to software reviewing process where multiple developers inspect the piece of code before it's accepted and merged.

Resources

- [Linus's law in Wikipedia](https://en.wikipedia.org/wiki/Linus%27s_law)
