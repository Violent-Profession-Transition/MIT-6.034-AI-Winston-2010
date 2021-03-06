## Lecture 2 Goal Trees and Problem Solving (Week 2 Feb132021)

Outline for Lec2:
- Modeling Human's Problem Solving
  - Generate & Test
  - Problem Reduction
- Problem Reduction Tree
- Transforms + Example
- Reflections

### Symbolic Integration Calculus

If a problem can integrate, is that program, in any sense of the word, intelligent?

You all learned how to integrate in high school, the question is, how did you do it? **Is the problem solving technique that we are trying to model by building a program that does symbolic integration, is that a common description of what people do when they solve problems?**

The kind of problem solving in Lecture 2 is like generating tests from Lecture 1, and we we engage in it without thinking too much about it. **BUT ONCE WE GET A NAME FOR IT, WE'LL GET POWER OVER IT.**

When you see an integration problem, you always try to apply a **transform**, and **make it into a different problem that is easier to solve**. You hope if you simplify it sufficiently, the pieces you have simplifed to will be found in some small table of integrals. **How many of such simplied pieces/elements have to be there ==> How much knowledge is involved**

**Problem Reduction = Take the problem we're given, and convert it into another problem that is simpler.**

First, apply safe all transforms; Then look into the table of simple integrals; Then do a test to see if we are done.

The program to do integration is a dawn-age program, written by a nearly blind, and subsequently completely blind graduate student James Slagle in 1960.
[Link to James Slagle's PhD thesis on the Symbolic Automatic INTegrator (SAINT)](https://dspace.mit.edu/bitstream/handle/1721.1/11997/31225400-MIT.pdf)

SAINT (acronym for "Symbolic Automatic INTegrator") program was written for IBM 7090 machine using punch cards (and only 32k of memory)!

SAINT took 1.5 minutes to integrate `x*exp(x^2)` and 11 minuets to integrate the MIT first year calculus final exam question (the example discussed in Lecture 2).

SAINT is written in LISP (list processing language by McCarthy).

### Goal Tree

`AND` node and `OR` node: the convention is to draw an arc over the `AND` nodes, so it looks like an `A`

Problem reduction tree, also called `AND/OR` tree, also called the **goal tree** (because this tree of problems is a tree that shows how our goals are related to each other)

James Slagle measured the depth of functional composition, to avoid something that is deeply nested and with a lot of functional compositions. (later turned out to not actually matter)

> **When a heuristic transformation or an algorithm-like transformation is applied to a goal, new goals are generated. These goals, in turn, may generate more goals, and a certain hierarchy is created. Such a hierarchy is conveniently represented by a graph or tree growing downwards.**
> -- from James Slagle thesis

SAINT is always looking across the whole tree, the leaves of the tree. Whenever it has to find a place to work on with the heuristic transformation, it happened to look at all the leaves of the tree that had not yet been dealt with, tried to find the easiest one. This involves a lot of backing up and starting over on a branch of the tree that it has previously ignored. 

### Reflections on SAINT

1. Out of the 56 hardest MIT first-year calculus quiz problems, SAINT is able to get 54/56. SAINT's set of rules lacked two transformations that were needed to solve all 56 problems (so the approach of SAINT is legit)

2. What is the maximum depth of the goal tree in the 56 problems? The maximum depth is 7. In the worst case, SAINT has to go down 7 levels of the tree.

3. What is the average depth of the 56 problems? Average is approximatedly 3. Insight: in the domain of calculus problems, integrals expressions that are given to freshmen at MIT, the average depth of problem reduction needed to solve the problem was 3. So that is not very complicated.

The depth of problem reduction needed to solve MIT hardest freshmen calculus problems is not 10 (how can anyone ever do those integrals!) and not 5 (only people destined to be math professors are going to get anything right), but **3** (ordinary mortals can do a pretty good job).

4. How many branches were unused? Only about 1. In the domain of problems that freshmen can work on in a calculus final, so it is not a large, bushy, useless tree.

The tree does not grow deep, nor does it grow broad. Most branches very quickly run into a dead end.

**Catechism to find out how much knowledge is involved:**
- what kind of knowledge is involved in doing integrations?
  - transformations
  - how goal trees work
  - when we are done with a problem
  - what don't need to be transformed if we can look it up in a table
  - same thought process goes with other domains like Circuit Theory, or Maxwell's Equations. **what is the nature of the knowledge involved --> what kind of knowledge is involved?** Is it Kirchhoff's laws, Maxwell's equations, what is it?
- how is the knowledge represented?
  - some of the knowledge recorded in a table to show what transformations there are
  - table for integral pieces
  - knowledge about goal trees was embedded in the procedure (procedurally represented)
- how is the knowledge used?
  - Straightforward: transformations are used to make the problem simpler
  - table used to trim off go to the leaves of the tree
- how much knowledge is in SAINT?
  - table of only 26 integral elements
  - only 12 safe transformations needed
  - only 12 heuristic transformations needed
  - **So just a few bits and pieces of knowledge here and there are sufficient to do everything you need to do the integration problems on a calculus final.** That is a surprise :)

Another surprise is: **the method to be used and the characteristics of the problem is highly related ==> in calculus, if you are smart, you can make the right transformation almost all the time and never back up the goal tree**. This was observed by Joel Moses (also a student of Marvin Minsky, Patrick Winston, James Slagle, and Joel Moses are all Minsky's students), and turned into a program that can beat the most dedicated mathematicians at integration. Its descendents are in MATLAB today.

### Meta Knowledge

Meta knowledge is knowledge about knowledge.

**Knowledge _about knowledge_ is power.**

### Appreciation of what it means to be intelligent

Whether a program that could do symbolic integration would/should be considered intelligent? After we have completed Lecture 2, it is expected that our feeling of intelligence in SAINT is somewhat diminished.

**Once we understand how something works, its intelligence seems to vanish**

