# FarmNotes
> Notes in the learning process of "clean code".

Reading about clean code promises and patterns, this notes are taken through this process. Beginning at the [Clean Code](https://www.amazon.com.br/Clean-Code-Handbook-Software-Craftsmanship-ebook/dp/B001GSTOAM?__mk_pt_BR=%C3%85M%C3%85%C5%BD%C3%95%C3%91&keywords=Clean+Code&qid=1525260282&sr=8-3&ref=sr_1_3) book and some of my own. The idea behind this project is to make an open book that anyone could copy, add and modify due your own needs; a collaborative way to improve software development through the learning process of making it easy for others to understand.

First advice is to have right by your side a Design Patterns by GoF to follow along some concepts; I bought mine used through a site called [Estante Virtual](https://www.estantevirtual.com.br/).

## The 5S
In 1951, the japanese Total Productive Maintenance(TPM) culture instaure the 5S:

* Seiri ("Sort"): knowing what and when;
* Seiton("Systematize"): everything has it's place;
* Seiso("Shine"): it must speak by itself;
* Siketsu("Standardization"): follow the rules;
* Shutsuke("Self-discipline"): reflect on one's work and be willing tho change.

## The overview
The act of design must be, by itself, as an small local act of repair. In the book is said that the simple act of code indentation could reduce considerably the number of bugs in a back-of-the-envelope discover at Bell Labs; but I didn't find anything about this that endorses this ideia.

Wanding is the act of "wonder around" a bad code in a way that repels you of making anything. Probably because who wrote the code followed the [LeBlanc's Law](https://en.wikipedia.org/wiki/Talk%3AList_of_eponymous_laws#Proposal_to_add_LeBlanc's_law): "later equals never".

## The Art of Clean Code?
Programming is a kind of art: the artists want make something beautiful and new, even if is not that new for the whole world or actually all the beautiful... But is new and beautiful to them. And that's why a team stuck with a bad code loses it's productivity also, because no one is creating something.

Being able to spot a bad code doesn't mean that you know how to fix or even re-factoring making it a better one. The one who seeks the best isn't always the one who finds it.

Coding is the final tool, anyone can measure anything through it: efficiency, manutenability, readability, "monolitch"(bility), even the worstability! And that means that, someone behind the keyboard who wrote it, can be measure also; the funny thing is that is "easy" for a code to be good at something at some point and bad at all things all the way, this feeling of "at least one" that can make some programmers ego goes up and become lazy to improve. Nonetheless to say that those ugly things that make the code bad could make it not work at all after some time.

MacBook's dictionary definition of crisp: "briskly decisive and matter-of-fact, without hesitation or unnecessary detail."... That being said, a good code should be at least a crisp one.

One definition of clean code that I particurally liked a lot is that a clean code makes it easy for othewr people to enhance it, and that's is linked to "Big" Dave Thomas, founder of OTI. I do really like when someone do a code review of something that I've wrote, but if there's nothing add to it the empty feels fulls me up -- no pun intended hahahah

![xkcd](https://imgs.xkcd.com/comics/automation.png)

## Naming variables

A good abbreviation could be a disinformative one also;

Do not use structre names on variables like queue or list, even if they do represent a variable that is one of them could you future-proof this?

Names like a, an, the, info, new and data should be avoided;

Use searchable names;

Methods should have a verb or a verb pharse names;

Pick only one, don't use fetch, retrive or get through out the code;

Add a meaningful context -- that remminds me, in a way, One level of indentation per method from [Object Calisthenics](https://gist.github.com/suissa/79aa860161b13e50e5fa3a0120fb6d68);

Don't add more context to a name more than necessary;

## Functions

"The first rule of functions is that they should be small. The scond rule of fucntions is that they should be smaller.";

This is more old than my grandma, but:

    "Functions hould do one thing. They should do it well. They should do it only.".

"The smaller and more focused a function is, the easier it is to choose a descriptive name.";

This one is a little bit tricky, for me especially:

    "The ideal number of arguments for a function is zero (niladic). Next comes one (monadic), followed closely by two (dyadic). Theree arguments (triadic) should be avoided where possible. More than three (polyadic) requires a very special justification -- and then shouldn't be used anyway."

    Creating objects to agregate variables isn't cheating!

"Functions should either do something or answer something, but not both";

Give it a try to try/catch blocks;

Functions that handles errors, ONLY handles erros;

## Don't Repeat Yourself(DRY)

In the book this part is one of the functions parts but I think it's worth it to add more to it later on.

"Duplication may be the root of all evil in software" -- To a given extend, I couldn't agree more.

"Every time you see duplication in the code, it represents a missed opportunity for abstraction."

The funny thing about absctration is that they might be irrelevant when you are doing some classwork or something like it but try to go a step even further, when you don't always know all of the code, to see that absctration helps you write code when you are using something wrote by others. A simple example is to see that you know that a print function expects variables and sometimes a mask, but do you know how they are processed and shown in your console? Anyway you expected to work properly because the absctraction point is in a level that you don't have to care with lesser important matter of it.
Comments

Comments are last resource tools, if you need a comment, stop, rethink it and than try it to refactor the code, even then if you fail to do so, and only then, write a code to better explain yourself.

TODO comments could be a nice remminder to pick up the things were we were left off.
Formatting

Lost this notes due internet connection errors.
Error Handling

"Error handling is important, but if it obscures logic, IT'S WRONG".

    Use exceptions rather than return codes — that means if the language supports try, catch and finally statements you should probably being using it;

    I didn't know that checked exceptions is an Open/Closed Principle violation.

## Boundaries
When using third-parties packages before anything else, write some codes for it; this will ensure that they work the way is expected to and, after bound to the system, the time that otherwise you would spend writing new test for it would be considerably reduced. Tests are a great way to understand the work of others.
Artificial coupling

Is joinning two or more modules that serves no direct purpose in a temporarily convenient location.
Three Laws of TDD

    You may not write production code until you have written a failing unit test;

    You may not write more of a unit test than is sufficient to fail, and not compiling is failing;

    You may not write more production code than is sufficient to pass the currently failing test.

See more at this link.

## F.I.R.S.T.
Rules for a clean testing:

    Fast: a slow test results in a slow fix it, letting the code to rot;

    Independent: when one test de depend on another one, the first one to fail causes a cascade of failures, making it hard to diagnosis;

    Repeatable: if the only work in one specifc machine would they really be testing all kind of enverionment? No! Tests should run in any machine because te real code will run too;

    Self-validating: either they pass or fail;

    Timely: tests comes before the coding.

## Here We Go
![xkcd](https://imgs.xkcd.com/comics/standards.png)

The Single Responsibility Principle (SRP)

"You should have one responsibility -- one reason to change."
Cohesion

A method should manipulate one or more variables; the more manipulates the more cohesive it's, which is not advisable to do it because a high co-dependency increasing logical as a whole.
Open-Closed Principle (OCP)

"Classes should be open for extension but closed for modification."
Dependency Inversion Principle (DIP)

"Classes shoul depend upon absctractions, not on concrete details."
Systems

Clean code is a mean to a way of management of low level abstractions, higher ones are managed through the system level.

It's better to read the book on this one.
Emergence

Kent Beck's four rules of Simple Design:

    Runs all the tests -- if you cannot test, you cannot ensure that it works properly -- even testing this is a bold statement to do it, so be cautious about it;

    Contains no duplicaton;

    Expresses the intent of the programmer -- using the pattern aplied as name for a method is a good design;

    Minimizes the number of classes and methods.

## Concurrency
Concurrency is about breaking the what gets done from when gets done -- single-thread couple those concpets.

Concurrency is an extensive subject, reading the Wikipedia page about it before proceding is adivised. It's a short reading. And other concepts also:

    ​[Producer-Consumer](https://en.wikipedia.org/wiki/Producer%E2%80%93consumer_problem);

    ​[Readers-Writers](https://en.wikipedia.org/wiki/Readers%E2%80%93writers_problem);

    [​Dining Philosophers](https://en.wikipedia.org/wiki/Dining_philosophers_problem).

Concurrency problems are not so easy to solve, especially when some of the threads are running in the client-side because the system itself looses some of the control compared to those running on the server-side.

About testing concurrent code, it's better to read the book since would take the same amout of words to describe it here. And besides that, reading the Apendex about concurrency it's like reading another different book by itself, more worth it then I've expected.
Successive Refinement

Instead of saying that a perfect code doesn't exists, answer the following questions:

    Is there a language that never has updates that brokes/deprecates previous code or patch something?

    You always know everthing that has to be known?

    A program always control everthing that has to be controled on the environment on which is running?

Then how a "perfect" code should exists in this world?

A good code is good as long the one who wrote it and always will be something to improving since we are improving all the time, change languages and bringing some concepts from others backgrounds, seeing the code made it by others. Code is like wine, it's gets better with time.

"Refactoring is a lot like solving a Rubik's cube. There are lots of little stpes required to achieve a large goal. Each step enables the next."

One thing to keep in mind when refining code is [The Principle of Least Astonishment](https://en.wikipedia.org/wiki/Principle_of_least_astonishment).
Logic
If or while statements

A:Plain Text 

if (isPayDay(date))

Is better than:

if ("Monday" == date.dayOfWeek && "First" == date.weekOfMonth)

And, besides that, avoid negatives conditionals.
Comparison

When comparing something, a good practice is to put the value first. So, instead of doing:

if (answerToAllQuestions == 42)

Try it doing:

if (42 == answerToAllQuestions)

 That's because if you mis-type and forget to put a equal from a comparison it will become an atribution:

if (answerToAllQuestions = 42)

Which many compilers won't catch as an error or even a warning since comparisons like the following are allowed but are not a clean way to read a code:

if ((myPointer = malloc(sizeof(int) * 42)) != NULL)

## Variables

If you had to declare a variable in the middle of the code, probably this part of the code should be in another function.
Abstractions

Remember that what is different than how:

def printScoreboard (Team A, Team B)
    puts "Time: " Time
    puts "Home: " A.name " Shots on goals" A.goals
    puts "Half: " Match.half
    puts "Visitors: " B.name " Shots on goals"  B.goals
end

printScoreboard should not know how to the data is parsed but only know that needs to call it the functions that print them:

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

This sounds more difficult than appears? Because it is!
Avoid Transitive Navigation

JavaScript programmers are going to hate this but, asside from Promises, why keeping navigation through a variable that anyone who reads the code besides you are going to think that as "what the heck is going on here?" aka [train wreck](http://www.thinkcode.se/blog/2011/12/30/how-many-train-wrecks-are-lurking-in-your-code).

const meaningOfLife = World.getHumans().getPerson("John Doe").getTastes().sort()[0]

Should be:

const humans = World.getHumans()
const you = humans.getPerson("John Doe")
const tastes = you.getTastes()
const meaningOfLife = tastes.sort()[0]

## Code review
When doubting about your code, find someone to read it without you having to explaing it; listen to this person feeedback a take some lessons from it. This might help you improve you current project.

Having to always look at the same code and expect to find something new to improve is kind like to throw a dice that always shows the same side expecting to show another.
What I felt that is missing

Articles that shows some statitiscs about it. I know that software engineering is imporant after I felt the need of my own and seeing how my performance improved after it; but the lack of meanfull way of aproaching the issue of showing how much changed has changed is troublesome. I've heard some of my professors calling it sotware engineering as a "pseudo-science" and I cannot disagree in a way with them, how someone can clain improvements without the way to measure it?

The book itself has a great follow up list of books that are easy to find, I will check out some of them soon to help improve here.

## What I felt true
I've began to write tests a short time before reading the Clean Code, but it says that when write tests your code is improved overall because you improve the design, and that's true in my own experience. I didn't use TDD when I wrote my first test and I had to re-factor a lot of code to ensure that the tests worked properly, but when I did that my think process changed a little bit and that's when after I've started doing TDD without even noticing; my code went for a high coupled functions to a more absctract even better named concepts and this improved a lot the time spent on thoses tasks.
