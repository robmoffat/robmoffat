---
id: 251
title: Why Are We Not All Just Building Things In SQL Databases?
date: 2015-10-21T21:20:34+00:00
author: bobm
layout: post
guid: http://robmoff.at/2015/10/21/why-are-we-not-all-just-building-things-in-sql-databases/
permalink: /2015/10/21/why-are-we-not-all-just-building-things-in-sql-databases/
categories:
  - Uncategorized
---
It should have been so easy:  transactional datastores, functional query languages on top of them, and then a programming language to modify stuff.  The promise of the DBMS.  But what went wrong?  Why do we have such a messy, complex landscape?

One problem is the cost:  databases _used to be_ hideously expensive.  A second is the language:  programming in SQL _sucked._  And while things like Oracle tried to bolt on Java as best they could, this always seemed… messy.   Coding everything with stored procedures didn’t work. 

And then there was the web:  Databases were a poor option if you wanted to build interactive web pages, whereas servlets gave you the freedom to do _anything_ that the protocol supported.  So, really there was no choice.  In order to build web-enabled applications, people were forced outside the DBMS to deliver them.  

Another thing is separation of concerns:   If you build _outside_ the database, then maybe you can swap the database for something else, at some future time.   This never happened, in reality, but at design-time it gave you extra choices.

What about in banks?  Going back, I remember the GriMis database at DB: you put risk numbers in, and they were pulled back into the report server.  It had to be this way as the databases weren’t fast enough to do the reporting themselves.  So, again, the databases let the side down.  Otherwise, you could have achieved the same result doing just SQL, and we could have saved the man-years of effort building the report server first in C++ and then in Java.

Somehow, over time, databases got relegated to the role of just being data stores, and application servers took over creating transactions for them and hosting the applications.   Somehow, this was _faster_ (despite extra networking costs).  And, this allowed databases to scale horizontally into the unmanageable mess of one-for-each-app rather than just vertically one-for-the-whole-enterprise which was bound by the size of the DBMS architecture and the hardware it ran on.

It’s not hard to see how you go from this fragmented picture to where we are today:  in each case, the short-term advantage of building something now trumps the long term homogeneity of the environment.  And so, we end up in massively heterogeneous environments: there is no long term.  The only place that homogeneity exists _is at the network layer._    

Lessons:

  * Heterogeneity wins, because decisions about complexity are made considering only the short-term.  
  * Heterogeneity wins, because, having given up the long term, people optimise on the problem areas they are facing, rather than considering the big picture.
  * _How did homogeneity win at the network layer??_  There were standards, they bought the same wires for the whole building, maybe the problem domain was small enough that they could consider it all in one go, also there are ways to convert between one network and another.
  * _Do One Thing Well.  _You can’t possibly solve all problems in the database.  You need to go wider.  So, programming languages were always going to be a separate thing to the database layer.  They couldn’t own the whole picture.