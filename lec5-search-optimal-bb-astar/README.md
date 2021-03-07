## Lecture 5 Search Optimal with Branch & Bound (Week 5 Mar062021)

Route 66 is popular highway in USA to go across the country, because it is the shortest.

But how do you know it is the shortest, and how do you find the shortest path?

With your eyes you can find a good path, you can't find the best possible path with just your eyes.

Today's lecture on How to find the shortest path is NOT a model of something that goes on in our head.

Search is NOT about maps, it is about CHOICES. We use maps as examples in search because they are visual, and they are convenient, and help us understand the concepts behind the algorithms.

### Heuristic Distance

How a crow would fly to your goal, or airline distance, even though there is no road.

### Oracle

Last time we were talking a lot about distances to the goal. Heuristic estimates of how far we are from the goal. Now we are doing the opposite: we are not considering how far we have got to go, we are only thinking about how far we have gone so far.

**Important Principle of Problem Solving = "ask someone who knows the answer"**

If you want to solve a problem, the easiest way is usually, ask somebody who knows the answer.

but what if the oracle is trying to delude us? --> check whether needs to extend other path length

If the other paths accumulated so far is already equal to or more than the Oralce's length to the goal, then no need to extend their lengths.

### No Oracle (Branch & Bound)

But we don't always have an Oracle around, without the Oracle that I can check against.

Just extend the shortest path, is any of the work done so far wasted? NO. Because all of the paths I have got so far are shorter than the path to the goal, **because the goal has not shown up**

So in the end, we don't actually need the Oracle. Can just develop the graph by extending the shortest path so far, until hit the goal. This guarantees you will find a path that is as short as you can possibly find (since there is no zero or negative distance lengths).

**Branch & Bound is almost doing British Museum search**

Awful lot of work: it put 1354 paths onto the queue (enqueueing part), it extends 835 paths that had come to the front of the queue.

**Enqueueing vs Extending:** here we want to be sure that anything we extend is a short path. We are keeping track of all the nodes, all of the paths that end in nodes, unless they have already been extended beyond that particular place.

**Prune the tree by NOT extend anything that I've already extended (because we are aiming for optimality), it is guaranteed to have a longer path length than something that already got to that same place.**

### Branch & Bound with Extended List

Still doing a lot of work, still examining a lot of paths, but instead of 835 extensions, now it only did 38 extensions

Note it is just a layering on top of branching out, it is not a different algorithm. It is an adjustment and improvement to the algorithm, making it more efficient.

**Dead horse principle: as soon as we figure out that a path goes to a particular place can't possibly be the winning path, we get rid of it, and don't bother extending it.**

### Branch & Bound with Admissible Heuristic

Using a lower bound on the **distance remaining**, the airline distance --> **extend the path that seems to have the shortest potential distance**

If the heuristic estimate is guaranteed to be less than the actual distance, that is called an admissible heuristic --> _admissible because you can use it for this kind of purpose_

## It almost always depends on the problem itself

If you change the problem, different Branch & Bound adjustments get different results.

When we start from the extreme left, there is no room of improvement for admissible heuristics since every extension has a shorter potential distance.

But when we start from the middle, extended list will foolishly visit the nodes on the left, since it is going to **just not repeat any movements through the same node again, but it is not going to keep us out of the left side because it has no idea of the remaining airline distance to the goal.**

## Use both extended-list and admissible heuristic at the same time == `A*`

They both have the possibility of doing us a lot of good, so maybe if we put them in harness together, we will get something that is even better.

| Find the BEST path instead of a _good_ path |
| ----------- |
| Oracle      |
| Branch & Bound   |
| + Extended List |
| + Admissible Heuristic |
| = `A*` |

Extended list is a layer on top of Branch & Bound

The admissible heuristic is another layer on top of Branch & Bound

`A*` is Branch & Bound, plus an extended list, plus an admissible heuristic

NOTE: in non-Euclidean case, admissible heuristic is not enough, we need consistency heuristic: |H(x,G)-H(y,G)|<= D(x,y)

When computation is extrememly expensive, you want to use every advantage you can

