---
id: 223
title: 'Ramp Up To The Point Of “Impossible&#8221;'
date: 2015-10-09T11:09:30+00:00
author: bobm
layout: post
guid: http://robmoff.at/2015/10/09/ramp-up-to-the-point-of-impossible/
permalink: /2015/10/09/ramp-up-to-the-point-of-impossible/
categories:
  - management
tags:
  - blog
---
_A corollary to “Work expands to fill the time available”. _
  
__
  
**Note:** <font face="Courier New"> This entry is not meant to be representative of a single institution.  It’s the result of broad experience and discussions with a number of colleagues working in a number of different Tier One Investment Banks</font>.

The risk department is a heady mix of several competing constraints, which, when taken together, become toxic:

  1. **We don’t want to break anything.  **We have to keep the “show on the road” at all times, produce our numbers every day, and not upset the business by producing a set of risk numbers that is significantly worse than it was the day before.
  2. **We have a growing regulatory burden.  **Which means that all the time we are trying to introduce new reports, new metrics and more granularity about what we are doing.  One of the upshots of this is that there is a lot of _money_ for risk.
  3. **The landscape is too complex.  **No one really has a complete understanding of all of the systems in play.  Additionally, systems don’t have sets of automated acceptance tests, so it’s impossible to say for sure what the systems do, or what they are supposed to do.

So, why do these elements, taken together, conspire to create a problem?

**How It Once Was**

You need to start with the understanding that, ten years ago, risk departments were, relatively speaking, _poorly funded._  And were not the centre of scrutiny within banks that they now are.  They would be composed of a small set of IT staff who were constantly trading off the complexity of a solution against timeliness against benefit.  

The systems that were produced were somewhat _ad hoc,_ changes were made frequently (perhaps daily) and things got broken.  But the teams responsible were right there, on the ground, with a full understanding and could fix them at the drop of a hat.

The business acted as the testing department, and, as changes were made, wild swings in the risk numbers would warrant urgent ‘phone calls to get it fixed, at any time of the day or night.  

Was this an ideal situation?  No.  This was in the days before continuous integration and automated testing were really the big noise they are now.  But the _tight feedback loop_ made up for this lack to some extent.

**What Changed**

Then, the Basel regulations happened.  And then the credit crunch.  And suddenly, what had previously been an internal function of the banks now became both really externally important and also a hot news topic at the same time.  

It was time to lose the “backroom boffins” image and modernise Risk departments.

Budgets increased, and staff numbers ramped up accordingly.  Entire off-shore teams appeared to help support the existing applications.   And inevitably, the shortcomings of those existing applications became apparent.

As staff numbers went up, three things happened.    The first was, that the people who had been _doing_ in the first place moved on to start _teaching_ and _managing_ new doers.  Some of the guys didn’t like this, and  left to go to other banks.  But, the story was the same there too, because the regulations had changed for everyone.  Coupled with the rise in new staff, this meant that _on average_ the amount of experience in these systems had decreased, per capita.  

This led onto the second thing happening.  Less experienced staff (and more staff generally) meant that there were more problematic changes.  More things got broken than before.   The ad-hoc feedback loops and systems were no longer good enough to ensure the stability of the systems, so the level of _control_ had to go up:  banks instigated complex release management procedures, access control regimes and sign-offs to prevent accidental mistakes.   They actually had to do this anyway, because of the tighter auditing and regulatory regimes around them.  But this meant that the feedback loops lengthened considerably between someone wanting a change, and the making of that change.  

The third thing that happened following the increased budgets is that the risk staff realised:  now is the chance we have to finally _build the systems we always wanted to build.  _So they started to build these systems.  But, it wouldn’t be that easy.

**Building New Systems**

For these staff, experienced in the old ways of keeping production systems running, the obvious thing to do would be to build _new_ systems.   By doing this, you don’t break what you already have:  and that’s one of the major lessons they had learnt being in the risk department already.   Yes, make fixes, change stuff, but try your best not to break the application and get woken up at 4AM to fix it.

Lots of the old, (now legacy) systems were based around databases and stored procedures.  Possibly calling off to some C, C++ or sometimes, Java libraries.   The new world would be Coherence, NoSQL and (latterly) Hadoop (insert buzzwords here).

