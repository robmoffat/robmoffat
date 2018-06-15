---
id: 250
title: Logging Vs Breakdowns (A Reporting Pattern)
date: 2015-10-16T14:38:34+00:00
author: bobm
layout: post
guid: http://robmoff.at/2015/10/16/logging-vs-breakdowns-a-reporting-pattern/
permalink: /2015/10/16/logging-vs-breakdowns-a-reporting-pattern/
categories:
  - software
---
Recently at work, we have been discussing our risk flow application, and discussing how logging should work.  The question is:

_When a business-user has an issue with the report, how will we log the details and information used to construct the report?_
  
__
  
Discussion has centered around a standardized logging format, or a standardized location for where this logging information should go.  However, I think all of this misses the point, and instead, you should introduce a pattern, the Self-Consistent Report Pattern.  I will discuss this in detail further down, but before I do, let’s look at&#8230;

**What’s Wrong With the Logging Idea**

The problem is this:  The business receive report A.  However, they are concerned that report A is wrong.  This means that either:

  * the data coming into report A is wrong, or
  * the calculation performed in report A is wrong.  

Obviously, now they have to investigate further.  So, the next step is to get hold of the aforementioned log files.    Now, maybe this means a call to the IT team.  Or, maybe there is a service that the logs can be pulled back from.  Either way.

Having got hold of the log files, they then need to _parse the log files_ looking for the information related to the error they found.  Maybe there are four or five items of information that come in, and they have to find each of these in the log file.   

Next, they can use this information to try and perform the same calculation that was on the report.  If they come up with the **same result**, then they know _something must be wrong with the input data._
  
__
  
If they come up with a **different result,** then they know, _something is wrong with the calculation._
  
__
  
One final thing that could happen is that they realise that actually, _they_ were wrong, and in fact, there’s no problem.  But, excepting this, they can then go write up a bug report.  

So, what’s wrong with that?  Multiple things:

  1. The business user now has two separate sets of data coming in.  The report and the log.  There’s a potential for error here:  what if he gets the wrong log?  What if the log is deleted?  
  2. _Logs_ tend to be full of stuff.  The business user doesn’t care about all the stuff to do with SQL queries,  heartbeats, message queues.  They just care about the input data and the calculation.  So this stuff obfuscates what’s needed.
  3. There’s every chance that the developer hasn’t included what’s needed in the log file.  In which case, nothing can be done.  Is there any way that we can ensure the log contains everything needed?  Possibly not.
  4. Once the business user gets _just the information he’s interested in_, he still has the problem of tying up this information with the information in the report. Maybe that means lots of data merging and pulling stuff into Excel.  Either way, that’s big bit of work to do, and a likely source of error, even before he gets to the calculation.

So how can we fix this?

**The Self-Consistent Report Pattern**
  
****
  
Let’s solve this problem by adding a single constraint to our report format:

_“The report should contain both it’s input and output data.  The output data should all be derivable entirely from the input data."_

So, this is to say that if we have a calculator that (trivially, here) sums up values _A, B & C_ into a result R, then A, B, C and R should all be on the sheet, like so:

<table>
  <tr>
    <td>
      <b>A</b>
    </td>
    
    <td>
      <b>B</b>
    </td>
    
    <td>
      <b>C</b>
    </td>
    
    <td>
      <b>R</b>
    </td>
  </tr>
  
  <tr>
    <td>
      5
    </td>
    
    <td>
      9
    </td>
    
    <td>
      4
    </td>
    
    <td>
      18
    </td>
  </tr>
  
  <tr>
    <td>
      2
    </td>
    
    <td>
      11
    </td>
    
    <td>
      2
    </td>
    
    <td>
      15
    </td>
  </tr>
  
  <tr>
    <td>
      1.5
    </td>
    
    <td>
      8
    </td>
    
    <td>
      4
    </td>
    
    <td>
      12.5
    </td>
  </tr>
</table>

At a stroke, this has solved problem 1 and 2 and 4 we identified above:

  * There is no need to get a separate log, it’s all here (1).
  * Done right, the report contains _only the information you’re interested in_, and not every single attribute of data ever loaded (2). 
  * There’s no need to do the matching manually, it’s done for you (4).

What about problem 3?  This is something you can _verify_ by loading the report into Excel and figuring out whether it’s self-consistent or not:  you get some business user to try and validate the results, based on the information that’s given to them, and _nothing else._

But obviously, if you go this far, you could just _automate that test_ and write an acceptance test that makes sure that the results on the sheet can be calculated, so the business user doesn’t need to do it over and over for each release.

**The Self-Consistent Report Pattern: Reloaded**

You can go one step beyond this, and actually add your testing code _into the report itself.  _That is to say, the system responsible for producing the report is also responsible for testing the consistency of the report _before it is published.  _Essentially, you are building the acceptance test into the report itself.  

This last idea works especially well when the report is at multiple levels, or roll-ups (Maybe a trade level and a counterparty level, or line-items and totals).   You might produce these two distinct levels in different tabs of an Excel sheet, or in different files, but you can run the consistency check across all of the levels, to ensure the counts match up, or the totals match up to the line-items.  