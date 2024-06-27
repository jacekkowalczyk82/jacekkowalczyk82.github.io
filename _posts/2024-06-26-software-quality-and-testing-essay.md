---
layout: post
title: Software Quality and Testing Essay
date: 2024-06-26 14:39 +0200
categories: update essay testing
tags: [java,software,quality,tests,testings]
---

# Essay about Software Quality and Testing 

Recently I noticed something that make me sad. I noticed that developers do not want to write tests. Maybe not all, maybe only some of them... but ....

## Quality 

I will start with some quotations of IT authorities. 

> Any fool can write code that a computer can understand. Good programmers write code that humans can understand. (Martin Fowler)

> Indeed, the ratio of time spent reading versus writing is well over 10 to 1. We are constantly reading old code as part of the effort to write new code. ...[Therefore,] making it easy to read makes it easier to write. (Robert C. Martin)

> Software engineering is what happens to programming when you add time and other programmers. (Russ Cox) 



## Rules and laws 

Every software engineer probably heard about the Good Chep Fast triangle -  You can pick only 2 of 3. 


![Good-Cheap-Fast](/assets/images/d4fa412bc99a5d8f571cce04a61fac83.png)(I do not remember where I found this image.)

I always say the we should always pick Good (in terms of Quality) and one of the others corners. 

I also believed that every person, software engineers, testers, product owners, project managers in every IT software company knows this relation of costs of fixing bugs during the Software Development Live Cycle. 

