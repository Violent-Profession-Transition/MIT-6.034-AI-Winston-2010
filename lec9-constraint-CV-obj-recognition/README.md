## Lecture 9 Constraint: Computer Vision OBject Recognition (Week 15 May162021)

**Main Agenda**
- Gospel According to Marr
- Ullman's Alignment Theory
- Ullman's Intermediate Features Theory
- Correlation
- still not solved, the attempts at solution have evolved very very slowly over the past 30 years (1980-2010)

**Gold star ideas**
- 


### David Marr, Primal Sketch, 2.5D Sketch

David Marr (1945-1980) was a British neuroscientist that integrated results from psychology, AI, and neurophysiology into new models of visual processing [wiki](https://en.wikipedia.org/wiki/David_Marr_(neuroscientist))

David Marr is such a powerful and central figure that almost anything he said was believed by a large collection of devotees.

Marr articulated a set of ideas about how computer vision would work that started off by suggesting that **with the input from the camera, you look for edges/edge fragments, and form this edge-based description of what is out there in the world, and Marr called it the PRIMAL SKETCH**

From the primal sketch, the **next step is to decorate the primal sketch with some surface normal vectors, showing where the faces on the object were oriented, and Marr called it the 2.5D sketch**

It is 2.5D because it is still 2D with camera-centric way of presenting information, but at the same time it attempts to describe the 3D arrangement of the surfaces

**The speculation was that you could not recognize the object in one step, so you needed several steps to get from the image to something you can recognize**

And the **third step was to convert the 2.5D sketch into generalized cylinders, and matched against a library of such descriptions, results in recognition**

Great theory:
1. start off by looking at edges
2. several steps of **transformations of representational apparatus**
3. produce something you can look up in a library of descriptions

Trouble is no one can make it work, too hard and too coarse to do it.
