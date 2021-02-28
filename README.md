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

---

## Lecture 3 Rule-based Expert System (Week 3 Feb202021)

### Block Program PUT-ON/CLEAR-TOP/GET-RID-OF

Demo of a program written by Terry Winograd (MIT/Stanford) using natural language processing, and **it is a program that looks like it is kind of smart and it somehow can answer questions about its own behavior**

The structure of the program is extrememly simple: how can you get such apparently complex-looking behavior out of such a simple program?

**Why it does something vs How it does something**: Why goes one level up for answer, How goes one level down for answer

Trace of program actions ==> **Goals**, or objectives the program wants to do ==> program will leave its trace, which is a goal tree (aka AND/OR Tree)

Similar to the goal-tree in the SAINT program for integration

**A program can answer (certain) questions about its own behavior as long as it has a and-or/goal tree**

**The complexity of the program's behavior is largely a consequence NOT of the _complexity of the program_, but the building of a giant goal-tree (as a consequence of the _complexity of the problem_**

### Simon's Ant

Late 1960s by Herb Simon(司马贺) [wiki link](https://en.wikipedia.org/wiki/Herbert_A._Simon) in a lecture "The Sciences of the Artificial" said:
> Imagine you are looking on a beach at a path of an ant, the path of the ant looks complicated and you think the ant is a genius. But if you look closely, the ant is just avoiding the pebbles on the beach.
> The complexcity of the behavior is the consequence of the complexity of the environment, not the complexity of the program

**Complex behavior, simple program ==> the problem has the complexity, not the program**

### Rule-based "expert" systems

The rule-based expert systems were developed in a burst of enthusiasm about the prospects for commercial applications of AI in the mid 1980s. AT that time, it was supposed that you can account for useful aspects of human intelligence by writing all of the knowledge in the form of simple rules. BUT all the knowledge had to be encapsulated in the form of simple rules.

Thousands of such systems were written.

#### Example of an Identification rule-based expert system: MYCIN

Classic program also written at Stanford: MYCIN, to diagnose bacterial infections of the blood.

Doctors asking you a lot of questions about your disease.

Use identifying animal as an example of MYCIN: write down all the things we can observe about an animal and try to figure out what that animal is.

**Forward-chaining Rule-based "Expert" System** (expert is for marketing reasons)
- not equipped with **common sense**
- do not have ability to deal with previous cases (unlike in medical school training)
- really novice systems that reason on bases of rules
- can also answer questions about its own behavior --> has goal-tree

**Backward-chaining = backwards from hypothesis to the facts; instead of from facts forward to the conclusions**

These rule-based system is sufficient to confuse even the expert that they were patterned after.

### Knowledge Engineering

Heuristics:
- look at specific cases, elicit from people knowledge they otherwise would not have thought to give you
- ask questions about things that appear to be the same but are handled differently
- build a system and see when it cracks --> to discover missing rules
- **knowledge engineer yourself! mechanisms for making yourself smarter and learn new subjects**
- the experts won't think what to tell you unless you:
  - elicit that information by specific cases
  - ask quetsions about differences
  - ultimately do some experiments to see where your program is correct

Are these systems really smart? Do rules have anything to do with common sense?

**When we tell a story, it is mostly a matter of controlled hallucination**: I know what rules are in your head, so I could take advantage of that in telling the story and not have to tell you anything that I'm sure you are going to know.

---

## Lecture 4 Search 1 (Week 4 Feb282021)

Search path of a thief vs honest beginner vs expert.

Not talking about optimal path today. Just pretty good paths and heuristic paths.

### Problem solving with the eyes

**We can visually using our eyes within seconds find a pretty good path, not the optimal one, but a pretty good one. And we do not know how using our eyes AI works.**

Important part of our total intelligence. We will never have a complete theory of human intelligence until we can understand the contributions of the human visual systems to solve everyday problems.

But for this course, **our programs do not have eyes, and they don't have visually grounded algorithms**.

### Intuition on how various search works

**IMPT: develop search tree in lexical order (the nodes are listed alphabetically)**

**IMPT: we don't have searches bite their own tail. No path is ever allowed to bite itself, to go around and enter and get back to a place that is already on the path**

1. British Museum approach = You find every possible path
2. Depth First Search = barrel ahead in a single-minded way
3. Breadth First Search = build up the tree level by level and SCAN ACROSS a level
4. Hill Climbing = DFS but not using simple lexical order to break ties, instead use which node is closer to the goal

**Search not = Maps! Search is about choice. Search is not about maps. It is about the choices you make when you are trying to make decisions.** For example, the **choices you make** when you explore the map.

**Backing up to the place where we last made a decision == backup or backtracking**

BFS is duplicating paths it has already searched ==> silly thing of going back through the final node that's already been gone through.

More clever searches = more informed search by taking into consideration whether we seem to be getting anywhere. In general, it is a good thing to get closer to where we want to go. **if you have some heuristic that tells you if you are getting closer to the goal, you should use it ==> hill climbing + DFS**

_It is not often the case you have extra information in decision making about heuristic measurement of distance to the goal, in which case you cannot use informed search. But if you have such heuristic measurement, you should use it in your search._

| Search Method  | Backtracking | Use Enqueued List | Informed Search |
| ------------- | ------------- | --- | --- |
| British Museum | N.A. (backtracking is not relevant because **British Museum has to find everything**, cannot quit if you found one.  | N.A. | N.A. |
| Depth First | Yes (optional add-on) | Helpful | No |
| Breadth First | No backtracking | Helpful | No |
| Hill Climbing | Yes, backtracking like DFS | Helpful | Yes, making use of heuristic information |

### Search as a model of what goes on in our head


