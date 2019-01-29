---
layout: post
title: "Discrete Peaceful Encampments"
date: 2019-01-24 00:01:00 +0000
tags:
  math
  puzzles
---

Over the past couple of days I've posted variations on "Peaceful Encampments" as puzzles on
StackExchange, to try to drum up some interest in them. I've learned that puzzlers greatly
prefer _discrete_ puzzles (queens on a chessboard) over _continuous_ puzzles (such as the
original "Peaceful Encampments" as seen on this blog): my discrete puzzles have gotten quick
and accurate answers, whereas
[my original continuous version](https://puzzling.stackexchange.com/questions/78676/peaceful-encampments)
is languishing.

[The other day:](https://puzzling.stackexchange.com/questions/78727/discrete-peaceful-encampments-9-queens-on-a-chessboard)

> You have 9 white queens and 9 black queens. Place all these pieces onto a normal 8x8
> chessboard in such a way that no white queen threatens a black queen (nor vice versa).

[Today, player three enters the game!:](https://puzzling.stackexchange.com/questions/78801/discrete-peaceful-encampments-player-3-has-entered-the-game)

> You have 4 white queens, 4 black queens, *and 4 red queens.*
> Place all these pieces onto a normal 8x8 chessboard in such a way that no white queen
> threatens a black queen, no black queen threatens a red queen, and no red queen threatens
> a white queen (nor vice versa).

----

I've wrote a C++ program to brute-force the maximum number of queens that can be placed
peacefully on an NxN chessboard in the 2-army and 3-army cases. Much of the search space
can be short-circuited, similarly to my [_meta-sudoku_ brute-forcer](/blog/2018/10/26/sudoku-stories/)
as seen on this blog (October 2018).

For two armies, the sequence of solutions is [OEIS A250000](https://oeis.org/A250000):

|  n    | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9  | 10 | 11 | 12 | 13 | 14 | 15 |
|:-----:|---|---|---|---|---|---|---|---|----|----|----|----|----|----|----|
|  f(n) | 0 | 0 | 1 | 2 | 4 | 5 | 7 | 9 | 12 | 14 | 17 | 21 | 24 | 28 | 32 |

(That is, on a 4x4 chessboard you can fit peacefully 2 white and 2 black queens;
on a 5x5 chessboard you can fit peacefully 4 white and 4 black queens; and so on.)

For three armies, the sequence is not found in the OEIS.

|  n    | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9  | 10 | 11 | 12  | 13  | 14  | 15  |
|:-----:|---|---|---|---|---|---|---|---|----|----|----|-----|-----|-----|-----|
|  f(n) | 0 | 0 | 0 | 1 | 1 | 2 | 3 | 4 | 5* | 7* | 8* | 10* | 12* | 12* | 12* |

(That is, on a 7x7 chessboard you can fit peacefully 3 white, 3 black, and 3 red queens;
on an 8x8 chessboard you can fit peacefully 4 white, 4 black, and 4 red queens; and so on.)

Numbers with asterisks are my best solutions but not necessarily the best possible.

Here are my solutions, for the record:

4x4: 2 white, 1 black, 1 red (verified best)

    .W..
    ...W
    B...
    ..R.

5x5: 4 white, 2 black, 1 red (verified best)

    WW...
    ...BB
    .W...
    W....
    ..R..

6x6: 3 white, 3 black, 2 red (verified best)

    W.....
    ..B..B
    .....B
    ......
    WW....
    ...RR.

7x7: 4 white, 4 black, 3 red (verified best)

    ..WW...
    ..W....
    ......R
    ....W..
    BB.....
    BB.....
    .....RR

8x8: 6 white, 5 black, 4 red (verified best)

    ..WW...W
    ..W....W
    .......W
    ........
    RR......
    RR......
    ....BBB.
    .....BB.

9x9: 7 white, 6 black, 5 red

    ..RRR....
    ..RR.....
    .......BB
    ........B
    .W.......
    WW.......
    WW.......
    WW.......
    ......BBB

10x10: 8 white, 7 black, 7 red

    ...RR.....
    ...RRR....
    ...RR.....
    ........BB
    .........B
    ..........
    .WW.......
    WWW.......
    WWW.......
    ......BBBB

11x11: 9 white, 8 black, 8 red

    ...WWWW....
    ...WWW.....
    ..........R
    ..........R
    ......WW...
    ..B........
    .BB........
    BBB........
    BB.........
    ........RRR
    ........RRR

12x12: 11 white, 10 black, 10 red

    ...RR.......
    ...RRR......
    ...RRR......
    ...RR.......
    .........BBB
    ..........BB
    ...........B
    .WW.........
    WWW.........
    WWW.........
    WWW.........
    .......BBBB.

13x13: 13 white, 12 black, 12 red

    ...RR........
    ...RRR.......
    ...RRRR......
    ...RRR.......
    .........WWWW
    ..........WWW
    ...........WW
    ..B..........
    .BB..........
    BBB..........
    BBB..........
    BBB..........
    ........WWWW.

Notice the similarity between my conjectured 9x9, 12x12, and 13x13 solutions and my
conjectured solution to the continuous "Peaceful Encampments" puzzle for three armies:

|:---------------------------------------------------------------------------------------:|
| [![Three encampments of size 0.0718 each](/blog/images/2019-01-21-three-armies.png)][1] |

[1]: http://club.cc.cmu.edu/~ajo/disseminate/encamp4.html?q=%7B%22v%22%3A%5B%7B%22minInvariant%22%3A0%2C%22maxInvariant%22%3A0.246%2C%22color%22%3A%22red%22%7D%2C%7B%22minInvariant%22%3A0.246%2C%22maxInvariant%22%3A0.566%2C%22color%22%3A%22green%22%7D%5D%2C%22h%22%3A%5B%7B%22minInvariant%22%3A0%2C%22maxInvariant%22%3A0.291%2C%22color%22%3A%22green%22%7D%2C%7B%22minInvariant%22%3A0.53%2C%22maxInvariant%22%3A0.889%2C%22color%22%3A%22red%22%7D%5D%2C%22s%22%3A%5B%7B%22minInvariant%22%3A0%2C%22maxInvariant%22%3A0.699%2C%22color%22%3A%22green%22%7D%2C%7B%22minInvariant%22%3A0.699%2C%22maxInvariant%22%3A1.107%2C%22color%22%3A%22red%22%7D%5D%2C%22b%22%3A%5B%7B%22minInvariant%22%3A-0.441%2C%22maxInvariant%22%3A0%2C%22color%22%3A%22green%22%7D%2C%7B%22minInvariant%22%3A0.345%2C%22maxInvariant%22%3A1%2C%22color%22%3A%22red%22%7D%5D%7D