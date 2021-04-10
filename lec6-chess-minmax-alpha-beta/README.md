## Lecture 6 Chess, Game and AI: Search min-max and alpha-beta (Week 6 Mar132021)

### Chess and AI

Hubert Dreyfus in 1963 said:
> Computers can't play chess

He then played against the Greenblatt Chess machine, and lost to the computer

Seymour Pavitt rebuttal:
> Dreyfus can't play chess either

1968 chess master David Levy bet John McCarthy that no computer would beat the world champion.

1977 DeepBlue -> chess becomes unteresting

### Game and AI

There are elements of game-play that do model some of the things that go on in our head, or model some kind of intelligence

DeepBlue adds tremendous speed.

### How to Model Chess Intelligence

There are several proposed ideas:

1. Make description of the board the same way a human would. Analysis, strategy, and tactic, to generate moves.

No one knows how to do it, until now, no game program incorporate this idea.

2. if-then rules, no evaluation of the board, does not try angthing. Look at board and select move. _Not a good approach_

3. look ahead and evaluate

Many features of the chessboard

Function of the features.

Linear scoring polynomial (more than what we need, we just need argmax)

Linear scoring polynomial not the only way to evaluate a move

4. British Museum and simply evaluate the entire tree of possibilities

**Tree of moves, with depth d and branching factor b --> there will be b^d terminal leaves**

For chess, the branching factor varies, depending on the stage of the game, the average branching factor is 14.

Claude Shannon estimated there are 10^120 leaf nodes. It did not seem to be praticable, it used to seem impossible.

There are 10^80 atoms in the universe. There are `pi*10^26` nanoseconds since the big bang.

10^80 atoms each try 1 possibility every nanosecond = 10^80 * 10^26 = 10^106 possibilities since the big bang.

**So if all the atoms in the universe were doing static evaluations at nanosecond speeds since the beginning of the Big Bang, they will still be 14 orders of magnitude short from evaluating the entire tree of moves for chess**

5. Put things together --> Look ahead not at one level but as far ahead as possible. Push the evaluation path out as far as we can and look at these static values of the leaf nodes down there.

This idea was first multiply invented by Claude Shannon and Alan Turing. They spent a lot of lunch time conversations talking with each other about how a computer might play chess against the future when there would be computers.



