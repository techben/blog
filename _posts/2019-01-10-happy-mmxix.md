---
layout: post
title: "Happy birthday, Donald Knuth! and Peaceful Encampments"
date: 2019-01-10 00:01:00 +0000
tags:
  adventure
  litclub
  math
  puzzles
  web
---

Today (January 10th) is Donald Knuth's 81st birthday. Happy birthday, Dr. Knuth!

Readers of this blog will already know [Donald Knuth](https://www-cs-faculty.stanford.edu/~knuth/)
as the primary author of TeX, Metafont, and WEB;
the author of the ongoing "Art of Computer Programming" (TAOCP) series; and one of the two Dons
behind the 1998 collaboration that produced a translation of _Adventure_ into a CWEB "literate program."
The beautiful (and fairly informative, and fairly entertaining) result is
[here](http://literateprogramming.com/adventure.pdf), and is also included as pages 235–395 of
Knuth's [_Selected Papers on Fun & Games_](https://amzn.to/2RhoZTb) (2011).

I met Dr. Knuth a couple of times in real life. The first time was at the Martin Gardner
Celebration of Mind at UC Berkeley in 2014. (Ambigram expert Scott Kim, familiar to readers of
Douglas Hofstadter's [_Gödel, Escher, Bach_](https://amzn.to/2SJTwW8), does the Celebration of Mind
logo every year. I once collected some of them
[over here](http://www.club.cc.cmu.edu/~ajo/disseminate/mg-ambigrams.html).)

Knuth's pet puzzle of the day, that day, was a sort of continuous version of a
[nonattacking queens](https://math.stackexchange.com/questions/687298/maximum-nonattacking-black-and-white-queens-on-infinite-chessboard)
problem which he called "Peaceful Encampments." Paraphrased by me:

> Consider a plain represented by the unit square. On this plain we want to "peacefully encamp"
> two armies of point-sized soldiers — one army red and one army green. Each soldier "attacks"
> chess-queen-wise: horizontally, vertically, and diagonally in all directions. The puzzle is
> to maximize the size of the equal armies (equivalently, maximize the size of the smallest army),
> given the constraint that no pair of opposing soldiers can be placed attacking each other.

Back in 2014, I went and wrote a JavaScript visualizer for the problem, and — purely by noodling
around, no rigor at all — came up with a few solutions such as
[this one](http://club.cc.cmu.edu/~ajo/disseminate/encamp.html?q=%7B%22v%22%3A%5B%7B%22minInvariant%22%3A0%2C%22maxInvariant%22%3A0.167%7D%2C%7B%22minInvariant%22%3A0.833%2C%22maxInvariant%22%3A1%7D%5D%2C%22h%22%3A%5B%7B%22minInvariant%22%3A0%2C%22maxInvariant%22%3A0.167%7D%2C%7B%22minInvariant%22%3A0.833%2C%22maxInvariant%22%3A1%7D%5D%2C%22s%22%3A%5B%7B%22minInvariant%22%3A0.000%2C%22maxInvariant%22%3A0.333%7D%2C%7B%22minInvariant%22%3A0.833%2C%22maxInvariant%22%3A1.166%7D%2C%7B%22minInvariant%22%3A1.666%2C%22maxInvariant%22%3A2%7D%5D%2C%22b%22%3A%5B%7B%22minInvariant%22%3A-1%2C%22maxInvariant%22%3A-0.666%7D%2C%7B%22minInvariant%22%3A-0.166%2C%22maxInvariant%22%3A0.166%7D%2C%7B%22minInvariant%22%3A0.666%2C%22maxInvariant%22%3A1%7D%5D%7D)
and [this one](http://club.cc.cmu.edu/~ajo/disseminate/encamp.html?q=%7B%22v%22%3A%5B%7B%22minInvariant%22%3A0.0%2C%22maxInvariant%22%3A0.5%7D%5D%2C%22h%22%3A%5B%7B%22minInvariant%22%3A0%2C%22maxInvariant%22%3A0.5%7D%5D%2C%22s%22%3A%5B%7B%22minInvariant%22%3A0.0%2C%22maxInvariant%22%3A1.0%7D%5D%2C%22b%22%3A%5B%7B%22minInvariant%22%3A0.0%2C%22maxInvariant%22%3A0.5%7D%5D%7D)
and [this one, which I still conjecture to be the best possible](http://club.cc.cmu.edu/~ajo/disseminate/encamp.html?q=%7B%22v%22%3A%5B%7B%22minInvariant%22%3A0%2C%22maxInvariant%22%3A0.422649730810374%7D%5D%2C%22h%22%3A%5B%7B%22minInvariant%22%3A0%2C%22maxInvariant%22%3A0.42265%7D%5D%2C%22s%22%3A%5B%7B%22minInvariant%22%3A0%2C%22maxInvariant%22%3A1%7D%5D%2C%22b%22%3A%5B%7B%22minInvariant%22%3A-0.2113248654051871177%2C%22maxInvariant%22%3A0.2113248654051871177%7D%5D%7D).

|:-----------------------------------------------------:|:------------------------------------------------------:|:---------------------------------------------------:|
| ![Encampments](/blog/images/2019-01-10-one-ninth.png) | ![Encampments](/blog/images/2019-01-10-one-eighth.png) | ![Encampments](/blog/images/2019-01-10-optimal.png) |

I wrote at the time:

> The square in the upper left-hand corner has a side of
> $$a = \left(1 - {1\over\sqrt{3}} \right)$$
> and the big right isosceles triangle wedged into the lower left corner has a side of
> $$b = 1 - {a\over 2}.$$
> This maximizes the size of the (equal) armies, which is
> $$b^2 - a^2 = \left(1 - {\sqrt{3}\over 2}\right) \approx 0.13397$$.

My description of the puzzle continues:

> Once you've solved that, the next puzzle is to peacefully encamp *three* armies, four armies, etc...
> all the way to infinity. Knuth had a raggedy-looking conjectured solution for three armies,
> and nothing for four or higher.

I'd be interested to know if any further progress has been made on this problem since 2014.