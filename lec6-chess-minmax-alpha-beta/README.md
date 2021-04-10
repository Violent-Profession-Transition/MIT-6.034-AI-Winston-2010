## Lecture 6 Chess, Game and AI: Search min-max and alpha-beta (Week 6 Mar132021)

### Chess and AI

Hubert Dreyfus, a MIT philosopher, in 1963 wrote a paper called:
> Computers can't play chess

Hubert Dreyfus is a major critic of AI ([wiki](https://en.wikipedia.org/wiki/Hubert_Dreyfus%27s_views_on_artificial_intelligence))

He then played against the Greenblatt Chess machine, and lost to the computer

Greenblatt chess machine is written by MIT AI lab research Richard Greenblatt ([wiki](https://en.wikipedia.org/wiki/Richard_Greenblatt_(programmer)))

Seymour Pavitt rebuttal:
> Dreyfus can't play chess either

1968 chess master David Levy bet John McCarthy that no computer would beat the world champion within 10 years.

5 years later John MrCarthy gave up, because no comptuer would in in a way that McCarthy wanted it to win, that is to say by **playing chess the way humans play chess**

1997 DeepBlue beat the world champion -> chess suddenly becomes unteresting

### Game and AI

There are elements of game-play that do model some of the things that go on in our head. And if they don't model things that go on in our head, they do model some kind of intelligence. (We need to understand _that_ intelligence too)

DeepBlue adds more than just tremendous speed

### How to Model Chess Intelligence

Various ways that we might design a computer program to play a game like chess.

How it might be possible for a computer to play chess. There are several proposed ideas:

1. Make description of the board the same way a human would. Analysis, strategy, and tactic, to generate moves.

No one knows how to do it, until now, no game playing program incorporate this idea (Dreyfus was right).

2. if-then rules, no evaluation of the board, does not try angthing. Look at board and select move. _Not a good approach_

Situations + possible moves = one possibile move selected based on if-then rules.

3. look ahead and evaluate

Look ahead from current situation and see all the possible consequences of moves and evaluate which of these board situations is best for me?

**Mechanisms of evaluating the situation deciding which of those is best**

A popular mechanism to evaluate move/board: Many features of the chessboard --> Function of the features --> Static value of the board seen from your perspective.

It is **static** because you are not exploring any consequences of what **might happen**, instead, **you are just looking at the board as it is**, checking the King's safety, checking the pawn structure... each of those produces a number fed into the function and out comes a value.

Linear scoring polynomial (more than what we need, we just need argmax of possible boards)

Linear scoring polynomial not the only way to evaluate a move

4. British Museum and simply evaluate the entire tree of possibilities

**Tree of moves, with depth d and branching factor b --> there will be b^d terminal leaves**

For chess, the branching factor varies, depending on the stage of the game, the average branching factor is 14.

Claude Shannon estimated there are 10^120 leaf nodes. It did not used to seem to be praticable, it used to seem impossible.

If you are going to do a British Museum treatment of the tree of moves, you have to do 10^120 static evaluations down there at the bottom if you are going to see which one of the moves is best at the top.

There are 10^80 atoms in the universe. There are 10^26 nanoseconds since the big bang.

10^80 atoms each try 1 possibility every nanosecond = 10^80 * 10^26 = 10^106 possibilities since the big bang.

**So if all the atoms in the universe were doing static evaluations at nanosecond speeds since the beginning of the Big Bang, they will still be 14 orders of magnitude short from evaluating the entire tree of moves for chess**

5. Put things together --> Look ahead not at one level but as far ahead as possible. Push the evaluation path out as far as we can and look at these static values of the leaf nodes down there --> use those static values to play the game

This idea was first multiply invented by Claude Shannon and Alan Turing. They spent a lot of lunch time conversations talking with each other about how a computer might play chess against the future when there would be computers.

Donald, Mickey and Alan Turing also invented this while working on Enigma

### Tree of Moves (Game Tree)

```
*
\ \
2 1
\ \ \ \
2 7 1 8
```

Simple tree with branching factor of 2 and depth of 2.

The numbers at the bottom = **values of the board from the perspective of the player at the top**

### Minimax

Let's say the player at the top would like to drive the play as much as possible toward the big numbers --> call that player the **maximizing player**

There is another player, his opponent, which we will call the **minimixing player**, and he is hoping that the play will go down to the board situation that is as small as possible

Player Max (eg white side) vs player Min (eg black side) are trying to maximuze or minimize the reward, and they take turns to play.

**Perceived value of that board situation at the top, from the perspective of player (min or max)**

Minimax algorithm = **You go down to the bottom of the tree, you compute static values, you back them up level by level, and then you decide where to go**

If you get down around 10 levels deep, and your branching factor is 14, it is not praticable to do all the static evaluations down there. But if you get down atbout 15 or 16 levels, you beat the world champion. So you want to get as far down in the tree as possible.

**When you get as far down into the tree as possible, what happens is the linear scoring polynomial with features that measure the board quality begins to clarify**.

In fact, when you get far, enough, the only thing that really counts is piece count, one of those features. So if you get far enough, piece count and a few other features will give you a good idea of what to do (action to take).

**Pull out every trick we can find to go as far down the tree as possible**

### alpha-beta

Layering on top of minimax that **cuts off large sections of the search tree**.

It is called alpha-beta because there are two parameters.

NOTE: alpha-beta is NOT an alternative to minimax, it is a layer on top of minimax to make it more efficient.
**Alpha-beta does not give you an answer different from minimax, it gives you exactly the same answer, NOT a different answer. It is a SPEED-UP, not an approximation**, it cuts off lots of the tree --> dead horse principle at work.

Not only do we not have to make these static evaluations, we do not even have to generate these moves.

**Minmax and alpha-beta arrive at, not the biggest number, not the smallest number, but a compromised number that is arrived at virtue of the fact that this is an _adversarial situation_**

### Progressive Deepening

Insurance or "anytime" algorithm (always have an answer ready to go as soon as an answer is demanded).

**Let's say the branching factor is 10, the number of static evaluations at level d is 10 times more than that at level (d-1) --> we can compute the static values and have a move in hand at level (d-1) for only 10% of the amount of the computation that is required for level d**

The amount of computation needed to do insurance policies at every level is not much different from the amount of computation needed to get an insurance policy at just one level, the penultimate level.

**Anytime algorithm: as soon as that clock runs out at two minutes, some answer is available. It will be the best one that the system can compute in the time available given the characteristics of the game tree as it has developed so far**.

DeepBlue in 1997 did 200 million static evaluation per second, went down using alpha-beta about 15 levels.

DeepBlue = minimax + alpha-beta + progressive deepening + a lot of parallel computing + dynamic/uneven tree development

DeepBlue beat Kasparov

### Closing Remarks

But is this a model of human intelligence? Or different kind of intelligence?

Is this a model of anything that goes on in our own heads?

Mixed.

Yes, we are often in situations where we are playing a game, and we are competeing with another player (adversatial), and we have to think about what the adversarial will do in response to what we do, down several levels.

But going down 14 levels is too much computational horsepower for human --> bulldozer processing gravel --> **substituting raw power for sophistication**

Chess players are good at memorizing chess boards as long as it is a legitimate chessboard, if the pieces are placed randomly, chess masters are no good at it at all. (a lot like Approach No.1)

DeepBlue is not our intelligence, it is bulldozer intelligence. (it is important to understand that kind of intelligence too)
