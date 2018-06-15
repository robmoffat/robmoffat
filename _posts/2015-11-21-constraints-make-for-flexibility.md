---
id: 257
title: Constraints Make For Flexibility
date: 2015-11-21T01:11:10+00:00
author: bobm
layout: post
guid: http://robmoff.at/2015/11/21/constraints-make-for-flexibility/
permalink: /2015/11/21/constraints-make-for-flexibility/
categories:
  - Uncategorized
---
Antione de Saint-Exupery said:

_Perfection is reached not when there is nothing more to add, but when there is nothing more to take away._

Which I think, is one of my favourite quotes of all time.  It _resonates_ on a deep level.  And, it’s extremely relevant to computer science, where we talk about YAGNI (You Aren’t Going To Need It) and Refactoring Mercilessly.  It’s also appropriate to the startup community, who talk about building their _Minimum Viable Products_.   That’s all true. 

Of course you shouldn’t build stuff you don’t need.  It’s waste.  And, waste lying round everywhere just makes everyone’s life harder.  Get rid of it.

But, those things don’t even capture it.  This is also about curation.

Sometimes, by limiting functionality, we end up with _more.  _Not just, the same, but actually more.

For example.  Pure4J disallows you from doing certain things with code. And, it enforces those rules pretty rigorously.  By _limiting what you can do_, suddenly, a whole new load of things open up.   Problems that you had before just disappear. 

Here’s another example that I’ve spoken about before:  Creating free-text fields in Jira.  By putting these in, you actually _reduce_ the functionality of the software, because now there are plenty of ways in which information may or may not be stored in the system, and no one can rely on it being there.  By having a fixed, mandatory choice of four options (creating a _constraint)_ you give people something they can use to _categorize_ and search against.  But, with an optional free-text field, it seems like you’ve given them more, but actually, you’ve given them less.  It’s next to useless for any kind of searching or categorizing and may as well not be there.

A third option:  Rich-Hickey’s Datomic database.  It’s basically a layer over _a regular database.  _And, it prevents you from changing stuff.  So, you can only add things to the database.  _How the hell is that better?_
  
__
  
It sounds like it should be a disaster.

But, it isn’t.

By doing this, you can pass around _copies_ of the database.  You can test in production.   You avoid a whole host of locking and atomicity problems that you had before.  And what have you really lost?   Actually, nothing you couldn’t do without.

So:  disallowing certain behaviours makes a system _more flexible.  _Don’t give users more than one way to do anything.  Just give them the one, _right_ way.  

Can anyone think of other examples of this pattern in action?