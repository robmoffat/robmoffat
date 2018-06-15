---
id: 261
title: All About Eve
date: 2016-01-13T11:00:39+00:00
author: bobm
layout: post
guid: http://robmoff.at/2016/01/13/all-about-eve/
permalink: /2016/01/13/all-about-eve/
categories:
  - Uncategorized
---
**Some Background:**
  
****
  
[Eve](https://github.com/witheve/Eve) is a new programming language.  Maybe.  Or, a development environment.  More accurately, perhaps, it’s a tool to think.  If you have an hour to spare, this is a great video to watch from Chris Granger:



If you don’t then I’ll summarise (badly).  The video starts with the question _“What will programming look like in 10 years?”.  _Chris started off his career with Microsoft working on Visual Studio, but then, faced with the complexity of this product, wanted to build an IDE which stripped back a lot of the complexity, and [Light Table](http://lighttable.com) was born (for editing Clojure / Clojurescript).  Light Table aims to minimise or eliminate the cycle between _writing code_ and _seeing results_.

The lesson from this was apparently, that just fixing the IDE wasn’t enough.  Programming itself suffers from the problem that it is _indirect and invisible_, beleaguered with _accidental complexity_ and _unobservable.  _
  
__
  
Paraphrasing heavily (really, watch the video), Eve started as a collection of experiments into how computing could be made better.    They extensively reviewed the existing literature and state-of-the-art, deciding that the closest we have come to really solving those issues of programming are in tools like _Excel_ and _SQL_ (i.e. relational databases).

Along the way, they throw out GUI editors, query visualisations and more traditional text based languages.  Chris then demonstrates version 0 of Eve, which is kind of a Wiki, combined with a query language, and kind of a database.  Everything updates instantly on screen.  There’s huge promise, and I am tempted to _get involved in a big, open-source way_.

**Lotus Notes**
  
****
  
My first thought on watching the demo was _This seems a lot like Lotus Notes._  And indeed, Wikis and Notes share a lot of common thinking:  unstructured data, functions for manipulating values, views on data etc.

I can imagine that not many people working in IT today are familiar with Notes, but take it from me: this is _a complement.  _  Notes was an amazing (and amazingly productive) environment to work in.   You could realistically build multi-user applications with workflow, email, reporting, _everything.  _The security was top-notch.  Lotus Notes came with an Email application, which was built in Lotus Notes, and during the 90’s millions of people used Lotus Notes for Email:  the point being, you could build amazing things in it.

So resurrecting a lot of the ideas of Lotus Notes now _makes a lot of sense to me._  We don’t have anything similar to this now, and that’s a shame.  There’s a middle ground (somewhere between building simulations in Excel, and building full applications in Java) which is served badly since we don’t have Notes anymore.

So, good on them.  This seems like a really cool product with a bright future.

But.

**I Don’t Think This Is What Programming Will Look Like In 10 Years**

If Lotus Notes was so cool, why aren’t we using it today?  Also, if programming in Excel is so awesome, why am I not developing banking software using it?

The problem is, (I think) _tradeoffs.  _And there are three I want to talk about:
  
__
  
**1.  Openness and Accidental Complexity**

When you have a closed system (like Eve, or WordPress, or Lotus Notes, or MySQL, or Excel) you can really put a lid on Accidental Complexity.  Accidental Complexity is things like:  in system A, I have a column called “Name”, but in system B, I have “First Name” and “Last Name”.  Or, here I have dates formatted in the American way, but the file I am importing has them in the European way.  Or, I have an event-driven system which triggers every time there is a new order, but my finance system requires a daily feed… those kind of things.

When you program in a _general purpose language_ like Java, or C++ or whatever, you can deal with accidental complexity, because these languages are like _glue_: they can join together disparate libraries, or databases, or applications, or feeds, or queues or whatever.  They are “Open”:  they accept that the world at large doesn’t play to any particular rules, and that they need to adapt to the world.

“Closed” systems, on the other hand, _force the world to play to their rules._  So, when I write a plugin for Eclipse, Excel, Minecraft, WordPress or whatever, I have to obey the rules.  That’s fine.  But, a lot of systems that we use every day are out there, not playing to the rules.  Certainly, there are _no_ pre-existing systems playing to Eve’s rules, because Eve’s only just been thought of.

But, can this problem be solved by building “plugins” for Eve?  So that we can get it to talk to existing relational databases, or filesystems, or whatever.  Well yes and no.   Lotus Notes had this challenge already, back in the day.  People wanted it to talk with SQL databases.  Work was done so that data could be synchronised, and maybe that solved a lot of people’s problems.  But inevitably, with this, you _imported the accidental complexity from those systems:_  table structures, date formats, edit cycles, transactions etc._ _
  
__
  
So, it feels to me that this is a fundamental issue:  _can we build open systems without importing accidental complexity?  _Because, if we can’t, then a lot of programming in the future can’t be done in an “Eve” way.

But, maybe that’s ok.

**2.  Organisation vs Approachability**

In Chris’ video, he talks about how in an early version of Eve, users were bedevilled by _scope._  They wanted to use data in functions, but were constrained by not having the data in scope.  He observed that neither Excel or relational databases had this issue, and so, the Wiki-style Eve takes a leaf out of that book and jettisons the concept of scope.

But, scope is a useful thing that was deliberately added to programming languages to reduce errors.  Global state is rightly vilified as being a source of errors in software:  as soon as you scale your software endeavour, you run the risk of confusing pieces of global state.

If you look at many of the features of Java (say):

  * Separation Of Concerns
  * Packages / Namespace / Scoping / Jars
  * Interfaces
  * Abstract Classes / Type Hierarchy
  * Versioning
  * Methods / Procedures / Functional Decomposition
  * Compilation / Compile-time checking

These are all features to improve the _organisation_ of the software, reduce _duplication_ and enforce consistency through _once-and-only-once.  _ Yes, you can build a much more _approachable, easy to learn, less indirect _language with none of these, but as the scope of your software problem gets larger, the bigger issue is organisation, not approachability.  So, we trade this off.

This is one of the big failings of Lotus Notes:  versioning the software was hard.  Upgrading databases was hard.  _Knowing what code was even in the application_ was hard.  Testing was all manual.  Re-use was minimal.  Revision control (a la git) was impossible.   When you changed something in one place, you had no idea whether this had introduced a problem somewhere else.

And now, it’s actually worse than this.  Right now, I feel that _Java (et al) fail us:  _It’s still really hard to do releases, and test that software is correct, and ensure that changing a part of the system I’m building is going to have no consequences on other parts of the system.

My client has a vast network of interrelated computer systems, on different release cycles, on different hardware, with different programming languages.. how do we know this all works together?

Yes, pure functional programming would help.  Yes, better testing would help.  Maybe Docker, or Chef could help.

But, right now it’s a mess, and in 10 years time it will be an even bigger mess.   Java allows us to organise at the scale of _one application.  _But we need tools to help us organise our software at a scale of _many applications.  _Because, software is eating the world, right?

**3.  Focus vs Coverage**
  
__
  
Lotus Notes came along when the Internet was in it’s formative years.  So, when you started as a Notes developer, you got given a printed manual or two.  This was great:  everything you needed to know was _in the manual.  _And, you could be massively productive and run rings around the guys building C++ applications with RDBMS back-ends.  Cool.

What eventually went wrong (I think) was that, as web pages took off, people wanted their Notes databases on the web, and Lotus/IBM then bolted on loads of stuff to make Notes databases web-browseable.  But, it was hard to use and fiddly, and required learning HTML, and the whole conceptual integrity of the Lotus Notes model was lost (see issue 1 again).

The problem is:  one size doesn’t fit everyone.  Also, you can’t hope to keep up with everything.  Software systems _at best_ can hope to serve one niche of people.

It’s the same reason why we don’t _just_ build applications solely in SQL Databases:  at some point in time, companies like Oracle tried to build products where you could build the _entire application_ inside the database, and it would have forms, and web pages and everything.  But, this didn’t work out either:  even ignoring vendor lock-in, it’s better to be able to mix-and-match your technology choices to fit to the problem you have:  trying to be _all things to all people_ is just a non-starter.

This is why Lotus Notes couldn’t keep up: it was too busy trying to do everything, rather than _one thing well._

**Unfair**

And, maybe this is unfair.  What Chris and the Eve team have done is looking amazing.  I don’t think Chris really meant for Eve to be “what programming looked like in 10 years”.  Really, what he was saying  is “we need to start doing more experiments about what programming is, and what it should be, like we did for Eve.”

Eve takes a stance on the three trade-offs above, and it’s pretty much the same stance Notes took:  I loved Notes, and I’d like to see a modern version.   Preferably one which solves things like versioning and so on.

But, the design of “programming in 10 years” needs to acknowledge these trade-offs, and then design _beyond_ them:  truly innovative design should reframe trade-offs in ways which completely change the landscape.  We’re only going to move beyond the current status quo with some amazing design, more experiments, more ideas and throwing away what doesn’t work.

**Chris’ Comments**
  
****
  
Chris Granger took the time to discuss some of these points with me, on Github:

<https://gist.github.com/ibdknox/2b185fcb8e5d1de68796>

**Update #2**

This was discussed further on Hacker News [here](https://news.ycombinator.com/item?id=10995235).