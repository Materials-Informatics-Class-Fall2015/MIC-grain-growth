---
layout:     post
title:      November Plan of Attack
date:       2015-10-30
author:     Fred Hohman
---

## I/O
As presented during our third progress report presentation last Wednesday, we have finalized our to-be-created model's inputs and outputs. We are inputting the autocorrelation of (2,2): the autocorrelation between our pins/precipitates. We will then be correlating this to a chord length distribution so that given a microstructure as an input we can make some predictions about it's final grain size distribution after being subjected to a growth process (such as temperature).

## A PyMKS Bug?
So we need to form a reduced basis for our inputs and a reduced basis for our outputs. On the input side, we will be inputting microstructures who have already been segmented and prepared for 2 point statistics and PCA. Recall out since our data set of 300x300x300 microstructures is really big. After talking with some of the MINED members, it might be one of the biggest data sets the group has had to deal with. 

Because of this we have ran into memory issues when computing statistics and PCA. It appears PyMKS has some temporary/intermediately variables in the 2 point statistics calculation that is eating extra memory, which is why `n_samples=18` of our 300x300x300 microstructures weren’t able to run quickly (even on PACE). Ahmet hypothesized that is it actually the PCA code from scikit learn I’m using, but right now it’s a bit unclear which is taking longer.

In short, it looks like PyMKS is making a copy (or sometimes *multiple copies*) of our data during the computations, and since our data matrix is super big, that memory is being used *quickly*. 

What's the positive angle? Looks like we might have found a place to optimize PyMKS so that we can reduce the memory requirement, which would let other people run larger data sets on their own personal computers.

## What Else?
We have a meeting with a scientist at Sandia national labs next week to finalize some data set parameters and to ask him what he thinks is most interesting about what we are doing so that we can focus and provide some new information for domain experts. This should be very insightful!

David M. has begun to look at calculating chord length distributions in a more sophisticated way since our current results are good, but PCA wasn't showing any immediate trends.

## Crunch Time
As we enter the last few weeks of the semester we are starting to get into crunch time. Let us know if you see a similar long computation times in PyMKS or if you have some questions about what we are trying to do.