![cost-of-defects-in-SDLC](/assets/images/cost-of-defects-in-SDLC.png) (Picture from:  
https://www.functionize.com/blog/the-cost-of-finding-bugs-later-in-the-sdlc) 

Now I am not so sure about the last....

Another rule, that I want to mention is the 80/20 rule - Pareto Principle (https://en.wikipedia.org/wiki/Pareto_principle) . 

Some can say that they do not belive this kind of laws, like: Pareto rule, or Murphy's law (https://en.wikipedia.org/wiki/Murphy%27s_law). 
Some can say it is just a theory and not real law. 

I must say that all these years spent in IT endustry taught me that it is real. It happend to me very often that after implementing 80% of functionality or 80% of tasks that were planned for Scrum Sprint, I am finding out that the last 20% of work needs 5 times more time. All planning goes to trash. The same happens with planning work for implementing the main code and  adding tests for it. It happend for me also many times that I implementd the main code in few hours and to cover this code with tests (happy path plus some corner/edge cases) I needed few more days. 

Why I am saying about all these? Simply, we should take this into account when planning work related. We need to resever lots of time for development and more for testing, we need to reserve some time for simple things and more for complex. Otherwise we will deliver to Production on time but it will by buggy as hell. I would not like to maintains such production system. 

### Pareto Rule 80/20

* 80% of work is done in 20% of time 
* the rest 20% of work needs 80% of time to finish it. 

### Happy Path bs Edge cases 

* Happy Path cases (80% of work) we can cover in 20 % of time spend on writing tests.
* Edge Cases  (the rest 20% of work) needs 80% of time to test it. 

* This is Optimistic.... 
* In reality it can be 95 / 5. 


### Entropy, Chaos Theory, Murphy's law

* https://en.wikipedia.org/wiki/Chaos_theory

> Software entropy is the risk that changing existing software will result in unexpected problems, unmet objectives, or both. Although negligible when software is first created, software entropy grows with each development iteration.

> Anything that can go wrong will go wrong. 

## TDD

I need to say here also something about TDD. 
Test Driven Development (TDD) methodology was trying to solve the problem of keeping code in good quality by writing first tests and then fixing teh main code to make the code passing. Idea is very nice, but in real life, when  we maintain the big and legacy projects, it does not work. 
During my IT career I have seen only few times developers working with TDD. Most of developers I met do not know this or do not use it at all. 
I must say that, I did some TDD, but long time ago and only for new code and only with Unit testing. 

If TDD is not working in real life so what to do, how to bring more quality to code, and why it is important? 

## Make it testable

Developers think of optimizing the code..... Make it easy to write, Some may use good quality of Clean Code practices. Some just want to use fancy technologies. Some are focused only on writing it and running it from IDE, but never thinks about running it without IDE, console/terminal. Some does not think about running in the cloud, k8s at all. I meet also developers who were designing the software with production envo only in mind, how it should work in the final deployment .  

But barely nobody thinks about how to make the software testable before going to production. How to deploy it, how to divide to modules /units which can be easily tested. Very litle think, **How to make the testing process easy?** so in the result they are designing something that may work but it will be very difficult to tests with Unit Test, or any other kind of tests. 

Very little thinks that the software will not work without bugs from the first time, we will need to run it multiple times, bugs can be in different modules, different steps of the implemented process.
Each of these steps should be possible to mock to test others separately. 

### Testable code and code fragments only for easy testing

I like to make the software not only easy for testing but some times I want to add to the software things that are not required by product owners, not needed from te perspective of the production system. For example: We plan to use Oauth authentication for the developed application (tokens and lots of advanced authentication techniques), but before we integrate all these together, how we are going to test it? How to test it if the Authentication system is not ready? How to test various cases with invalid credentials? I like the idea of adding extra code to the application which will allow to use also the Basic Auth: username and password. This way we can create multiple test accounts, multiple correct and invalid credentials. 

The extra code cane be togled on/off with some configuration. It can be possible to deploy software to PROD without some modules that were designed only for testing. 

Architecture must also allow testing. If we design the application with big dependentancy to infrastructure, or data that are transfered to our system from external system and to test it we need to also rely on these external systems, then it will be very difficult to test it. 

Architecture, communications, data processing, usage workflow must support mocking of modules or systems. 


#### Example: LocalDate LocalTime LocalDateTime 

LocalDate, LocalTime, LocalDateTime clases can be used in short way :

```
LocalDate localDate = LocalDate.now();	
System.out.println(localDate);
//it will work but how to test code that relies on the real time?
```

Use methods with Clock: 

```
LocalDate localDateWithClock = LocalDate.now(Clock.systemDefaultZone());	
System.out.println(localDateWithClock);
localDateWithClock = LocalDate.now(Clock.system(ZoneId.of("Asia/Tokyo")));
System.out.println(localDateWithClock);
```

This way you can create instances of LocalDate in test that can use any Clock you want, it can be also the clock that is showing always the same date no matter what. 

Read more at: https://www.studytonight.com/java-examples/java-localdate-nowclock-method


**I must say about few techniques:**

* Composition over inheritance
* SOLID
* Mocks


### Composition over inheritance

* https://en.wikipedia.org/wiki/Composition_over_inheritance

> "To favor composition over inheritance is a design principle that gives the design higher flexibility. It is more natural to build business-domain classes out of various components than trying to find commonality between them and creating a family tree. " 

* https://medium.com/hprog99/composition-over-inheritance-a5f02a820eb0
* https://blogs.oracle.com/javamagazine/post/java-inheritance-composition
* https://www.digitalocean.com/community/tutorials/composition-vs-inheritance

### Plain Mocks with Polymorphysm

Before mockito library was invented there were techniques that allow to design the code in teh way that some pieces of it can be mocked. You can read more about this here: https://dev.to/drathi/how-to-mock-without-using-mockito-or-any-frameworks-1b5g 

The basic rule, I learned is to extract init /construction code to methods, so we can then overwrite them in the child classes. 
SOLID rules help to make code that is easy for mocking and for testing. 


### SOLID

Good developers should know, and the best of them should even use it daily. This very know principle of writing the Clean Code. 

* https://en.wikipedia.org/wiki/SOLID
* https://pl.wikipedia.org/wiki/SOLID


## Test Data

What about test data? All systems are working with some data. We should prepare a lot of test data, for all stage environments before PROD (DEV, TEST, PREPROD or what ever naming you are using). 

## Automated vs manual 

During the whole development process of the software we will need to repeat tests many times, do some regressions. It is good to have automated tests but ... 

It does not have to be always fully automated, It can be sometimes manual or semi automated testing. I know manual testing is not the best way but ...
again we need to remember the Pareto 80/20 when talking about costs of automation of tests. I preffer to automate what is easy to automate, or what can be mistake prone during manual tests. I also prefere to find some balance and **sometimes semi automated tests is the best choice**. 


Lazy dev doesn't want to write tests. I am lazy and for some small scripts or small utils I do not wrote automated tests but I do manual tests - Always. 
I repeat them always, I add some new code new functionality or I fix bug. 
Manual test can be in form of the readme file or run configuration in IDE.
I run it and check the output, logs, did the program do what ment to be done? Is it working as expected...

But for bigger commercial apps, testing is a must have.
I can understand that it can be hard to write tests for the legacy old application that no one want to touch...

But when starting new project that is going to be cloud based with popular technology stack like Java, Spring Boot on k8s, what is the excuse not to write tests? This technology stack provides a lot of tools for nice automated testing, for example: Mockito, Mock Server. 

## Make it work. Make it right. Code quality, clean code.

Many years ago, my collegue and manager tought me: "Make it work. Make it right." - First, I am focussing on making the software just to work, and then I am cleaning it, fixing, making better, more testable and deliver it with tests. 

It is important that we should not stop after "Make it work". There is extra work to do after that. 

We shoulld do some cleaning, refactoring. Do not say I will do it later later. 

**Define you DOD - Definition of Done - It is done when it is working right and it is well tested.** 

"I will do it later" is leading to deployment ot production without propper testing. I heard many times: lets do not write these tests right now as we will refactor the code and we will need to fix test again after refactoring. **How can you be sure that you rafactored code correcly?** 

You might test it manually. OK, but I think you aware that manual testing is very time consuming and error prone? 

I heard also many times: We are in hurry, the deadline is coming. We need to deliver it fast to production. We will write automated tests later after delivery. 

Guess what. There will be no time for housekeeping work and adding tests to production working code. There will be new features or bugs to solve. 

To deliver fast/accelerate use correcly the CICD processes. CICD includes testing for every new feature. In a loop. 

![www.abtasty.com-cicd.png](/assets/images/www.abtasty.com-cicd.png) (Picture from: https://www.abtasty.com/ci-cd/)


## Final thoughts 

**Testing is complex and very important process and we should never do any other activities at the expense of testing. To deliver Good Quality software we must Test.** 


## Books and resources not only about testing

* https://martinfowler.com/
* [Clean Code: A Handbook of Agile Software Craftsmanship By Robert C. Martin](https://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882)
* [The Art of Software Testing, 3rd Edition](https://www.amazon.com/Art-Software-Testing-Glenford-Myers/dp/1118031962)
* [Continuous Delivery: Reliable Software Releases through Build, Test, and Deployment Automation by David Farley, Jez Humble](https://www.amazon.com/Continuous-Delivery-Deployment-Automation-Addison-Wesley/dp/0321601912)
* [Pragmatic Software Testing: Becoming an Effective and Efficient Test Professional](https://www.amazon.com/Pragmatic-Software-Testing-Effective-Professional/dp/0470127902)
* [The Pragmatic Programmer: your journey to mastery, 20th Anniversary Edition, 2nd Edition](https://www.amazon.com/Pragmatic-Programmer-journey-mastery-Anniversary/dp/0135957052)
* [Site Reliability Engineering: How Google Runs Production Systems](https://www.amazon.com/Site-Reliability-Engineering-Production-Systems/dp/149192912X)
* [SRE Books](https://sre.google/books/)
* [The Phoenix Project](https://www.amazon.com/Phoenix-Project-DevOps-Helping-Business/dp/0988262592)
* [Accelerate](https://www.amazon.com/Accelerate-Software-Performing-Technology-Organizations/dp/1942788339/)

