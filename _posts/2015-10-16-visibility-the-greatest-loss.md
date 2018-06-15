---
id: 249
title: 'Visibility:  The Greatest Loss'
date: 2015-10-16T14:38:32+00:00
author: bobm
layout: post
guid: http://robmoff.at/2015/10/16/visibility-the-greatest-loss/
permalink: /2015/10/16/visibility-the-greatest-loss/
categories:
  - software
---
I am starting to believe that the reason programming is difficult is because of the visibility issue:  There is no relationship between the code you type on the screen, and what comes out of the other end.

It requires a strange imagination to bridge the gap from one to the other.  Not to mention an overwhelming desire or need to get something done.

The closest that the man in the street gets to programming, is with Excel.  Even Excel _ruins_ visibility.  It’s really easy to lose track of how a calculation works in Excel: there’s nothing preventing that happening.  How is this cell calculated?  Well, I can see the names of the cells being referenced. If I click, I can see them: the important cells get highlighted in rainbow colours and I can see what connects to what in the formula.   But, I have to interact with Excel to get this to happen:  the model is built in my head, through my exploration of the sheet.  I am not shown the model, I have to construct it myself, cell by cell. 

**Visibility is the most easily-destroyed helpful property of software**
  
****
  
It’s not even something that’s really mourned after it’s gone.  The visibility remains in the mind of the developer.  Just like, if I hide a ball behind a curtain.  There’s no loss to me:  I _know_ the ball is behind the curtain; I put it there.  The loss is to time, when the ball is forgotten, or to the next person, who needs to know where I put the ball.

But, if we want to create systems that _can be understood_ then visibility is _really really important._  

**Banking Risk**

If you are building a computer game or a website, then this is not a problem that affects you too much:   it’s all on-screen.   Arguably, you can’t just eyeball in either case:  to see some features of the game or website you’ll need to_ _interact with it.  So, there are things that are invisible until you explore.

But, in the world of banking risk, everything is invisible.  Numbers are completely _meaningless_ until you introduce some _visualisation.  _But, visualisation is expensive.  Yes, you can put some numbers into an Excel spreadsheet.  But it’s still quite a lot of work for IT guys to take numbers and display them meaningfully.

**Wilful Loss Of Visibility**

Sometimes, people deliberately want to obfuscate the logic and meaning in order to build privileged positions for themselves.  I see this happening at work, but Michael Lewis does a good job of representing this in _Flash Boys_ too:  people profit from obfuscation:  _In the land of the blind the one-eyed man is king._

**Abstraction**
  
****
  
Abstraction is a key feature of most programming languages:  the ability to introduce an _indirection_ to say:  these cases are all examples of a more general case, so use the general case.  But, as soon as we have this indirection, we lose visibility over what is actually being done.  This is _the cost of abstraction. _
  
__
  
Indirection means that my feet can operate the pedals in the car, but I don’t know what is actually happening after that.  
  
__
  
**Encapsulation**
  
****
  
The mere idea of encapsulation is an affront to visibility:  you are saying:  “This here is a machine.  You don’t need to know how it works inside.  Use the interface and it will keep you from doing anything with the machine that you’re not supposed to do”.  

But, this is like my washing machine at home.   I have literally _no idea_ of what’s going on inside it.  I put the clothes in.  I press some buttons.  There’s water involved.  Clothes come out clean.  

Visibility is also the _cost of encapsulation.  _I can interact with the device through its simple interface.  But, as a result of providing me that simple interface, the manufacturers have (possibly deliberately) hidden from me what goes on inside.

**Modern Software Techniques Are Failing Us**
  
****
  
These tools:  encapsulation, abstraction, are _useful.  _But, they don’t come without cost.  Can we not have tools which allow us to work without this cost?  

Part of the problem is the _map and territory_ issue.   When we design software, we end up with a bunch of bytes on a computer disk, that make sense to the computer.   They make no sense to us.  People don’t work this way.    When the programmer creates the program, he is primarily concerned with communicating to the computer _what it needs to do.  _But then, we’ve added layers on top to make it easier for the programmer to use his mental faculties over time.  Things like, assemblers, third generation languages, object orientation. 

**The Real World**

But this is analogous to the _real world:_ “Stuff” is just atoms.  And atoms don’t make sense to us.  Our senses are all about managing the signals produced by these atoms, and converting them into something upon which information processing can be done.  

From this, we develop _mental models_ of things:  mental maps of territories, mental models of people’s behaviour.  Mental feedback loops: “if I eat this, I will feel full”.  

