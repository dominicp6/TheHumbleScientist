---
title: "The Prayer Bead Conundrum"
date: 2023-04-09T09:47:33+01:00
draft: false
math: true
markup: 'mmark'
cover:
    image: beads.jpg
tags: ["combinatorics"]
---
Are you ready to put your probability skills to the test? In this little conundrum, you'll be challenged to think creatively and apply your knowledge to solve a combinatorics problem involving bead arrangements in a circle. It's tricky, but if you already know your multinomials from your binomials or your permutations from your combinations, then you have all the mathematical background necessary to give it a try! 

---

### The Prayer Bead Problem

*You are lost and hungry in the foothills of the Himalayas and seek refuge in an ancient monastery. The wise Tibetan monk who greets you offers you food and shelter, but only if you can solve a challenging problem:*

> *You have 50 prayer beads in two colors: 30 white and 20 black. You want to arrange them all in a circle so that there are exactly four groups of black beads (a group of black beads is a sequence of one or more black beads that are not separated by white beads). How many ways are there of doing this?*

Give it a go! If you need hints or the solution, then scroll down when you're ready.

---

### Hints

**Hint 1**: This problem is not easy, so you might want to work through special cases with smaller numbers of beads first. Can you spot how the number of clusters of white beads is related to the number of clusters of black beads? Another tricky aspect of this problem is the circular arrangement. Solving the problem when they are arranged in a straight line is easier, and might provide useful insights. 

**Hint 2**: Solving this problem will require experience in combinatoric formulas. If you think you need a refresher, then a good place to start would be to get familiar with the [Stars and Bars problem](https://en.wikipedia.org/wiki/Stars_and_bars_(combinatorics)). You should try to think about how that formula might be relevant to this problem.

**Hint 3**: When counting arrangements in these kinds of problems it can sometimes be useful to partition based on several special cases, to be examined separately. Finally, remember to look for ways that a particular arrangement can be decomposed into several "sub-arrangements". If you know how many of each sub-arrangement there are, then you can just multiply the combinatoric factors to arrive at the quantity of interest.

---

### Solution

Let's look at the general case: let $W$ be the number of white beads, $B$ the number of black beads, and $k$ the number of black clusters. We'll enumerate positions the beads take in the circle in clockwise order as $1, 2, 3$, and so on.

To get started, we make an insightful observation: if we have $k$ clusters of black beads, then we also have $k$ clusters of white beads, since a white bead cluster must lie between every two black bead clusters on the circle. The easiest way to convince yourself of this is by drawing some specific examples.

We are now ready to tackle the problem and count the possible arrangements. As we will see, it will be necessary to partition the permitted arrangements based on whether the bead in position $1$ is either black (Case 1) or white (Case 2).

**Case 1: The bead in position $1$ is black**

First, we imagine mentally partitioning our $B$ black beads into $k$ clusters on the ring, such that there is at least one bead in each cluster. We will ignore white beads and the exact positions of the clusters for now; simply note that the bead in position $1$ must be in one of the $k$ black clusters.

Counting the number of ways of ordering just these black clusters in a ring (ignoring white clusters) is a variant of the [Stars and Bars problem](https://en.wikipedia.org/wiki/Stars_and_bars_(combinatorics)) in combinatorics. You will need to adapt the standard formula a little bit to make it work on a circle, and you should then find that the total number of ways of ordering black clusters is:

$$
\binom{B}{k}.
$$

Next, we partition our remaining $W$ white beads into the $k$ 'gaps' between the black bead clusters. This is also (a slightly different) variant of the Stars and Bars problem, and the number of ways of doing this is (verify!):

$$
\binom{W-1}{k-1}.
$$

The total number of possible arrangements, when the bead in position $1$ is black, is then

$$
\binom{B}{k}\binom{W-1}{k-1}.
$$

**Case 2: The bead in position $1$ is white**

This is the same logic as above, but the role of the white and black beads is reversed, and so the number of arrangements, if the bead in position $1$ is white, will be

$$
\binom{W}{k}\binom{B-1}{k-1}.
$$

**Putting it all together**

Considering both cases, the total number of permissible arrangements is therefore

$$
\binom{B}{k}\binom{W-1}{k-1}+\binom{W}{k}\binom{B-1}{k-1}.
$$

In our problem involving the wise Tibetan monk, we have $W=30, B=20, k=4$. For which the total number of arrangements is


$$
\binom{20}{4}\binom{29}{3} + \binom{30}{4}\binom{19}{3} = 44, 259, 075.
$$

---

### But wait, there's more!

If you have got this far, you might ask what exactly counts as a different arrangement. In writing the solution above, we've taken the strictest interpretation and counted all arrangements as distinct so long as we don't have the same colour beads in every position. But you might instead claim, quite rightly, that if we simply rotate a particular configuration, then this should count as the same arrangement! This certainly reduces the number of arrangements, but you still have to be careful with the counting because different configurations can have different degrees of rotational symmetry. In other words, we can't simply divide our answer by the number of beads and call it a day. This is a classic example of how a seemingly simple problem can open up a Pandora's box of technicalities... I'll leave it to you to work out the details!
