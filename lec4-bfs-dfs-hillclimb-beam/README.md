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
5. Beam Search = BFS with informing heuristics, limit the number of paths to be considered at any level
6. Best First Search = always work on the leaf node that is best, closest to the goal

**Search not = Maps! Search is about choice. Search is not about maps. It is about the choices you make when you are trying to make decisions.** For example, the **choices you make** when you explore the map.

**Backing up to the place where we last made a decision == backup or backtracking**

BFS is duplicating paths it has already searched ==> silly thing of going back through the final node that's already been gone through.

More clever searches = more informed search by taking into consideration whether we seem to be getting anywhere. In general, it is a good thing to get closer to where we want to go. **if you have some heuristic that tells you if you are getting closer to the goal, you should use it ==> hill climbing + DFS / beam + BFS**

_It is not often the case you have extra information in decision making about heuristic measurement of distance to the goal, in which case you cannot use informed search. But if you have such heuristic measurement, you should use it in your search._

DFS + heuristics = Hill-climbing

BFS + heuristics = Beam (beam width = top W best nodes that get us closest to the goal)

Best first search was seen in SAINT integration program, it is always taking the easiest problem in the search tree and work on that.

| Search Method  | Backtracking | Use Enqueued List | Informed Search |
| ------------- | ------------- | --- | --- |
| British Museum | N.A. (backtracking is not relevant because **British Museum has to find everything**, cannot quit if you found one.  | N.A. | N.A. |
| Depth First | Yes (optional add-on) | Helpful | No |
| Breadth First | No backtracking | Helpful | No |
| Hill Climbing | Yes, backtracking like DFS | Helpful | Yes, making use of heuristic information |
| Beam | No like BFS | Helpful | Yes, informing heuristics |

### Continuous Space Search with Hill Climbing

like in multi-variate calculus

In continuous spaces, the Hill Climbing sometimes lead to problems that cannot perform

Mountin, big fog, trying to climb uphill before freeze ==> use compass and take a few steps in North, South, West and East directions, and see which direction seems to be doing the best job of getting us moving upward ==> explore the four directions we can go and pick the "best" one.

A lot of people do freeze to death on Mt. Washington when the fog comes up, Hill Climbing fails them and they cannot get to the top to the ranger station. The reason is **there are large lawns on the shoulders of Mt. Washington and quite flat**

**Hill Climbing depends on what the space is like:** stuck on local maximum, long plateau/tele-phone pole problem (most surfaces are flat, only small spikes of phone pole), sharp ridge (fooled into thinking you are on top, but you are just on a sharp ridge)

### Search as a model of what goes on in our head

We have "searches" happening in our heads, anytime we make a plan, we are evaluating a bunch of choices and seeing how they work.

