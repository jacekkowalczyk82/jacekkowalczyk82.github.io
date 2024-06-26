---
layout: post
title: Software Quality and Testing Essay
date: 2024-06-26 14:39 +0200
categories: update essay testing
tags: [java,software,quality,tests,testings]
---

# Essay about Software Quality and Testing 

Recently I noticed  something that make me sad. I noticed that Developers do not want to write tests. Maybe not all, maybe only some of them... but ....


## Rules and laws 

Every software engineer probably heard about the Good Chep Fast triangle -  You can pick only 2 of 3. 

![Good-Cheap-Fast](/assets/images/d4fa412bc99a5d8f571cce04a61fac83.png)

I always say the we should always pick Good (in terms of Quality) and one of the others corners. 

I also believed that every person, software engineers, testers, product owners, project managers in every IT software company knows this relation of costs of fixing bugs during the Software Development Live Cycle. 

![cost-of-defects-in-SDLC](/assets/images/cost-of-defects-in-SDLC.png) (Picture  from page: 
https://www.functionize.com/blog/the-cost-of-finding-bugs-later-in-the-sdlc) 

Now I am not so sure about the last....

Another rule, that I want to mention is the 80/20 rule - Pareto Principle https://en.wikipedia.org/wiki/Pareto_principle . 

Some can say that they do not belive this kind of laws, like: Pareto rule, or Murphy's law (https://en.wikipedia.org/wiki/Murphy%27s_law). 
Some can say it is just a theory and not real law. 

I must say that all these years spent in IT endustry taught me that it is real. It happend to me very often that after implementing 80% of functionality or 80% of tasks that were planned for Scrum Sprint, I am finding out that the last 20% of work needs 5 times more time. All planning goes to trash. The same happens with planning work for implementing the main code and  adding tests for it. I t happend for me also many times that I implementd the main code in few hours and to cover this code with tests (happy path plus some corner/edge cases) I needed few more days. 

## TDD

I need to say here also something about TDD. 
Test Driven Development (TDD) methodology was trying to solve the problem of keeping code in good quality by writing first tests and then fixing teh main code to make the code passing. Idea is very nice, but in real life, when  we maintain the big and legacy projects, it does not work. 
During my IT career I have seen only few times developers working with TDD. Most of developers I met do not know this or do not use it at all. 
I must say that, I did some TDD, but long time ago and only for new code and only with Unit testing. 

If TDD is not working in real life so what to do, how to bring more quality to code, and why it is important? 

## SOLID - make it testable

* Composition over inheritance
* SOLID
* Mocks






## DRAFT notes


estable code and code fragments only for easy testing

Developer things of optimizing the code.....easy to write. Fancy technologies, how it should work... Some are focused only on writing it and running it from IDE, never thinks about running it without IDE. console terminal. Some does not think about running in the cloud, k8s

Some think about how it should work on production what it needs to do.....

But barely nobody thinks about how to make the software testable before Prod. How to deploy it, how to divide to modules /units which can be easily tested.

Very little thinks that the software will not work without bugs from the first time, we will need to run it multiple times, bugs can be in different modules, different steps of the implemented process.
Each of these steps should be possible to mock to test others separately


What about test data ,
Repeating tests after some part is implemented bug fixed

It does not have to be always fully automated code

It can be sometimes manual or semi automated test

Pareto. 80/20. Costs of automation






Make it work make it right. Code quality, clean code.

Lazy dev doesn't want to write tests. . I am lazy and for some small scripts or small utils I do not wrote automatwd tests but I do manual tests. Always. I repeat them always I add some new code new functionality or I fix bug. Manual test can be in form of the readme file or run configuration in IDE.
I run it and check the output, logs did program do what ment to be done? Is it working as expected,,.


But for bigger commercial apps, testing is a must have.
I can understand that it can be hard to write tests for the legacy old application that no one want to touch..,.

Bit when starting new project that is going to be cloud based with popular technology stack Java spring boot on k8s, what  is the excuse not to write tests?

Refactoring

I will do it Later

We. Would need to fix tests after refactoring

We are in hurry, the deadline is coming we need to deliver fast, after delivery you prod
.. guess what. There will be no time for housekeeping work and adding tests to production working code. There will be new features or bugs to solve

to deliver fast, accelerate is the CICD. CICD includes testing for every new feature. In a loop

Architecture must also allow testing, if we assume design the application with  big dependent idea to infrastructure, zaleNosci między modułami że dane przychodA tylko w jeden sposób i że nie są się podmienić modułu na nocka yo będzie ciężko to przetestować

Architecture communications, data processing, usage workflow must support mocking of modules systems. Infrastructure or data.



Books
Clean code
Clean architecture

Martin Fowler continuous delivery
Accelerate
Phenix project? Może nie bo to trochę inna tematyka a trochę SRE.








