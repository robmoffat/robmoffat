---
id: 221
title: '“Ta-Darchitecture&#8221;'
date: 2015-10-09T11:09:25+00:00
author: bobm
layout: post
guid: http://robmoff.at/2015/10/09/ta-darchitecture/
permalink: /2015/10/09/ta-darchitecture/
categories:
  - management
tags:
  - antipatterns
  - blog
---
**Name:**  "Ta-Da” Architecture.  Named for the sound made to accompany a magician when pulling a rabbit out of the hat.

**Problem:**  A grand unveiling of the design, put together by some (often well-meaning) cabal.
  
 
  
_“I know you’ve all been waiting for this for a while.  And yes, I know lot’s of plans have been on hold while we get this thing nailed down, but finally, I’d like to present to you all the architecture for our new software system.  It’s amazing, and it will replace everything we’ve got at the moment which is all now legacy.  Let me take you through this powerpoint presentation showing you what we’re going to build."_

This is how it starts.  Junior developers lean forward in their chairs. _Hey, we’re actually going to be shown… the future!_ But the seasoned hacks sigh and roll their eyes.  _ _ They’ve seen this before.  Another well-meaning, but hastily put together design which fails to correspond to any view of reality other than the author’s. 

Maybe it’s been done by a consultancy.  Maybe it’s been put together by some management “strategy” group.  The Big Ta Da! Architecture is characterised by strict secrecy up to the point of revelation.  But, this strict secrecy means that it has not been exposed to the kind of rigorous cross-examination or exposure to actual business requirements that might lead to a cogent, well-thought through design.

Often, the Ta Da Architecture is warmly received by budget holders:  There is something special in the banking world about having a “vision”.  In fact, one of the Ta-Da Architectures I’ve witnessed was called “Vision”.  It lasted for nearly two years and sucked in vast amounts of money.  For the executive proposing it, it was warmly received and got lavish funding.  Initially.  The problem was, after a year or so the realisation set in that actually, the architectural vision had prevented important business critical functionality from being delivered.  It was unceremoniously canned and the instigator moved on to pastures new.

Ta Da Architectures often disenfranchise staff who might have been in a position to contribute meaningfully.  These staff are able to see the obvious mistakes and oversights present in the system, but usually powerless to do anything about it:  once announced, the Ta Da Architecture is as good as approved, there’s no point complaining now.

**Context: **

  * You are working in a growing organisation.  
  * Stakeholders worry about the heterogenicity of the environment, or “legacy” systems.
  * There’s plenty of budget available to support pie-in-the-sky thinking.  
  * Budgets need to be justified to some extent with strategic direction.

**Building banking software is hard: **

  * There is complicated maths involved.
  * It’s difficult to tell the difference between things that work and things that don’t.
  * There are lots of exceptions to contend with.
  * The data sets get large.
  * There are lots of legacy systems.

**Forces:**

  * The need to "come up with something” to appease stakeholders/budget holders.
  * The need to look good in meetings:  if you have an architecture that keeps the stakeholders happy, then in the short term you can silence your critics.
  * Strategic plans are needed soon.
  * Architecture is _fun_.  People like starting with a clean slate.

**Supposed Solution:**

  * It will take too long to build up a set of use-cases, or a detailed set of requirements, so don’t bother with those.
  * Equally, involving everyone in a decision making process will be too time consuming.  
  * Based mainly on gut feel or previous experience, sketch out new architecture and create a powerpoint presentation.
  * Present the architecture to the budget holders to rapturous applause and approval.
  * Present the architecture to the project teams as a _fait accompli_ to begrudging acceptance._  Ta Da!_

**Resulting Context:**

  * Many of the constraints proposed are unlikely to fit the actual requirements of the projects being undertaken.
  * Rather than solving any problems, the TaDarchitecture is actually a _whole new set of requirements_ that projects now need to meet.
  * Often, these requirements will be nonsensical under detailed analysis and thought, because they were only ever intended to pass muster with budget holders.
  * Lots of people feel disillusioned that their opinions weren’t considered.

****
  
**Warning Signs**

  * Designs that promise functionality “for free”.
  * Designs which aren’t backed by requirements.
  * Whole-cloth solutions, rather than individual ideas which can be implemented on their own.

**Related Anti-Patterns:**  
  
     Waterfall
  
     BigDesignUpFront
  
     BusinessAren’tBudgetHolders
  
     GoldOwnerIsNotGoalDonor

**Compare With:**

  * YAGNI
  * 3 Strikes Then Refactor
  * Use Cases
  * Collaborative Design