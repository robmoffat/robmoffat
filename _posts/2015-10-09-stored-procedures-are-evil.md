---
id: 218
title: Stored Procedures Are Evil
date: 2015-10-09T11:09:16+00:00
author: bobm
layout: post
guid: http://robmoff.at/2015/10/09/stored-procedures-are-evil/
permalink: /2015/10/09/stored-procedures-are-evil/
categories:
  - software
tags:
  - blog
---
For multiple reasons, under certain circumstances.

1.  If you restrict yourself to plain SQL, you can move between databases.  This is really handy if you want to be able to create in-memory databases for testing, vs. production databases, which are something else.

2.  Your logic is no longer in a single place.  This makes it harder to reason about.   Of course, if you are somehow implementing the entire application as stored procedures, then maybe this isn’t a problem. 

3.  SELECT is pure functional programming.  That’s really great.  But SP’s may have side-effects.  That makes them harder to reason about.

4.  They’re hard to test, although it’s not impossible.  

5.  Chances are, you can generate your DB using domain objects if you have good domain object meta-data (see hibernate, GORM etc).  With stored procs, this is not going to happen.

6.  The language you are using to define stored procedures was probably invented in the 1980’s.  There’ve been lots of improvements in language design since then.