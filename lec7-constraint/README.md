## Lecture 7 Constraint Satisfaction Problem (Week 13 May012021)

Motivating example: Find legitimate coloring of the continental USA's map

Prof Patrick:
> There are some things that you needed to learn a different way, and that different way involves my telling you how it all came to be.

Patrick knows most of the people in AI, and he knows ALL of the people who did the work in Lecture 7.

This lecture will talk about the struggle for coming up with the ideas that led to one of the most powerful methods you will learn about in this subject.

It all has to do, originally with an attempt to make a computer capable of seeing.

Adolfo Guzman is a graduate student of Marvin Minsky and was doing a summer project to determine how many objects are there in a line-drawing.

Adolfo Guzman went to Boston Baby, the precursor to Toys R Us to take a lot of pictures to get a feel for the domain.

When Guzman presented this work in his PhD thesis defense, Marvin Minsky thought it was great work and MIT should make Guzman a professor.

Dave Huffman was also on the committee and said that it was ad hoc and the thesis should be rejected.

Dave Huffman is the guy who invented Huffman coding as a term paper in an information theory course taught by Bob Fano (an Italian-American computer scientist at MIT).

Huffman thought it was too ad hoc, too heuristic, it did not take advantage of anything we might know about physics.

### Trihedral + 3 faces

The world is in fact full of three face vertexes or three face junctions.


Dave Huffman wanted to develop a mathematical, different, and better theory.

All these works started off with the efforts of Guzman, who is an experimentalist, and Huffman is a mathematician.

So naturally, they approached the problem differently

We went through a lot of work and discovered that in this world, this is a complete, 100%, nothing else can be there, catalog of all possible ways the junctions can have line labels arranged around them. There is nothing else in this world.

That is a very powerful constraint.


