---
title       : Learning Theory
subtitle    : 
author      : Ashish Kumar
job         : Data Scientist - Attune Consulting | Author  
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
github:
  user: kumar1ashish
  repo: LearningTheory
---
## Definition of Learning

A computer program is said to learn from experience E with respect to some class of tasks T and performance measure P, if its performance at tasks in T, as measured by P, improves with experience E.


Choice of P very important!! - Expert system or human comprehension? - Datamining!!

>Broad enough to include most tasks that we would call "learning tasks" but also programs that improve from experience in quite straightforward ways (rote learning or caching)!

A database system that allows users to update data entries - it improves its performance at answering database queries, based on the experience gained from databases updates (same issue as what is intelligence)

---
## Concept Learning

> Much of learning involves acquiring general concepts from specific training examples.

> Each concept can be viewed as describing some subset of the objects or events defined over a larger set.

> Alternatively each concept can be thought of as a boolean-valued function defined over this larger set.

> Concept Learning - inferring a boolean-valued function from training examples of its input and output

---
## Designing a Learning System

T: Checkers (Draughts)

P: percent of games won in world tournament

What experience?

What exactly should be learned?

How shall it be represented?

What specific algorithm to learn it?


---
## Direct versus Indirect Learning

1. Individual checkers board states and correct move for each
2. Move sequences and final outcomes of various games played.

> Credit Assignment Problem - the degree to which each move in the sequence deserves credit or blame for the final outcome - game can be lost even when early moves are optimal, if these are followed later by poor moves or vice versa


---
## Teacher or not?

Degree to which learner controls the sequence of training examples

Teacher selects informative board states & provides the correct moves.

For each proposed board state the learner finds particularly confusing it asks the teacher for correct move

Learner may have complete control as it does when it learns by playing itself with no teacher - learner may choose between experimenting with novel board states or honing its skill by playing minor variations of promising lines of play


---

## Choose Training Experience

How well training experience represents the distribution of examples over which the final system performance P must be measured

P is percent of games in the world tournament, obvious danger when E consists of only games played against itself (probably can't get world champion to teach computer!)
most current theories of machine learning assume that the distribution of training examples is identical to the distribution of test examples

It is IMPORTANT to keep in mind that this assumption must often be violated in practise.


E: play games against itself (advantage of getting a lot of data this way)


---

##  Choose a Target Function

ChooseMove: B -> M where B is any legal board state and M is a legal move (hopefully the "best" legal move)

alternatively, function V: B ->R which maps from B to some real value where higher scores are assigned to better board states
now use the legal moves to generate every subsequent board state and use V to choose the best one and therefore the best legal move


---

## Choose Rep. for Target Func.

Use a large table with an entry specifying a value for each distinct board state

Collection of rules that match against features of the board state 

Quadratic polynomial function of predefined board features

Artificial neural network

NOTICE - choice of representation is closely tied to an algorithm choice!!

## Expressibility Tradeoff

Very expressive representations allow close approximations to the ideal target function V,
but the more expressive the representation the more training data the program will require in order to choose among the alternative hypothesis

Also depending on the purpose, a more expressive representation might make it more or less easy for people to understand!!

---

## Design 

T: Checkers

P: percent of games won in world tournament

E: games played against self

V: Board -> R

Target Function Representation:


---
## Choose Function Approx. Algo.

First need Set of training examples

<b,Vtrain(b)>
< (z1=3,z2=0,z3=1,z4=0,z5=0),+100>   because z2=0
Vtrain(b)<- V1(Successor(b))

good if  V1 tends to be more accurate for board positions closer to game's end


## Choose Learning Algorithm

Learning Algorithm for choosing weights   W1 to best fit the set of training examples  {<b,Vtrain(b)>}={<b,V1(Successor(b)>)

Best fit could be defined as minimizes the squared error E

We seek the weights that minimize E for the observed training examples.

We need an algorithm that incrementally refines the weights as new training examples become available & is robust to errors in estimated training values.

One such algorithm is LMS (basis of Neural Network algorithms)

---
## Least Mean Squares

LMS adjusts the weights a small amount in the direction that reduces the error on this training example

Stochastic gradient-descent search through the space of possible hypothesis to minimize the squared error









                         ..to be continued




