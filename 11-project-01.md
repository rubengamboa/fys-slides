---

title:        COSC 1101 The Beauty & Joy of Computing
subtitle:     Project Information
author:       Ruben Gamboa
date:         September 30, 2015
#logo:         uw-logo-large.png
#biglogo:      uw-logo-large.png
job:          Professor
highlighter:  highlight.js
hitheme:      tomorrow             # default
mode:         selfcontained        # {standalone, draft}
framework:    io2012               # {io2012, html5slides, shower, dzslides, revealjs, ...}
widgets:      [mathjax, bootstrap] # {mathjax, quiz, bootstrap}

---

<style>
slide.title-slide {
     background-color: #EDE0CF; /* CBE7A5; #EDE0CF; ; #CA9F9D*/
     background-image: url(assets/img/uw-logo-large.png);
     background-repeat: no-repeat;
     background-position: center top;
   }
slide:not(.title-slide) {
    background-image: url(assets/img/uw-logo-small.png);
    background-repeat: no-repeat;
    background-position: right bottom;
    background-size: 24px;
}
</style>

# Staying on Course

---

## Difference between High School and College

High School                                               | College                                      
----------------------------------------------------------|----------------------------------------------
Mandatory & Free                                          | Voluntary & Expensive
Fully structured time                                     | Largely unstructured
Need permission to participate in extracurriculars        | Up to you!
Parents and teachers give friendly reminders              | Up to you!
35 hours per week in class                                | 12-15 hours per week in class
Classes chosen by counselors                              | Up to you!
Teachers/counselors keep track of your progress           | Up to you! 
Told what to do and corrected if necessary                | Take responsibility and suffer consequences

---

## Difference between High School and College

AP Course                                                 | College Course                               
----------------------------------------------------------|----------------------------------------------
170 hours                                                 | 40 hours
Study 0-2 hours a week outside of class                   | Study 6-9 hours / week per class
Casual listening is enough                                | Need to interact deeply with material
Material is largely learned in class                      | Material is largely learned outside of class
Reading materials are repeated in class                   | It is assumed that you've read and understood readings

---

## Difference between High School and College

