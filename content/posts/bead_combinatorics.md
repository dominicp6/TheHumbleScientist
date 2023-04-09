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
So you've studied probability. You know multinomials from binomials, permutations from combinations, and you compute odds of poker plays for fun and profit. Well, now it's time to put your knowledge to the test with this little conundrum. 

---

### Problem

*For seven days and nights you wander the foothills of the Himalayas. Delirious and low on supplies, you seek refuge in an ancient monastery perched precariously on the hillside. You approach the high wooden doors and knock. After a moment of silence the door creeks open. The face of an aged Tibetan sage greets you. He looks at you with an air of wisdom and curiosity, silently beckoning you to enter. The sage leads you to a small courtyard, sitting you down on a cushioned mat. You explain your desperate situation, and the sage listens intently. But he informs you that only the most worthy may receive shelter, and so he states your task:*

> *Before you I present 50 prayer beads, 30 white and 20 black. These beads are to be arranged in a circle so that there are four clusters of black beads. If you find how many ways there are of doing this, then I will grant you food and shelter!*

Just to be clear, by "a cluster of black beads", the sage means a continuous string of adjacent black beads on the circle without any intervening white beads.

So that's the conundrum! Give it a go and see how far you can get. Once you're ready, scroll down for the solution.

---

### Solution

Let's look at the general case: let $W$ be the number of white beads, $B$ the number of black beads, and $k$ the number of black clusters. For convenience, let's enumerate the positions the beads can take in the circle in clockwise order as position $1, 2, 3, $, and so on.

To get started, we make an insightful observation: if we have $k$ clusters of black beads, then we also have $k$ clusters of white beads, since a white bead cluster must lie between every two black bead clusters, and we are putting these clusters on a circle. Make sure that you understand this before continuing!

Now we are ready to tackle the problem. Our general strategy will be to partition the set of possible configurations of black beads based on the bead in position $1$ being either black or white.

**Case 1: The bead in position $1$ is black**

First, we partition our $B$ black beads into $k$ clusters on the ring, such that there is at least one bead in each cluster. Note that this is a variant of the "stars and bars" problem in combinatorics, and the total number of ways of doing this is (try to verify this yourself):

$$
\binom{B}{k}.
$$

Next, we partition our remaining $W$ white beads into the $k$ 'gaps' between the black bead clusters. This is also (a slightly different) variant of the "stars and bars" problem, and the number of ways of doing this is:

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

In our problem involving the wise Tibetan sage, we have $W=30, B=20, k=4$. For which the total number of arrangements is


$$
\binom{20}{4}\binom{29}{3} + \binom{30}{4}\binom{19}{3} = 44, 259, 075.
$$

So, quite a lot!

Now, if you have gotten this far through the problem, you might be asking what exactly counts as a different arrangement. Here you may have noticed that we've taken the strictest interpretation by labelling distinct positions on the rings. But you might be in the camp that believes if we simply rotate the positions of all beads simultaneously, then this should count as the same arrangement. However, if we choose to do it this way, then we have to be a bit careful because different configurations have different degrees of rotational symmetry. In other words, we can't simply divide by $W + B$ and call it a day. I'll leave it to you to work out the details ;) 

Regardless of how we count, we certainly would have perished before completing the task if we had tried to enumerate every possibility! Our combinatorics skills have let us live another day.