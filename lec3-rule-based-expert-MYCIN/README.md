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

