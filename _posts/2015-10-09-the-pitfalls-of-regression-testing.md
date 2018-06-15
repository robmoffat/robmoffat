---
id: 224
title: The Pitfalls Of Regression Testing
date: 2015-10-09T11:09:34+00:00
author: bobm
layout: post
guid: http://robmoff.at/2015/10/09/the-pitfalls-of-regression-testing/
permalink: /2015/10/09/the-pitfalls-of-regression-testing/
categories:
  - software
tags:
  - antipatterns
  - blog
---
**What Is It?**

Let’s say you have two versions of some software.  A and A\*. A\* will replace version A at some period in the future.   Because we’ve not bothered to build any automated acceptance tests for either A or A\*, we want to make sure we haven’t introduced any faults into A\* that A didn’t have.  

Obviously, A might have lots of faults.  But, with regression testing we are able to prove that at least, A* won’t have any new ones.  Or are we?

Regression testing proceeds by running the two systems side-by-side using the same input data, and hopefully producing the same outputs.  Someone will usually write some kind of _diff_ (short for difference) routine to compare the results of the two systems, to see if they are the same.  

Often, this turns into an industry in itself, for reasons we will now go into.  Because, regression testing never works the way you hoped it would.

**Number Formats**

The first and most trivial problem you run into is that the numbers are different.  For example, one million can, more or less be represented in any one of these ways:

  * 1.0E6,
  * 1,000,000
  * 1000000,
  * 1000000.000000000 
  * 1,000,001

So, whoever wrote the _diff_ tool, to compare the two systems, now has to consider that the formats are different.  

In the worst case (the last one),  the numbers are _actually_ different. But, not different enough to matter.  Is anyone going to look into why the numbers have changed?  Probably not.  But a dollar here or there is nothing, right?  Right?  What about two dollars? And so on.

**Out-Of-Order Processing**

The second issue that you run into (and the second-most trivial) is that the results are in a different order coming out of each system.  If A and A* are producing _vast_ quantities of data, this in itself now becomes a software engineering problem, because somehow, you have to _sort_ the two sets of data to be the same, before you can compare them.

Again, this is not the end of the world, but the _diff_ tool gets a bit more complex.  Maybe complex enough to require it’s own database.

**Field Changes**

Third up, and also quite trivial:  the report formats coming out of A and A\* may have changed.  In the best case, A\* has added some new columns to the report, and so to compare the results of the two systems, you’re now going to need to understand the column orders and remove the extra ones from the comparison.

In the worst case, A* _changes_ the columns.  If the key changes, it might make it impossible to work out what the row from A was that needs to be compared with A*.  Usually, the mapping is recoverable but, yes of course the diff tool takes on more complexity.

**File Formats**

Maybe the original, CSV format of A is proving cumbersome, and A* is now using XML or JSON or protobufs or something crazy.  Of course, poor _diff_ now has to convert either the new format back to the old, or the old format to the new, in order to compare them.  

Sometimes, for backwards compatibility, A* will continue to also producing CSV format.  So that’s helpful for the _diff_ tool, right?  Well, some.  But are you sure that the data in the XML format is consistent with that in the CSV?   How do you know?

**Methodology Changes**

Things are starting to get serious now.  But at this stage, we’ve spent considerable efforts building _diff_ and also it’s brother, _diff-xml_, so we’re kind of committed.   The next change you start to see is that, obviously, we have made improvements in A to get A\*, so actually, there are some differences because A\* is deliberately different from A.  

This is great &#8211; these are the changes we wanted to see.  This means the software is right, yes? Well, possibly.  Some of the values are different.  But are they different _correct_ or different _broken?_  If you’re lucky, (and you have a good programmer) you might be able to get around this problem with some clever enhancements to the _diff_ which either exclude any differences due to the change, or compare in some way that takes into account the methodology change. But, probably not.  

**Aggregation Changes**
  
****
  
This is where it gets _really_ tricky: let’s say the output of A and A\* is to aggregate some input. But, the way in which aggregation is performed has changed.  You might end up with different row counts in A and A\*, and no way to reconcile them at all.   This is pretty much curtains for the diff tool, unless it only affects a few of the rows and you can exclude again.

**Non-Determinism**
  
****
  
This problem is that perhaps A and A* may not produce the same results each time they are run.   This means you can’t even regression test A with itself, let alone something new.  ‘A&#8217; may also use a back-end service in the production of its results, so even if the code in A itself is deterministic, it may be reliant on something that isn’t.  How will you work around that?

**Human Factors**

The likelihood is, whenever you run the _diff,_ someone has to eyeball the exceptions it produces.  They’ll probably be ok with this the first time, so long as there aren’t too many to look through.  After a while though, they’ll probably cheerfully tell you things are fine, even when they’re not.  They were fine the other day, so _whatevs_.  

If none of the other issues warn you against regression testing, this should be the big one:  people are not designed to repetitively do _anything. _Without oversight, they will cut corners.  Don’t put them in this position: it’s not fair.

**Too Much Trouble**
  
****
  
One of the biggest problems is that, eventually, it’s probably too much trouble.  You have to get both systems up and running at the same time, with the same input data, and deterministic services, and you might have to access the production systems for this, and then get the data out of them, and then run the diff tool and eyeball the numbers.  You’ll probably have to clone databases so that A* has the same data as A.  You’ll probably have to do that every time you run it as A is a live system&#8230;

In the end, the payback of regression testing is probably slight.  But, if you can confidently say that none of these issues is going to present a serious problem to you, then by all means, skip writing acceptance tests and go ahead.