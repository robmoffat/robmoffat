---
id: 222
title: Why Jira Fails
date: 2015-10-09T11:09:28+00:00
author: bobm
layout: post
guid: http://robmoff.at/2015/10/09/why-jira-fails/
permalink: /2015/10/09/why-jira-fails/
categories:
  - software
tags:
  - antipatterns
  - blog
---
Bug & feature tracking should be really simple, but it ends up not being.   Here are two problems:

**The Extra Field**

At some stage, someone requests that they can sort by some new field.  Like, “Service Name” or something banal.  This gets used by some people on the project, but not everyone, and not consistently.  The integrity of the database is now compromised.  You can’t rely on “Service Name”.

Quick Fix:  Tagging

**The Lifecycle Bloat**

Someone says, we need another stage in the lifecycle of a bug, called "Pre-UAT Testing".   This is added.  Now, we all have to work through a more complicated lifecycle.  This gets used by some people on the project, but not everyone, and not consistently. 

The integrity of the database is now compromised.  You can’t rely on “Pre-UAT Testing” always being a thing.

**What Went Wrong?**

Not everyone has the same mental model of the process, or the shape of the system.  They then try to change the system to map onto their mental process.  In the process though they introduce complexity, and confusion.  Now the system fails to map onto other people’s mental processes. 

There is a good argument for using the Lowest Common Denominator.  This maps onto no-one’s understanding of the process.  In fact, it might change the process to be something simpler as people adapt.  

Different software processes have different requirements, but Jira tries to meet all of these requirements, and bloats in complexity because of this.

The BitBucket Issue Tracker was better than Jira, because of everything it left out, not because of what features it had.

**Summary**

  * If there are n people in the system, then we have n+1 models of the system, where the extra one is Jira.
  * Ideally, we need to harmonise these n+1 models into the single model of Jira. 
  * But, for some people, their model will not fit into Jira.
  * If we change Jira, then it’s likely to be more complicated, and people are less likely to understand the model in Jira.
  * Some models in n don’t make any sense at all, when they’re thought through.  Sometimes, they end up being the model used in Jira.

**How To Solve This Problem**

  * The development process should define the tracker.  The tracker should support the development process.  
  * Both the tracker and the development process need to be so stupidly straight forward that everyone can understand the model. 
  * Both the tracker and the development process need to be sufficient to build software properly.
  * If you want people to use your development process, bake it into software so they have to accept your model.