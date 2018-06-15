---
id: 253
title: Round-Trip Transformations
date: 2015-10-30T07:29:36+00:00
author: bobm
layout: post
guid: http://robmoff.at/2015/10/30/round-trip-transformations/
permalink: /2015/10/30/round-trip-transformations/
categories:
  - software
tags:
  - banking-patterns
---
Following on from “Logging vs Breakdowns”, here is my second Banking pattern:

_Apart from pure calculations, all other data manipulation should be round-trip transformations._

**Examples**
  
****

  * CRUD operations:  _Store some data in the database, read it back. (Upsert/read or Delete/read)_
  * Marshalling:  turn data into XML, and back again
  * Buses:  put a message on a bus, read it off.

**Read-Only REST Service?**

Let’s say you have a  third-party service publishing data.  To get it, you need to make a REST call.  Let’s say, it’s price information on some bonds.  

What are the chances that you have read the price information properly?    Well, Murphy’s law says that if you don’t code this as a reversible transformation, you’ll get it wrong.  So, how can you do that?

Simply, you need to _extend_ the service, so that it is reversible: maybe you create a mock of the (read-only) service, so that you can put data in, and then read it back, and the reading part is functionally equivalent.  (i.e. using the same HTTP protocol etc.) In this case, you _are_ testing all the code, but you are not going to use the writing chunk in reality.

**Integrity**

A round-trip transformation is a homoiconic representation of the data.  It’s the _same data_ in a different form.   As opposed to a calculation, where fundamentally we are creating something new out of the data.   It should be easy to tell where this pattern applies by asking the question:

_Is this operation reversible at all?  Do I have everything I need to revert back to what I had at the start?_
  
__
  
I.e.  given f(x) -> y, can f’(y) -> x exist?

If so, you are looking at a round-trip operation.

**Write-Only Services?**
  
****
  
In a way, it’s even more important to subsume a write-only service into a round-tripable operation.  This is because, _you have no idea if what you wrote made it there at all.  _Again, it’s essential to mock-and-extend the interface to ensure you are testing the round-trip.

**Still Not Perfect**
  
****
  
This pattern falls short of perfection: let’s say you have to persist fields A, B and C in the database.  But, on write you transpose A and B, and on read you make the same mistake.  On the database side, your data is wrong.  At your side, it’s always correct.  

Unfortunately, _there’s nothing you can do about this._ There is always the chance of this happening.  Essentially, you have written the code and the test, and the same error is present in both.   The best you can do is to try and write the read and the write separately, so that you are coding both in a different way.  Otherwise, still it’s _tough._
  
__
  
I don’t believe there is a way to solve this problem.   

**Notable Exceptions**
  
****
  
The obvious one _should_ be logging, but we already tackled this in “Logging vs Breakdowns”.  But, really you should still be logging that you are performing some manipulation.
  
__
  
**Suggestions**

Break down all the functionality in your process to either round-trip transformations or Self-Consistent reports.  It should be clear from this that data is always bulk-gaining as you go along.  