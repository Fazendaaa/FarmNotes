# FarmNotes
> Notes in the my learning process.

Reading notes about clean code. Books that read about it:
* [Clean Code](https://www.amazon.com.br/Clean-Code-Handbook-Software-Craftsmanship-ebook/dp/B001GSTOAM?__mk_pt_BR=%C3%85M%C3%85%C5%BD%C3%95%C3%91&keywords=Clean+Code&qid=1525260282&sr=8-3&ref=sr_1_3)
* [Pragmatic Programmer](https://pragprog.com/book/tpp/the-pragmatic-programmer)
* [Refactoring](https://www.amazon.com/Refactoring-Improving-Existing-Addison-Wesley-Signature/dp/0134757599)

And some others mentioned though out this notes.

The notes taken are based in those books and some of my own, through my own experience. The idea behind this project is to make an open book that anyone could copy, add and modify due your own needs; a collaborative way to improve software development through the learning process of making it easy for others to understand.

First advice is to have right by your side a Design Patterns by GoF to follow along some concepts; I bought mine used through a site called [Estante Virtual](https://www.estantevirtual.com.br/); I know the Design Patterns are more OOP related but most books reference it and even not reading in its wholesome, is a good addition to have, it might help you out understand what some authors really want to mean.

A good first tip about writing code before reading any of this tips is: _"Trust no one, including yourself."_

- [FarmNotes](#farmnotes)
    - [The 5S](#the-5s)
    - [The overview](#the-overview)
        - [Before going any further](#before-going-any-further)
    - [The Art of Clean Code?](#the-art-of-clean-code)
    - [Design By Contract](#design-by-contract)
    - [Naming variables](#naming-variables)
    - [Functions](#functions)
    - [Don't Repeat Yourself(DRY)](#dont-repeat-yourselfdry)
    - [We Dont Need It Yet (WDNIY)](#we-dont-need-it-yet-wdniy)
    - [Orthogonality](#orthogonality)
    - [Comments](#comments)
    - [Formatting](#formatting)
    - [Error Handling](#error-handling)
    - [Boundaries](#boundaries)
    - [Artificial coupling](#artificial-coupling)
    - [Three Laws of TDD](#three-laws-of-tdd)
    - [F.I.R.S.T.](#first)
    - [Here We Go](#here-we-go)
        - [Cohesion](#cohesion)
        - [Open-Closed Principle (OCP)](#open-closed-principle-ocp)
        - [Dependency Inversion Principle (DIP)](#dependency-inversion-principle-dip)
        - [Systems](#systems)
    - [Emergence](#emergence)
    - [Concurrency](#concurrency)
    - [Successive Refinement](#successive-refinement)
        - [Refactoring](#refactoring)
    - [Logic](#logic)
        - [If or while statements](#if-or-while-statements)
        - [Comparison](#comparison)
        - [Memory allocation](#memory-allocation)
    - [Variables](#variables)
    - [Abstractions](#abstractions)
        - [Avoid Transitive Navigation](#avoid-transitive-navigation)
    - [Code review](#code-review)
    - [What I felt that is missing](#what-i-felt-that-is-missing)
    - [What I felt true](#what-i-felt-true)
    - [Recommend reading](#recommend-reading)

## The 5S
In 1951, the japanese **Total Productive Maintenance(TPM)** culture instaure the _5S_:

* Seiri (_"Sort"_): knowing what and when;
* Seiton (_"Systematize"_): everything has it's place;
* Seiso (_"Shine"_): it must speak by itself;
* Siketsu (_"Standardization"_): follow the rules;
* Shutsuke (_"Self-discipline"_): reflect on one's work and be willing tho change.

This is also related to the "kaizen" word, which is related to the concept of small daily changes and improvements.

## The overview
The act of design must be, by itself, as an small local act of repair. In the book is said that the simple act of code indentation could reduce considerably the number of bugs in a back-of-the-envelope discover at Bell Labs; but I didn't find anything about this that endorses this idea.

Wanding is the act of "wonder around" a bad code in a way that repels you of making anything. Probably because who wrote the code followed the [LeBlanc's Law](https://en.wikipedia.org/wiki/Talk%3AList_of_eponymous_laws#Proposal_to_add_LeBlanc's_law): _"later equals never"_.

And just a friendly reminder from the Unix philosophy: _"Robustness is the child of transparency and simplicity."_

### Before going any further
_"What is the most important thing in a software?"_
* Performance
* Safety
* Documentation
* Using a solid framework
* Doing what needs to be done
* Making it readable
* other: ___________________________

That's what I call a tricky question, I don't really think there's a right or wrong question, your use case is what really is the important and the quality level needed for it. As mentioned in the Pragmatic Programmer: _"Great software today is often preferable to perfect software tomorrow."_

All of this is related to the chosen approach to the problem, but that doesn't mean that they can't be related in a near future, a code written in a higher level of abstraction allows you to solve the problem itself without having to worry on solving domain problems; but, later on, you can improve this established code in a low level, improving its performance.

## The Art of Clean Code?
Programming is a kind of art: the artists want make something beautiful and new, even if is not that new for the whole world or actually all the beautiful... But is new and beautiful to them. And that's why a team stuck with a bad code loses it's productivity also, because no one is creating something.

Being able to spot a bad code doesn't mean that you know how to fix or even re-factoring making it a better one. The one who seeks the best isn't always the one who finds it.

Coding is the final tool, anyone can measure anything through it: efficiency, manutenability, readability, "monolitch"(bility), even the worstability! And that means that, someone behind the keyboard who wrote it, can be measure also; the funny thing is that is "easy" for a code to be good at something at some point and bad at all things all the way, this feeling of "at least one" that can make some programmers ego goes up and become lazy to improve. Nonetheless to say that those ugly things that make the code bad could make it not work at all after some time.

MacBook's dictionary definition of crisp: _"briskly decisive and matter-of-fact, without hesitation or unnecessary detail."_... That being said, a good code should be at least a crisp one.

One definition of clean code that I particularly liked a lot is that a clean code makes it easy for other people to enhance it, and that's is linked to "Big" Dave Thomas, founder of OTI. I do really like when someone do a code review of something that I've wrote, but if there's nothing add to it the empty feels fulls me up -- no pun intended hahahah

![xkcd](https://imgs.xkcd.com/comics/automation.png)

## Design By Contract
_"Any fool can write code that a computer can understand. Good programmers write code that humans can understand."_ -- FOWLER, Martin.

Before writing any line of code (loc) one must first write good tests for it, a TDD approach that can be improved by the [three laws of TDD](#three-laws-of-tdd). Design By Contract (DBC) is a step further of documentation and sequentially a code improvement.

Right after you wrote your tests, you should also document the function beforehand; this will help you out to review the code scope right before implement it. Right after this you can see if any changes might be done and then make them.

The DBC is this step were you explicit tell to other what your code must do, but first you remind yourself of it. This will aid you, guiding it each step of the way.

A TypeScript example, using the [TypeDoc](http://typedoc.org/) notation:
```TS
/*
 * Sum the given values
 * 
 * @param x - first value
 * @param y - second value
 *
 * @example
 * add(1, 2)
 * add(3, 2)
 * add(1, 3)
 *
 * @returns the result
 */
const add = (x: number, y: number): number => x + y;
```

**note**: I do personally prefer type languages due to its easy to read and document capabilities. Besides that, languages that also don't allow automatic casting for me are the best ones due to its expressiveness when writing something that might fail and the compiler or interpreter won't throw an error or warning in some cases and it will works just fine; this could lead to some hours of debugging when testing it the code without even notice this "problem".

## Naming variables
A good abbreviation could be a disinformative one also;

Do not use structure names on variables like queue or list, even if they do represent a variable that is one of them could you future-proof this?

Names that should be avoided:
* **a**
* **an**
* **the**
* **info**
* **new**
* **data**
* etc

Other tips:

* Use searchable names
* Methods should have a verb or a verb phrase names
* Pick only one, don't use fetch, retrieve or get through out the code
* Add a meaningful context -- that reminds me, in a way, One level of indentation per method from [Object Calisthenics](https://gist.github.com/suissa/79aa860161b13e50e5fa3a0120fb6d68)
* Don't add more context to a name more than necessary

## Functions
> "The first rule of functions is that they should be small. The second rule of functions is that they should be smaller.";

This is more old than my grandma, but: _"Functions should do one thing. They should do it well. They should do it only"_.

_"The smaller and more focused a function is, the easier it is to choose a descriptive name."_

This one is a little bit tricky, for me especially:

_"The ideal number of arguments for a function is zero (niladic). Next comes one (monadic), followed closely by two (dyadic). Three arguments (triadic) should be avoided where possible. More than three (polyadic) requires a very special justification -- and then shouldn't be used anyway."_

Other tips are:

* Creating objects to aggregate variables isn't cheating!
* _"Functions should either do something or answer something, but not both"_
* Give it a try to try/catch blocks
* Functions that handles errors, **ONLY** handles errors

## Don't Repeat Yourself(DRY)
In the book this part is one of the functions parts but I think it's worth it to add more to it later on.

_"Duplication may be the root of all evil in software"_ -- To a given extend, I couldn't agree more.

_"Every time you see duplication in the code, it represents a missed opportunity for abstraction"_.

The funny thing about abstraction is that they might be irrelevant when you are doing some classwork or something like it but try to go a step even further, when you don't always know all of the code, to see that abstraction helps you write code when you are using something wrote by others. A simple example is to see that you know that a print function expects variables and sometimes a mask, but do you know how they are processed and shown in your console? Anyway you expected to work properly because the abstraction point is in a level that you don't have to care with lesser important matter of it. [Codeclimate](https://codeclimate.com/) is the support that I use for this part in my projects.

## We Dont Need It Yet (WDNIY)
* _"Always implement things when you actually need them, never when you just foresee that you need them."_
* _"Solving tomorrow's problem is an excellent avoidance strategy, because you can't be proven wrong."_ - Kent Beck

more about it [here](http://wiki.c2.com/?WeDontNeedItYet)

## Orthogonality
From Pragmatic Programmer:

_"When components are isolated from one another, you know that you can change one without having to worry about the rest. As long as you don't change the component's external interfaces, you can be comfortable that you won't cause problems that ripple through the entire system."_

_"You get two major benefits if you write orthogonal systems: increased productivity and reduced risk."_

_"Don't rely on the properties of things you can't control."_

## Comments
> "Comments should explain the why, not the what" - Unknown

Comments are last resource tools, if you need a comment, stop, rethink it and than try it to refactor the code, even then if you fail to do so, and only then, write a code to better explain yourself.

TODO comments could be a nice reminder to pick up the things were we were left off.

## Formatting
Lost this notes due internet connection errors -- need to read Clean Code again.

Hadley Wickham engraved a interesting new term in [Advanced R](http://adv-r.had.co.nz/): _"Dagwood Sandwich"_. This means a call that have many parenthesis side by side:

```R
# bad
Fee(1, Fie(2, Foe(3, Foo(4))))

# good
Fee(Fie(Foe(Foo(4), 3), 2), 1)

```

## Error Handling
_"Error handling is important, but if it obscures logic, IT'S WRONG"_.

Use exceptions rather than return codes — that means if the language supports try, catch and finally statements you should probably being using it;

I didn't know that checked exceptions is an Open/Closed Principle violation.

_"It doesn't really matter whether the bug is your fault or someone else's. It still your problem."_

## Boundaries
When using third-parties packages before anything else, write some codes for it; this will ensure that they work the way is expected to and, after bound to the system, the time that otherwise you would spend writing new test for it would be considerably reduced.

Tests are a great way to understand the work of others.

## Artificial coupling
Is joining two or more modules that serves no direct purpose in a temporarily convenient location.

## Three Laws of TDD
_"Program testing can be used to show the presence of bugs, but never to show their absence."_ - Dijkstra

[Test Driven Development](https://www.amazon.com/Test-Driven-Development-Kent-Beck/dp/0321146530)

* You may not write production code until you have written a failing unit test
* You may not write more of a unit test than is sufficient to fail, and not compiling is failing
* You may not write more production code than is sufficient to pass the currently failing test

See more at this [link](https://www.computer.org/csdl/mags/so/2007/03/s3032-abs.html).

## F.I.R.S.T.
Rules for a clean testing:

* Fast: a slow test results in a slow fix it, letting the code to rot
* Independent: when one test de depend on another one, the first one to fail causes a cascade of failures, making it hard to diagnosis
* Repeatable: if the only work in one specific machine would they really be testing all kind of environment? No! Tests should run in any machine because te real code will run too
* Self-validating: either they pass or fail
* Timely: tests comes before the coding

## Here We Go
![xkcd](https://imgs.xkcd.com/comics/standards.png)

**The Single Responsibility Principle (SRP)**
* _"You should have one responsibility -- one reason to change"_.

### Cohesion
* A method should manipulate one or more variables; the more manipulates the more cohesive it's, which is not advisable to do it because a high co-dependency increasing logical as a whole.

### Open-Closed Principle (OCP)
_"Classes should be open for extension but closed for modification."_

### Dependency Inversion Principle (DIP)
_"Classes should depend upon abstractions, not on concrete details."_

### Systems
Clean code is a mean to a way of management of low level abstractions, higher ones are managed through the system level.

It's better to read the book on this one.

## Emergence
Kent Beck's four rules of Simple Design:

* Runs all the tests -- if you cannot test, you cannot ensure that it works properly -- even testing this is a bold statement to do it, so be cautious about it
* Contains no duplication
* Expresses the intent of the programmer -- using the pattern applied as name for a method is a good design
* Minimizes the number of classes and methods

## Concurrency
[Concurrency](https://en.wikipedia.org/wiki/Concurrency_(computer_science)) is about breaking the what gets done from when gets done -- single-thread couple those concepts.

Concurrency is an extensive subject, reading the Wikipedia page about it before proceeding is advised. It's a short reading. And other concepts also:

* ​[Producer-Consumer](https://en.wikipedia.org/wiki/Producer%E2%80%93consumer_problem)
* [Readers-Writers](https://en.wikipedia.org/wiki/Readers%E2%80%93writers_problem)
* [​Dining Philosophers](https://en.wikipedia.org/wiki/Dining_philosophers_problem)

Concurrency problems are not so easy to solve, especially when some of the threads are running in the client-side because the system itself looses some of the control compared to those running on the server-side.

About testing concurrent code, it's better to read the book since would take the same amount of words to describe it here. And besides that, reading the Appendix about concurrency it's like reading another different book by itself, more worth it then I've expected.

## Successive Refinement
Instead of saying that a perfect code doesn't exists, answer the following questions:

* _Is there a language that never has updates that broke/deprecates previous code or patch something?_
* _You always know everything that has to be known?_
* _A program always control everything that has to be controlled on the environment on which is running?_

Then how a "perfect" code should exists in this world?

A good code is good as long the one who wrote it and always will be something to improving since we are improving all the time, change languages and bringing some concepts from others backgrounds, seeing the code made it by others. Code is like wine, it's gets better with time.

_"Refactoring is a lot like solving a Rubik's cube. There are lots of little steps required to achieve a large goal. Each step enables the next."_

Besides that, requirements, growing scale, hardware updates, etc, change faster than the code developed to it can keep its pace.

One thing to keep in mind when refining code is [The Principle of Least Astonishment](https://en.wikipedia.org/wiki/Principle_of_least_astonishment).

### Refactoring
While seeking to improve a current code base:
1. First, write down tests for the current code
2. Make it more readable through renaming it variables, functions, methods
3. Break it apart
4. Start to move things a little
5. Add new things
6. Make major changes
7. _"RELEASE THE KRAKEN!!!"_ - JONES, Davy

## Logic
### If or while statements
Plain Text 
```typescript
if (isPayDay(date))
```

Is better than:
```typescript
if ("Monday" == date.dayOfWeek && "First" == date.weekOfMonth)
```

And, besides that, avoid negatives conditionals.

### Comparison
When comparing something, a good practice is to put the value first. So, instead of doing:
```c
if (answerToAllQuestions == 42)
```

Try it doing:
```c
if (42 == answerToAllQuestions)
```

That's because if you mis-type and forget to put a equal from a comparison it will become an attribution:
```c
if (answerToAllQuestions = 42)
```

Which many compilers won't catch as an error or even a warning since comparisons like the following are allowed but are not a clean way to read a code:
```c
if ((myPointer = malloc(sizeof(int) * 42)) != NULL)
```

### Memory allocation
Some awesome tips from Pragmatic Programmer are:

_"1. Deallocate resources in the opposite order to that in which you allocate them. That way you won't orphan resource if one resource contains references to another."_

_"2. When allocating the same set of resources in different places in your code, always allocate them in the same order. This will reduce the possibility of deadlock."_

## Variables
If you had to declare a variable in the middle of the code, probably this part of the code should be in another function.

## Abstractions
Remember that what is different than how:

```ruby
def printScoreboard (Team A, Team B)
    puts "Time: " Time
    puts "Home: " A.name " Shots on goals" A.goals
    puts "Half: " Match.half
    puts "Visitors: " B.name " Shots on goals"  B.goals
end
```

`printScoreboard` should not know how to the data is parsed but only know that needs to call it the functions that print them:
```ruby
def printTime
    puts "Time: " Time
end
​
def printHalf
    puts "Half: " Match.half
end
​
def printHomeTeam (Team team)
    puts "Home: " team.name " Shots on goals: " team.goals
end
​
def printVisitorsTeam (Team team)
    puts "Visitors: " team.name " Shots on goals: " team.goals
end
​
def printScoreboard (Team A, Team B)
    printTime()
    printHomeTeam(A)
    printHalf()
    printVisitorsTeam(B)
end
```

This sounds more difficult than appears? Because it is!

### Avoid Transitive Navigation
JavaScript programmers are going to hate this but, aside from Promises, why keeping navigation through a variable that anyone who reads the code besides you are going to think that as _"what the fu... 'heck' is going on here?"_ aka [train wreck](http://www.thinkcode.se/blog/2011/12/30/how-many-train-wrecks-are-lurking-in-your-code).
```typescript
const meaningOfLife = World.getHumans().getPerson("John Doe").getTastes().sort()[0]
```

Should be:
```typescript
const humans = World.getHumans()
const you = humans.getPerson("John Doe")
const tastes = you.getTastes()
const meaningOfLife = tastes.sort()[0]
```

## Code review
When doubting about your code, find someone to read it without you having to explaining it; listen to this person feedback a take some lessons from it. This might help you improve you current project.

Having to always look at the same code and expect to find something new to improve is kind like to throw a dice that always shows the same side expecting to show another.

## What I felt that is missing
Articles that shows some statics about it. I know that software engineering is important after I felt the need of my own and seeing how my performance improved after it; but the lack of meaningful way of approaching the issue of showing how much changed is troublesome. I've heard some of my professors calling it software engineering as a _"pseudo-science"_ and I cannot disagree in a way with them, how someone can clain improvements without the way to measure it?

The book itself has a great follow up list of books that are easy to find, I will check out some of them soon to help improve here.

## What I felt true
I've began to write tests a short time before reading the Clean Code, but it says that when write tests your code is improved overall because you improve the design, and that's true in my own experience. I didn't use TDD when I wrote my first test and I had to refactor a lot of code to ensure that the tests worked properly, but when I did that my think process changed a little bit and that's when after I've started doing TDD without even noticing; my code went for a high coupled functions to a more abstract even better named concepts and this improved a lot the time spent on those tasks.

From the Unix philosophy I found the Rule of Diversity: _"Distrust all claims for 'one true way'"_, a rule to be followed because the same project could have 'only one true way' to the approach that its designers decided so. The project follows the design not the other way around, so a good project means a good design; and that's why sometimes some people found themselves hating others works, because they followed another approach.

## Recommend reading
* [Basics of the Unix Philosophy](http://www.faqs.org/docs/artu/ch01s06.html)
