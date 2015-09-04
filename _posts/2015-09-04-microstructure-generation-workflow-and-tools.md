---
layout:     post
title:      Microstructure Generation Workflow and Tools
date:       2015-09-04
author:     Fred Hohman
---

Even though our project is still in the early stages, the workflow and planning is beginning to take shape. This post will give a brief overview of the tools we will be using to carry out our grain growth simulations. 

## Generating Statistics

Our first step is to create an initial microstructure that we wish to simulate. We want to simulate on real materials, so we need a way to instruct the computer to match an digital microstructure with something that exists in nature. We do this by matching the statistical size distribution of the grains of a microstructure in a program called StatsGenerator. Here we can tweak parameters of the distribution itself, as well as specifying molecular grain geometry, Euler angles, and the associated ODF and pole figures. 

During our first run-through of our workflow, we crated an initial microstructure of randomly distributed grain size. This does not represent any particular material found in nature, but it is sufficient as an example to test our other tools. Our main work will be focused on particular materials that will be explicitly listed when appropriate. 

## Creating Initial Microstructure

Once our statistical data has been matched and created, we next use an open source software called [DREAM.3D][dream3d]. Developed by multiple academic institutions, DREAM.3D is an

> open, extensible software environment to allow integrated processing, characterization and manipulation of microstructure digitally.

DREAM.3D allows the construction of modular "pipelines" that take in statistical data and output material microstructure. Many options exist within the software that allow a user to tailor a research problem and create an appropriate microstructure. We are using an existing pipeline that is detailed in a sideshow [here][linkedin].

## SPPARKS and PACE

Once we have an initial microstructure created, we wish to simulate its grain growth (that is our project after all!). We will be using another open source code developed by Sandia National Labs called [SPPARKS][spparks]. From the website description,

> SPPARKS is a parallel Monte Carlo code for on-lattice and off-lattice models that includes algorithms for kinetic Monte Carlo (KMC), rejection kinetic Monte Carlo (rKMC), and Metropolis Monte Carlo (MMC).

We have already successfully compiled SPPARKS on [PACE][pace], a Georgia Tech computer cluster where we will run our simulations. SPPARKS can be run on a single processor, but given our project's scope and the amount of simulations we wish to do, running in parallel will speed up the data generation process.

SPPARKS requires command line interactions and some accessory scripts in order to run according to our specifications; however, this post will not describe the pedantic detail of code variables. Specific changes to the code and variables used will be specified in a future post once our simulations are completed.

## Visualizations

Once PACE as finished our simulations, we will then download the data locally to manipulate and process. We have a Python script that inputs our data and converts it into `.vtk` files that are able to be visualized by a software called [Paraview][paraview]. From the website, 

> ParaView is an open-source, multi-platform data analysis and visualization application. ParaView users can quickly build visualizations to analyze their data using qualitative and quantitative techniques. The data exploration can be done interactively in 3D or programmatically using ParaView’s batch processing capabilities.

Paraview allows a user to flexibly interact with 3D data. For example, since we now have 3D microstructure data evolving in time, we are able to play a movie and watch grain growth evolution occur. We can also view a single 2D slice of data in the XY, YZ, or XZ plane and watch it evolve. Paraview also provides many exporting formats to allow external data analysis.

## Recap

Just to recap everything stated above, here is an abridged version of the workflow and tools we will be using to carry out our research:

### Data Generation

* Generate and match statistics of a particular material
* Create initial microstructure using DREAM.3D
	* Obtain a `.spparks` file with our microstructure data
	* Clean up data using `.awk` script
* Upload data and run SPPARKS grain growth simulation on PACE cluster
	* This uses our initial microstructure as the starting point
	* Generates multiple microstructures evolving in time
	* Transfer all data to local machines
* Use Python script to convert simulation data files into `.vtk` files
* Visualize simulation data in Paraview 
	* View grain growth evolution in time as movie
	* Can inspect any 2D slice of 3D microstructure individually

### Analysis

Our first external data analysis mini-project will be plotting the 3D grain boundaries in Paraview which will require some Matlab programming in order to parse each slice of 2D data from each time step in the simulation. We plan to perform many n-point statistical computations as well as dimensionality reductions once our data is sorted and organized. These processes will be described further in a future posts.


[paraview]: http://www.paraview.org "Paraview."
[spparks]: http://spparks.sandia.gov "SPPARKS."
[pace]: http://pace.gatech.edu "PACE."
[dream3d]: http://dream3d.bluequartz.net "DREAM.3D."
[linkedin]: http://www.slideshare.net/mwpriddy/dream3d-tutorial "LinkedIn."