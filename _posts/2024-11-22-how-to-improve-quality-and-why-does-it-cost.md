---
layout: post
title: How to improve quality and why does it cost
date: 2024-11-22 13:37 +0100
---

In my previous article I was mentioning two important laws/rules that are ruling the IT world:
* [Pareto principle](https://en.wikipedia.org/wiki/Pareto_principle)
* Good Cheap Fast triangle - Iron triangle [Fast, Good or Cheap: How to Achieve the Iron Triangle](https://www.business.com/articles/fast-good-cheap-pick-three/)

More links about the Iron triangle:
* [Project management triangle - Wikipedia](https://en.wikipedia.org/wiki/Project_management_triangle)
* [Common law of business balance - Wikipedia](https://en.wikipedia.org/wiki/Common_law_of_business_balance)

## Iron Triangle and Pareto Principle 

In this article I would like to refer to these principles as well. Lets start with **Iron Triangle - Good, Cheap, Fast. Pick two** first. 

IMHO When we plan any Software Development work, we develop applications and we think about quality we should pay attention these two rules: Pareto and Iron Triangle. 

Managers who count money probably will choose Cheap corner but not me. I like the good quality software and IMHO all companies that want to stay on the market should also select GOOD. 
When we select the Good corner as the most important element then we need to make decision between Cheap or Fast. 

**Cheap** -  we work with the same resources and do not introduce any new tools, people to the team, anything that can increase the cost. 

**Fast** - We want to deliver very fast. There defined deadlines. Customers are informed about new software of features and they expected to have it on time. There two variants of this: 
* **Fast and expensive** - we want to delivery very fast and we hire the best people on the market with great experience to have the ready product on time and with good quality. 
* **Fast and cheap** - we are delivering fast without extra costs. We are using the same team and same toolbox without investments. 

Maybe I simplify it too much but I think most will understand what I am talking about. 

From what I noticed during my IT work, the management of companies, projects very often prefers **Cheap and Fast corners**, which is **the worst choice ever**. 

But lets imagine management already choose **Good** so what else it will be selected? I think in most cases it will be **Cheap**. 

**Fast** is the least possible selection. 

Following these selections **Good and Cheap** the common result effect is **slow**. 
I think we need to face it . Delivering **Good and Cheap** software will be slow. **Quality takes time**, if we want to deliver good quality it  will take time, it will be slow. 

I heard lots of complains and excuse that we did not write, fix tests because it was time consuming and we needed to deliver something ASAP. Teams were pushed to the limits of their performance to deliver the product, but it was done on cost of the quality , they did not find  tie for doing tests. And here we need to say few words about **Pareto Principle 80/20**. There are multiple variants of this rule. 

I like this variant: if 80%  of work we did X time, then the remaining 20% of work will be done in Y time, and Y is 4 times X ( Y= 2*X, X is 20% of time, and Y is 80% of time). 
80% of work is done in 20% of real time needed for the given work, and 20% of work requires 80% of needed time. This rule means that teams very often underestimate the work to only this 20%time, for example they say they will deliver product/feature in 1 Scrum sprint. If they estimate "correctly" they will make it  but without tests, and they will probably need 4 extra sprints for testing. designing, implementing tests for this product. 
It might sound not realistic, but I can say it from my experience that it is true. Very often writing tests for my code that I wrote in 1 day, took me extra 4 or 5 days. Tests are more time consuming than the main code. Another example of Pareto rule in testing is that 20% of time we spend on writing the happy path scenarios, and to cover the Edge/Corner cases we need 80% of time. 
**Quality takes time**. 

The most known interpretation of Pareto Principle is that we achieve 80% of needed results we can get by doing well only 20% of tasks. Other tasks are less important and they bring less , only 20% of value. 
Some can say that the main code is more important as it is the thing that brings value ( 80% ), this is what the customer pays for, and 20% of of this value are tests...  and this also brings us to the same conclusion: we do main code (80% of value) in 20% of time, and test code (20% of value) in ... 80% of time... 

I think it is very clear what I want to say. 

The same logic we can apply to manual vs automatic testing. Writing automated tests takes time and it it is expensive  but I think it is obvious that automated tests can speed up the testing process, especially regression testing. I know automation of tests is expensive, and in some cases we need to consider if the value of automated tests is so big to explain also the big cost of writing automated tests. We should always consider what is most important for us and it is not one time decision, we need to make this decision for every single feature of the product. Cost of writing the automated test for back-end components is smaller probably that for the UI. There is no single golden answer for this question, but I think also that **we must always do testing**. Will it be manual or automated, it is a second choice, but always do tests. 

Many years ago my line manager (greetings for Krzysztof :-) ) taught me the approach **"Make it work. Make it right."** I really like it and use it. In this approach we start with some working solution, we can even call it prototype, POC, concept but after it is working  we **must** remember to make it **right**, do all refactors, code cleaning, make the final solution and also test it properly. Pareto principle is also applied here. The working solution (80% of work in 20 % of time), The correct right solution (20% of work in 80% of time). 
It is always true. 

If we ignore the "make it right" part we can get into real troubles, technical debt and risk of serious failures on production. 

There are many more extensions of this rules, and all these are kind or rules like [Murphy's law](https://en.wikipedia.org/wiki/Murphy's_law) that you cannot prove and also you can't refute. 

**To summarise**

Quality Assurance takes lot of time. Excuses like: I did not implement test because this needs time, or I needed to do more important task, does not make sense. We must face it: Quality Assurance is time consuming. That is it. Period. 

## Long term effect of investing time for QA

I think it should be obvious that investing into QA we gain more time for the production maintenance, If there is less bugs we have less fixes to do. We should always remember that the cost of fixing bugs  is growing with time, on production is much higher then on every previous stage of software life cycle. Also having already good set of automated tests it is very cheap to do regression testing after introducing new features for new version. 

## Techniques to improve Quality 

### DevOps

In my opinion it is the most balanced methodology when we think about development, testing,  delivering and maintenance of the software.  

One team is responsible for all stages of software life cycles.  The DevOps team cares a lot about the quality as this team is also responsible for **call duty**. They do not want to be woken up in the middle of the night.  

### PR - pull requests

Pull request also takes lots of time for person that is doing the code review, but how can we approve code changes without checking them. 

### Pair programming

I think Pair programming can be sometimes even more effective than PR, code review as the other person is more up to date with the solution designed and implemented, so the seconds person needs less time for checking and approving PR.  

If we implement pair programming t our team it does not mean we need to always do pair programming for all tasks. We can use it for only more complex topics or only when less experienced developer is doing the task. He also needs to learn and the pair programming is great technique for learning. On short term we invest lots of time as two persons are working on the task instead of one, but in the long term we gain better quality and we do not wast time for fixes later. 

### Tests

We should always do tests. We can do them manually or we can automate them. Not all tests should be automated. We should consider always pros and cons of automation. Some manuals tests will be extremely expensive to automate, but automated test is the goal for which we should aim. Automated tests are the cheapest in execution. We need to invest time to write them and maintain  but later it is very cheap to do regression testing. 

## And finally 


> Nauczyłam się, że droga postępu nie jest ani szybka, ani łatwa.
> I was taught that the way of progress is neither swift nor easy.

* Maria Skłodowska-Curie