Getting funding for new projects based on exciting architectures was _easy:_ the budgets were already available to them because of the increased regulatory attention.  What was going to be much harder would be specifying these systems.  Partly this would be because of the lower level of knowledge-per-capita, and partly because so much of the logic and intent of the original systems has been lost over time and wasn’t properly documented in the first place.

**In A Hole**

So the hole looks like this:  legacy systems are very hard to maintain, and contain hidden, intrinsic knowledge.  New systems are hard to specify, because you either have to avoid stepping on the toes of the legacy systems, or you have to outright replace them, but then you are back trying to understand what the legacy system does.

All the while, you have a huge IT department, trying to implement useful change, wanting to deliver software and wanting to further their careers and improve their CVs. The upshot of this is that lots of “window dressing” projects end up being created:  These are characterized by having lofty ambitions and are long on strategic intent.  This makes them easy to slip by the budget holders, as you sell them on the bright future, but hard to implement in practice.  If not impossible.  

Imagine this going on for several years, so that all the easy, "low-hanging fruit” software has been written. Probably quite badly.  You end up with software projects in development for years, without delivering anything.  The wool being pulled over the eyes of management:  releases that occur but deliver _nothing_ of value (apart from ensuring someone’s bonus).  Testing cycles that go on _forever._
  
__
  
**Work expands to fill the time available**
  
__
  
And, sometimes, work expands to fill the money available.  The money available may not have any relationship to either the _perceived value_ that the project will bring, or even the _delivered value_ of the project.  In the latter case, sometimes not delivering the project will be of greater value than delivering it.

**Diagnosis**

I _want_ to conclude that what’s needed is more emphasis on automated acceptance testing.  If we had this across the business, we would be able to see:

  * What the software is supposed to do (the test cases give examples of use)
  * Whether or not it actually does this (the results of running the tests)

I _would also like to_ conclude that our problems are partly due to the _invisible_ nature of the software we’ve created:

  * No one is able to walk up to a running risk system and say, for definite, by looking at it, what inputs it needs and from where, what systems it reports into, and where, and how often.  
  * No one is able to reason about what would happen if we _changed_ part of the system.
  * Testing burden goes way up:  We don’t have explicit definitions of the interfaces between risk components, It is impossible to draw the boundaries around a testing activity and say for definite, "if we change this component, all others will be unaffected."

 
  
But, I am not going to conclude either of those things.  Because I think, even if these problems were solved, we would still, somehow, generate the extra complexity to screw ourselves again.  For example, Java got rid of a lot of the pain points of C and C++.  But, it’s clear that now other problems have come to the fore: dependency management, version control, testing and so on.  I guess you always have a biggest  problem.

When the current solution is simple, and there is money available, there will be a tendency to complicate the solution to capture missing use-cases, making the solution more complex.  As the solution becomes more complex, change becomes harder.     This is orthogonal to the defect rate of the system.  It’s not necessarily the case that the more complex system will have fewer (or more) defects.  Where defects are measured as deviations from the ideal system.  

**Prescriptions**

Is it possible to escape this trap? 

  * We can’t go backwards, to **a point of lower functionality**, even if the lower functionality place has fewer defects.    That’s because, it would then be necessary to somehow _prove_ that we had fewer defects.  And that might mean understanding our existing system.
  * **Going forwards** gets harder all the time.  More and more time is consumed in _testing_ and in _specifying_ the software.  It’s a waterfall process, and the waterfall is enormous.  
  * We could start capturing the behaviour of the system as a **set of tests.**  But the problem is, there is no instant payoff for these, they would necessarily span multiple systems and they would be fragile.  
  * We could start building **maps of the territory,** but the problem is that the territory changes and the maps are continually out-of-date. 
  * We could start doing **pure functional** programming.  Because, then you know your inputs and your outputs.  But really, I wouldn’t know where to begin on this, in any environment with multiple databases, outputs going to different places etc. etc.  
  * We could try going in an **agile** direction, that is: try to release early, and often.  And code small changes.  This may simply be impossible, given the risk-aversion and the complexity of the environments.

Honestly, right now I don’t know what the solution is.

     