High School                                               | College                                      
----------------------------------------------------------|----------------------------------------------
Teachers grade everything                                 | Professors grade some things and may assign "optional" homework
Teachers remind you of incomplete work                    | Professors may not know if you've completed your work
Teachers seek you ouf if they think you're in trouble     | Professors expect you to seek them out
Teachers carefully take attendance                        | Professors rarely take attendance (but know if you're frequently absent)
Teachers take responsibility for your success             | Professors wish you well

---

## Difference between High School and College

High School                                               | College                                      
----------------------------------------------------------|----------------------------------------------
Lots of tests over small amounts of material              | 2-3 big tests
Makeup tests available                                    | Hardly ever
Tests scheduled to avoid school events                    | Tests scheduled by ebb and flow of class
Review sessions, sample tests, etc.                       | Maybe Q/A sessions
Lots of opportunities to turn things around               | Hard to recover from serious mistakes

---

# Lab 4

---

## Testing whether N is Prime

* Elementary school algorithm
  * Check to see if 2 divides N -- if it does, N is not a prime
  * Check to see if 3 divides N -- if it does, N is not a prime
  * ...
  * Check to see if N-1 divides N -- if it does, N is not a prime
  * N must be a prime!

---&twocol

## Testing whether N is Prime

*** =left

* Translating school algorithm to *Snap!*

           if 2 divides N
               report FALSE
           if 3 divides N
               report FALSE
           ...
           if N-1 divides N
               report FALSE
           report TRUE
     
*** =right

> * Translating "X divides N"
    * Use mod block to get remainder, as in "X mod N = 0"

> * Using a loop
    * We don't want to have a lot of similar statements
    * We can't do it, unless we know N ahead of time
    * Use a "repeat until" loop, with a variable K that starts at 2 and goes up to N-1

---&twocol

## Writing Snap! in English (e.g., for Exam)

*** =left

<div class="centered">
    <img src="assets/img/snap-program.png" width="288" title="Snap Program" alt="Snap Program">
</div>

*** =right

        when green flag is clicked
            pen up
            clear
            go to x: 0 y: 0
            point in direction 90
            pen down
            for i=1 to 200
                move i steps
                turn right 121 degrees

---

## Writing Snap! in English (e.g., for Exam)

<p style="font-size: 200%; color: red">Don't Panic!</p>

> * All of these are considered the same
    * move 100 steps
    * move 100
    * walk 100
    * run 100
    * fly 100
    * scooch over by 100

> * I want to know that you can almost remember the right blocks to use

> * I need to understand what blocks go inside what other blocks (for repeat, if, etc.)

---

# The Project

---

## Mechanics

* Brush up on your grammar, style, spelling, etc.

* These things are important for this class -- and more important, for your life

* Bottom line: Do not butcher the Queen's language!

---

## Current Status

* You should have already finished TIP (and many of you have)

* Maybe you should have an idea

* Now it's time to go out and get started in the project

---

## Choosing a Topic

* Anything you're interested in

* There should be a connection to computing (but that's usually easy)

* Now you have to learn how computing is used or may affect your topic of interest

---

## Example Topic

* I'm interested in **astronomy**

* I've heard about **survey projects** that generate a lot of data

* Computers have to come into that somehow

---

## Writing Process

1. Collect
2. Plan
3. Develop

You've seen variations of that in school, but they're usually focused on the **paper**.
I want you focused on the **ideas**.

---

## Collect

* Find materials that will make it into the writing
  * read
  * research
  * take notes
  * think
  * make mental connections
  * maps or webs
  * list-making
  * freewriting

---

## Collect: Example

* I need to find some astronomy surveys
  * Sloan Digital Sky Survey (SDSS)
  * Large Synoptic Survey Telescope (LSST)

* What can they do?

* How much data do they generate?

* What do people do with that data?

> * **Problem:** too much data for people to handle and analyze in real time!

> * **Solution:** software pipelines that automatically process the data

---

## Collect: Sources

* Very important!

* We need to keep track of **where** we're learning things from

* This will become the bibliography
  * It should be varied
  * Include at least one trip to the library for a journal-quality article
  * Can also include books, magazines, websites, etc.

* Project background information (with references) is **due October 16**

---

## Plan

* All planning activities
  * map
  * list
  * rehearse
  * outline
  * polish that topic

---

## Plan: Example

* We're looking at the software pipeline for an astronomical survey

* What needs to happen?

* What does the data look like coming in?

* What do the products look like coming out?

* What tough problems are involved?

> * **Problem:** How do we know what we're looking at?

> * **Solution:** Use machine learning to tell stars and (very distant) galaxies apart!

---&twocol

## Develop

*** =left

* Choice 1: Actual writing
  * draft
  * revise
  * proof read
  * edit

*** =right

> * Choice 2: Program
    * identify key abstractions
    * pick data
    * decide how data should be processed
    * test
    * fix
    * test some more
    * fix some more
    * . . . .

---

## Develop: Example Paper

* Thesis: How can computers learn to distinguish stars from galaxies that take up only 1 pixel?

* What background do we need to explain?

* Organize the background material

* Write first draft

* Wait a couple of days

* Read first draft, panic

* Wait a couple of days

* Write second draft

* Read second draft, better

* Repeat as needed

---

## Develop: Example Software

* Goal: Distinguish stars from galaxies that take up only 1 pixel?

* What is this "machine learning" thing, anyway?

* How do they do it?
  * Different shape of SED (Spectral Energy Distribution)

* What data do we need?
  * Entire SED gives us the "ground truth"
  * Intensity at different colors can be used for learning

* What processing can we use?
  * Machine learning looks way too fancy
  * Maybe we can just look for one value that distinguishes stars from galaxies

---

## Develop: Example Software

* Write a program that goes through a list of objects
  * Each object has intensity at colors U and B
  * Each object says whether it's a star or galaxy (from complete SED)

* Compute U-B for each object

* Find a cut-off X such that object is a star if U-B > X

* Then go through another list of object to predict (using X) if they're stars or galaxies
  * Use "ground truth" (from complete SED) to see how many we get right
  * Pray that it's better than 50-50
  
* Bottom line: You showed you learned a lot of the background, and you wrote a program that used some of it

---

# Wrapping Up Chapter 2

---

## Software Is Eating Our Lunch

* What is the thesis of the article?

* What is *Creative Disruption*?

* How well did the predictions of the article hold up?

* What new tech giants are coming?

