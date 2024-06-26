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