In the real world, people have to do _lots of work_ to build maps, guides, teachings that other people can use to understand the world in the way they do.  

If we conceptualize a computer program as a foreign land, it’s almost as if the programmer is primarily sculpting this landscape, but not producing any maps for it: people are forced to learn the territory themselves, or treat the whole thing like the washing machine and _not worry_ about how things happen. 

**Brain-Computer Interface**

Tools (like Eclipse, and Excel, say) don’t just try and reduce our finger-typing.  They are a brain-computer interface.  In order to fully exploit the pattern matching and inference-building techniques in the brain (the uniquely human talents which we don’t yet understand how to build in software), we need to _increase the surface area_ between the human and the computer.

Since we can’t change human perception (yet), this means that software has to _adapt to exploit the human perceptive system.  _This means, on a basic level:

  * Using colours (e.g. to highlight our code)
  * Using indentation to give structure (geography). 
  * Using _visualisations_ where possible, instead of tables of numbers.
  * Using _words_ and _iconography_ over pure opcodes.
  * Graphs and Maps at different levels of abstraction / scale.
  * _Domains:  _subdivision of the space so that you only need to consider parts in isolation.
  * Sound? 
  * Smell!?

Obviously there are areas that programming doesn’t exploit well at the moment:  geographic structure is _really really poor.  _Programs and data are often represented in trees (or, hierarchical structures).  These trees tend to be _canonical_, in the sense that they are _one particular tree_, rather than a choice from all possible trees.   For example:   java classes are shown in a package structure in Eclipse.  However, you could show them in an import-dependency structure.  This wouldn’t then be a tree, it might have cycles in it.  

**Machine Code & Beyond**

What something like assembler language does, is transform machine code into something more _visible and human.  _Abstract numbers become _instructions.  _We have removed (or at least, created a simpler) layer of indirection.  This improves visibility:  we are trained to recognise words and their meanings.  So, assembly language is the first example of improving visibility via the BCI techniques described above.

After assembly, we went beyond this:  Java, Lisp or Haskell (or any 3GL) use keywords profusely, and you get to define your own lexicon.  

Further, Java, Lisp and Haskell all take different approaches to reducing the problem space.   Java uses object orientation to reduce the scope of what you have to visualise in one go.    This is again another concession to the human visualisation system: "we know you can’t visualize _anything_, but you can visualise some smaller domain”.   Lisp uses its single list abstraction.  Haskell uses pure functions.  

Excel uses both _pure functions_ and _geography.  _
  
__
  
None of them are particularly rich in higher-level abstractions.  Java for example has packages, which are fairly weak: you can create all kinds of inter-dependencies between packages (and the objects within them) which destroy any kind of coherence  / loose coupling that the package has.

**Life**

If we want to build new, better languages, and improve the way we do things now, we need to take the hints from nature.  Obviously, this table is wrong, but it serves to indicate that we have a lot more to do:

<table>
  <tr>
    <td>
      Life Level
    </td>
    
    <td>
      Computing Level
    </td>
  </tr>
  
  <tr>
    <td>
      DNA / Proteins / RNA / Amino Acids
    </td>
    
    <td>
      Machine Code / Bits / Bytes
    </td>
  </tr>
  
  <tr>
    <td>
      Organelles / Viruses
    </td>
    
    <td>
      Functions, Methods, Data Structures
    </td>
  </tr>
  
  <tr>
    <td>
      Cells
    </td>
    
    <td>
      Objects / Source Files
    </td>
  </tr>
  
  <tr>
    <td>
      Organs
    </td>
    
    <td>
      Packages ?
    </td>
  </tr>
  
  <tr>
    <td>
      Phenotypes
    </td>
    
    <td>
      Programs
    </td>
  </tr>
  
  <tr>
    <td>
      Families
    </td>
    
    <td>
      Operating Systems / Servers
    </td>
  </tr>
  
  <tr>
    <td>
      Societies
    </td>
    
    <td>
      Organisations
    </td>
  </tr>
</table>

**Questions Arising**

  * If these different levels of hierarchy are so useful, why can’t you define _more of them?_
  * Pure4J shows that you can do a lot with annotations.   Could we also have annotations to describe this kind of super-structure in Java, say?
  * What benefits would that give us?
  * We currently deploy and run stuff at the program level.  We are starting to move up to the next level with things like Docker (i.e. OS/Server level).  But this is hopeless when we have a whole Bank to change!  What would it look like if we could manage everything together?

__
  
__