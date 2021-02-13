# MIT-6.034-AI-Winston-2010
Pharmacy Meets AI

---

## Lecture 1 Overview (Week 1 Feb062021)

Covenant Number 1: No laptops, please

AI has to do with **thinking** (whatever that is)

AI is not only about thinking, it is also about **perception and action**

In an engieering scope, AI is about **models targeted at thinking, perception and action**

Model making is what MIT is about:
> We build models using differential equations. We build models using probabilities. We build models using physical and computational simulations.
> ... Models to explain the past and predict the future, understand the subject, and control the world.

If I take this class, will I get smarter? Yes. Because you will have better models of your own thinking.

**In order to have a model, you have to have representation**

AI = representations that support the making of models targeted at thinking, perception, and action.

What is a representation?

### Farmer, Fox, Goose, and Grain Problem

Representations and graph. 2^4=16 possible representations of the situations.

**Constraints exposed** due to the right representations, just like algebra; **algebraic notation expose the constraints**

AI is also about the algorithms/procedures/methods

**AI = algorithms, methods, representations**

### Generate and Test

MIT leaf, what kind of leaf is it?

**Generating some possible solutions, feeding them into a box that tests them, and then outputs failure and success**

**Rumpelstiltskin Principle: once you can name something, you get power over it**

The end of your shoelace = aglet, it keeps the thing from unwinding

**Ability to name things: symbolic labels give us power over concepts**

The most simple ideas in AI are often the most powerful

**You've Got the Representation Right, You're often Almost Done!**

### How many countries in Africa does the Equator cross?

Your eyes count the visual map and translate back to a number 6. Vision system and language system.

### History of AI

Started with Lady Lovelace 1842:
> The analytical engine has no pretensions to originiate anything. It can do whatever we know how to order it to perform.

1950s Alan Turing and Turing Test

Marvin Minsky in 1960: "Steps Toward Artificial Intelligence"

A nearly blind graduate student wrote a program that did symbolic integration

Took the world by storm, because not everyone knows how to do integration, and world was hyped.

Eliza program chat bot

Program to do geometric analogy (similar to popular intelligence test)

Late dawn age, we turn attention from purely symbolic reasoning to perceptual apparatus: the nature of shapes and forms

Late dawn age, learning systems. Some neural net training with thousands of trials

Important late dawn development: **rule-based expert systems**

For example, the Atlanta airport, your airplane is parked by a rule-based expert system that knows how to park air-crafts effectively.

Bulldozer age: Deep Blue. Bulldozer = we have at our disposal unlimited amounts of computing, and frequently you can substitute computing for intelligence. So no one would say that Deep Blue does anything like what a human chess master does, Deep Blue processes data like a bulldozer processing gravel

Current age? Imagination age?

200,000 years we have been in the current anatomical form. Then the ensuing 150,000 years not much evolution. Then 50,000 years ago, some group of human developed a capability that separated human from all other species

Quoting Noam Chomsky:
> It seems that shortly before 50,000 years ago, some small group of us acqured the ability to take two concepts, and combine them to make a third concept, without disturbing the original two concepts, without limit.

We learned how to begin to describe things, in a way that was intimately connected with language. (But we also think with our eyes)

### Language and 

Language does two things:
- it enables us to make descriptions. Descriptions enable us to tell stories. Storytelling and story understanding is what all of education is about
- it enables us to marshal the resources of our perceptual systems, and even command our perceptual systems to imagine things we have never seen

"Imagine running down the street with a full bucket of water"

**language is at the center of things**

---

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


