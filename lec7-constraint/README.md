## Lecture 7 Constraint and Computer Vision in Line Drawing Analysis (Week 13 May012021)

Motivating example: Find legitimate coloring of the continental USA's map

Prof Patrick:
> There are some things that you needed to learn a different way, and that different way involves my telling you how it all came to be.

Patrick knows most of the people in AI, and he knows ALL of the people who did the work in Lecture 7.

This lecture will talk about the struggle for coming up with the ideas that led to one of the most powerful methods you will learn about in this subject.

### Computer Vision and Line Drawing Analysis

It all has to do, originally with an attempt to make a computer capable of seeing. So people start with seeing simple things like children's blocks.

Adolfo Guzman is a graduate student of Marvin Minsky and was doing a summer project to look at a line drawing and determine how many objects are there in a line drawing.

Adolfo Guzman went to Boston Baby, the precursor to Toys R Us to take a lot of pictures to get a feel for the domain.

## Which faces belong together in an object

When Guzman presented this work in his PhD thesis defense, Marvin Minsky thought it was great work and MIT should make Guzman a professor.

Dave Huffman was also on the committee and said that it was ad hoc and the thesis should be rejected.

Dave Huffman is the guy who invented Huffman coding as a term paper in an information theory course taught by Bob Fano (an Italian-American computer scientist at MIT).

Huffman thought it was too ad hoc, too heuristic, it did not take advantage of anything we might know about physics.

### Trihedral + 3 faces

The world is in fact full of three face vertexes or three face junctions.

Dave Huffman wanted to develop a mathematical, different, and better theory.

All these works started off with the efforts of Guzman, who is an experimentalist, and Huffman is a mathematician.

So naturally, they approached the problem differently

**important presumptions of Dave Huffman: general position + a trihedral world (all vertexes are going to be formed from 3 planes)**

We are going to deal with intersections of three planes, and try to answer **how many kinds of junctions can you see if the world is composed that way**

Huffman is also adding constraints out of the physical world.

We went through a lot of work and discovered that in this world, this is a complete, 100%, nothing else can be there, catalog of all possible ways the junctions can have line labels arranged around them. There is nothing else in this world.

That is a very powerful constraint.

**but sometimes you might interpret certain junctions as four-faced junction**, and thought you can make it but cannot label it.

### Cracks, Shadows, Non-trihedral Vertexes, and Light

Neither Guzman nor Huffman solved the problem of dealing with natural objects with shadows, with cracks, with more than trihedral vertexes in space.

This is solved by another graduate student David Waltz.

### Depth-first Search and Search Space

Naturally David Waltz wrote a depth-first search program. Each junction or vertex has its own suite of possibilities, and so it becomes a simple depth-first search problem.

**But the search space is exponential and much too big for an ordinary computer --> has to rely on constraint**

### Use Constraints to Eliminate Interpretations

Left with just one unique interpretation for all of the junctions

But there are cases where not enough constraints for us to figure the line drawings out

These line drawing interpretation results are kind of consistent with what we humans do when we look at these drawings.

So it is very likely that we in our heads **do have some constraint propagation apparatus that we use in vision**.

Solve problems that involve a lot of constraint in finding a solution.

Here we saw the constraint propagation activity at work on line drawing analysis, but next time we are going to see it at work in map coloring.
