---
layout:     slide
title:     	Grain Growth Progress Report Presentation I
date:      	2015-09-15
author:     Fred Hohman, David Montes de Oca Zapiain

theme:		night # default/beige/blood/moon/night/serif/simple/sky/solarized
trans:		default # default/cube/page/concave/zoom/linear/fade/none

horizontal:	</section></section><section markdown="1" data-background="http://ahmetcecen.github.io/project-pages/img/slidebackground.png"><section markdown="1">
vertical:		</section><section markdown="1">
---
<section markdown="1" data-background="http://ahmetcecen.github.io/project-pages/img/slidebackground.png"><section markdown="1">
## {{ page.title }}

<hr>

#### {{ page.author }}

#### {{ page.date | | date: "%I %M %p ,%a, %b %d %Y"}}

{{ page.horizontal }}

<!-- Start Writing Below in Markdown -->

## Topics
 
* Theory
* Data and Computation

{{ page.horizontal }}

## Theory Outline

* Background Theory on Grain Growth
* Objective of our Project
* Intended Approach
* Overview of Tools we are using

{{ page.horizontal }}

## Theory on Grain Growth and Objective

* The driving force for grain growth is the grain boundary interfacial free energy. 
* Precipitates “pin”, deter, this grain growth since they reduce the surface area when a boundary crosses a precipitate. 

![Picture 1]({{ site.url }}/MIC-grain-growth/img/blogpostimages/presentation1/1.png)

{{ page.horizontal }}

## Objective 

* We are using Kinetic Monte Carlo equations through the SPPARKS Program to analyze the effect of different precipitate distributions on the Grain Growth of a Microstructure. 
* Then we want to predict with sufficient accuracy and in a computationally non-expensive fashion if a specified Distribution of Particles will cause abnormal or normal grain growth. This will be achieved by using a Data Science Approach.

{{ page.horizontal }}

![Picture 2]({{ site.url }}/MIC-grain-growth/img/blogpostimages/presentation1/2.png)

{{ page.horizontal }}

## Inputs and Outputs

* We have an initial random Microstructure to which we are going to place various different distributions of precipitates. 
	1. Random
	2. Uniform
	3. Clustered
* We will also vary the shape, size and volume fraction of Precipitates. 
* Perform enough Simulations to have a enough statistical data. 
* On each simulation we can output various snapshots of the Micro Structure so we can calculate the grain size distribution and as well observe its evolution history. 

{{ page.horizontal }}

### Data and Computation Outline

* Data Tools and Generation Workflow
* How Much Data?
* Current Status
* What's Next

{{ page.horizontal }}

## Data Tools

* SPPARKS: open source code developed by Sandia National Labs
* PACE: computing cluster 
* Pinning Script
	* Allows pinning of different distributions 
* Paraview: 3D visualization software

{{ page.horizontal }}

## Data Generation Workflow

* Create initial/master random microstructure using SPPARKS
* Apply pinning algorithm with desired variables selected
* Run SPPARKS on PACE on our pinned microstructure to simulate grain growth
* View 3D models in Paraview

Goal: one button that does it all.

{{ page.horizontal }}

## How Much Data? 

We are varying 3 variables in our simulations

1. Pin size/shape:
	
	* 0 neighbor cube (single voxel, 1x1x1)
	* 1 neighbor cube (3x3x3)
	* 2x2x2 cube
	* 2x1x1 prism
	* 3x1x1 prism
	* 3D plus sign

![Picture 3]({{ site.url }}/MIC-grain-growth/img/blogpostimages/presentation1/3.png)

2. Pin percentage: {0.5, 1.0, 1.5, 2.0, 2.5, 3.0}
3. Pin distribution: random, uniform, cluster

{{ page.horizontal }}

## How Much Data? 

* Pin size/shape: 6 options
* Pin percentage: 6 options
* Pin distribution: 8 options

Total number of simulations to be run: 6 x 6 x 8 = 288

Note: this could be reduced depending on computational time!

{{ page.horizontal }}

## Current Status

* We have compiled SPPARKS on PACE and became familiar with running simulations
* Developed pinning algorithm for random and uniform distributions, missing clustering
* Able to successfully simulate grain growth with pins and visualize growth in 3D as animation/movie

{{ page.horizontal }}

## What's Next

* Finalize number of variables
* Patch together tools in master program that inputs our variables and outputs multinational data 
* PymKS—*coming soon!*

<!-- End Here -->


{{ page.horizontal }}

#[Print]({{ site.url }}{{ site.baseurl }}{{ page.url }}/?print-pdf#)

#[Back]({{ site.url }}{{ site.baseurl }})

</section></section>

