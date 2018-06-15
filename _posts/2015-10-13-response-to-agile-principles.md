---
id: 247
title: Response to Agile Principles
date: 2015-10-13T22:13:32+00:00
author: bobm
layout: post
guid: http://robmoff.at/2015/10/13/response-to-agile-principles/
permalink: /2015/10/13/response-to-agile-principles/
categories:
  - management
tags:
  - antipatterns,blog
---
**"Our highest priority is to satisfy the customer through early and continuous delivery of valuable software."**

  * Is this satisfying the customer?
  * Does the customer always want software continuously delivered?
  * Do they want it early?
  * Is there such a thing as too early?
  * I think the customer would often happily trade off “Early” for “some semblance of finished”.  Early means re-testing.  Early means trying to use something with features you need missing.

**"Welcome changing requirements, even late in development. Agile processes harness change for the customer’s competitive advantage."**
  
****
  
&#8211; Is there actually just one customer?
  
&#8211; We should be working out ways to prevent requirements changing, and also to elucidate requirements early on.  
  
&#8211; Often, the requirements are only really apparent after some software has been written.
  
&#8211; But, often the requirements aren’t there because people haven’t sufficiently thought them through.
  
&#8211; There is no reward for coming up with decent requirements early on.

**Deliver working software frequently, from a couple of weeks to a couple of months, with a preference to the shorter timescale.**
  
****
  
&#8211; The reason for this is _not_ get value delivered early on, per se.  It’s to get feedback loops.
  
&#8211; Also, the reason is that by practicing deployment early, you get good at it.
  
&#8211; But, there are hidden costs to deploying software (even with CI/CD).  People want to check it.  There are often forms to fill in, security reviews to do, and so on.   
  
&#8211; Software with only a few features might not be worth using at all.

**Business people and developers must work together daily throughout the project.**
  
****
  
&#8211; Except this happens never.  If they spent all their time with developers, they wouldn’t be business people.
  
&#8211; This is the single biggest failure of the agile process.  Business people (the people you need to help you) are _always_ too busy to spend much time on the project.

**Build projects around motivated individuals. Give them the environment and support they need, and trust them to get the job done.**
  
****
  
&#8211; Invariably, no project is an island.  Often you have to interact with system B, etc.

**The most efficient and effective method of conveying information to and within a development team is face-to-face conversation.**
  
****
  
&#8211; Developers hate talking to each other.
  
&#8211; People are often working in other countries, in other time zones.
  
&#8211; Face to face conversation is OK, but you need to write things down so that you remember what was said
  
&#8211; Often, everyone disagrees.  You sometimes need sign-offs.
  
&#8211; Lists are really useful.  
  
&#8211; Conversations are lost the moment they are complete.  No one ever remembers conversations the same.  Often, important people are excluded from conversations. 
  
&#8211; I conclude that this is very inefficient and very ineffective. However, it still might be for some use-case the most efficient and effective.  This is a shame.  
  
&#8211; Open source software gets built with almost none of this.  Explain.  
  
&#8211; Groupthink.
  
&#8211; Design By Committee. 
  
&#8211; There are clearly more productive ways to develop ideas. Our brains somehow do it (organising the thoughts of billions of neurons).  This is why art is a one-person-show.  If only we could access these organisational constructs.
  
&#8211; Right now I am in an _online meeting.  _We have _a list of actions.  _We are taking _notes_.  We are assigning _blame_.  We are capturing _issues in a list_.  It’s all kind of ad-hoc.  None of this is face-to-face communication.   There is a continuum here of online, offline, ad-hoc, recorded, signed-off, tracked, untracked communication.  Why?

**Working software is the primary measure of progress.**
  
****
  
&#8211; Which is measured how, exactly?
  
&#8211; What constitutes working? 
  
&#8211; How do we weigh the software we have working?
  
&#8211; Maybe this is counterproductive.  Less software is better than more.
  
&#8211; Bill Gates: “SLOC is like measuring completion of building aircraft by weighing it”.

**Agile processes promote sustainable development. The sponsors, developers, and users should be able to maintain a constant pace indefinitely.**
  
****
  
&#8211; This isn’t even a principle.  It’s just two sentences saying what you hope will be true about the world.

**Continuous attention to technical excellence and good design enhances agility.**

&#8211; I think this is another way of saying, get rid of technical debt.  

**Simplicity&#8211;the art of maximizing the amount of work not done&#8211;is essential.**

&#8211; I think this is another way of saying, get rid of technical debt.  

**The best architectures, requirements, and designs emerge from self-organizing teams.**
  
****
  
&#8211; If this is true, why do we need agile to tell us how to organise things then?

**At regular intervals, the team reflects on how to become more effective, then tunes and adjusts its behavior accordingly.**
  
****
  
&#8211; This is really just the Lean/Deming/ISO9000 thing all over again.  Is this even true anymore?  Why do teams only concern themselves with their own processes?  Can’t teams learn from each other?  Why does each team have to re-invent the wheel.  
  
&#8211; Isn’t software supposed to be some unique thing?  Shouldn’t things change as they go along?  