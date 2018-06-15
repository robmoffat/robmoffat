---
id: 216
title: Breaking Inversion Of Control
date: 2015-10-09T11:09:11+00:00
author: bobm
layout: post
guid: http://robmoff.at/2015/10/09/breaking-inversion-of-control/
permalink: /2015/10/09/breaking-inversion-of-control/
categories:
  - software
tags:
  - antipatterns
  - blog
---
Inversion of control is much like pure functional programming, but watered down.

<table>
  <tr>
    <td>
    </td>
    
    <td>
      Pure Functions
    </td>
    
    <td>
      IoC
    </td>
  </tr>
  
  <tr>
    <td>
      You don’t go off and resolve your own dependencies
    </td>
    
    <td>
      Y
    </td>
    
    <td>
      Y
    </td>
  </tr>
  
  <tr>
    <td>
      Don’t change the state of your context (side effects)
    </td>
    
    <td>
      Y
    </td>
    
    <td>
      N
    </td>
  </tr>
  
  <tr>
    <td>
      Deterministic (rely only on other pure functions)
    </td>
    
    <td>
      Y
    </td>
    
    <td>
      N
    </td>
  </tr>
</table>

Actually, I think that’s it.  The difference is that purity means you don’t change the context.

This means with pure functions, you can be _lazy,_ and only evaluate when the result is needed.  This is an optimisation.  Also, knowing you haven’t changed the context is valuable, as you can cache the result.