## Lecture 8 Constraint and Computer Vision in Line Drawing Analysis (Week 14 May092021)

**Main Agenda**
- the trouble with ??as
- domain reduction algorithm
- propagation options
- deering effects
- resource ???
- Over/Under

**Gold star ideas**
- marshal arts principle
- anytime algorithm


### Simplicia Map Coloring

There are 26 states, one for each letter in the alphabet

First do a depth-first-search for a suitable coloring of this map (going down the order a-b-c-d-e...)

**At each level, we are going to rotate the color choices so we don't over-use any one color**

The program demoed in lecture is roughly 30 frames a second, and it will take 5000 years to iterate through.

If you use as many states as there are in the Unites States, you get up to 10^17~18th years

Of course you could do some parallels into that, and it is not as bad as chess, where you need all the atoms in the universe and you still cannot do it.

But still, it is pretty horrendous.

### Problem with dfs

If you do a depth-first-search and you have a problem like Texas and Arizona, Oklahoma, Arkansas and Louisiana first, and then wait around to do Texas last, then you get yourself into a bind by your fourth choice, that you don't discover until your 48th choice --> you develop a horrendous impossible Search

**Constraint Propagation to the Rescue!**

Just like in the case of trihedral line-drawings, we will pile up all the possible things that the value can be -- Red, Green, Blue, Yellow, and we start up constraint propagation

So we say for the upper left hand corner state, is there any reason to believe that Red is impossible? We look at the neighbors and see **what kind of constraint flows in from the neighbors**. They do not have to be Red, so there is nothing that rules out Red in the upper left hand corner state (and nothing that rules out green, blue, yellow)

_We have elected to assign colors to these states in this order: AR -> OK -> AK -> LA -> Tx_

_And we are going to rotate our color choices, just so we don't overuse any one color_

_But we are going to also have a look at Texas as we go around, because Texas is bordering on the states that we are choosing colors for_

So the only possible colors that Texas could be are RGBY

When we run out of choices to color Texas, we **back up**, so that means that Yellow is ruled out for Louisiana, and Texas is assigne Yellow. **Then we select the next color in line for Louisiana, which happens to be red**. And now this is consistent with Yellow in Texas and Blue in Arkansas.

**We are using the martial arts principle again, because the whole problem is that local constraints, undiscovered local constraints are causing downstream problems** --> we are going to use the enemies' power against them

We will look at the local constraints as we go and make sure they are not going to get us downstream

### Language to Describe What is Going On

So it is clear what the choices are.

**Vocabulary**
- Variable `v`: something that can have an assignment
- Value `x`: something that can BE an assignment
- Domain `d`: a bag of values
- Constraint `c`: a limit on (pairs of variables, and pairs of variable values), but in general it can be limit on variable values `x`

The states = variables `v`

The colors = values `x`

Domain = Bags of colors = Remaining color possibilities that we can still use on a particular state

Constraint = Map coloring constraint that no states that share a boundary can have the same color (adjacent states cannot have same color)

### Reduce Intuition to a Procedure

![ProblemStatement](./Texas_AdjacencyMatrix_Coloring.jpg)

**All we are doing is we are making these Depth-First Search assignments. Then in the neighborhood of those depth first assignments, we are looking around to see if the values that are possible include something.**

**And if they don't include anything, we know we made an irrevocable blunder and we have to back up**

![DomRed1](./DomainReductionAlg_Patrick.png)
![DomRed2](./DomainReductionAlg.jpg)